---
title: Отладка кода Python на удаленных компьютерах Linux
description: Используйте Visual Studio, чтобы отладить код Python, выполняющийся на удаленных компьютерах Linux, в том числе здесь приведены необходимые этапы настройки, обеспечения безопасности и устранения неполадок.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: dcc5d9746a556af54ea206528fcb9a402e25d700
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916596"
---
Visual Studio позволяет локально и удаленно запускать приложения Python на компьютере Windows и выполнять их отладку (см. статью [Удаленная отладка](../../../debugger/remote-debugging.md)). С помощью [библиотеки debugpy](https://pypi.org/project/debugpy/) можно также выполнять удаленную отладку, используя другую операционную систему, другое устройство или реализацию Python, отличную от CPython.

При работе c debugpy для отлаживаемого кода Python создается сервер отладки, к которому может подключаться Visual Studio. Для такого размещения нужно внести лишь небольшое изменение в код для импорта и запуска сервера и в некоторых случаях скорректировать на удаленном компьютере настройки сети и брандмауэра, чтобы разрешить подключения TCP.

> [!NOTE]
> Для Visual Studio 2019 версии 16.4 и более ранних версий использовалась [библиотека ptvsd](https://pypi.python.org/pypi/ptvsd). В Visual Studio 2019 версии 16.5 библиотека ptvsd 4 заменена библиотекой debugpy.

## <a name="set-up-a-linux-computer"></a>Настройка компьютера Linux

Для выполнения данного пошагового руководства необходимо следующее:

- удаленный компьютер с Python на базе операционной системы, такой как Mac OSX или Linux;
- открытый порт 5678 (входящий трафик) в брандмауэре этого компьютера, который используется по умолчанию для удаленной отладки.

> [!NOTE]
> Это пошаговое руководство основано на Visual Studio 2019 версии 16.6.

Можно без труда создать [виртуальную машину Linux в Azure](/azure/virtual-machines/linux/creation-choices) и [получить к ней доступ с помощью удаленного рабочего стола](/azure/virtual-machines/linux/use-remote-desktop) из Windows. Для виртуальной машины удобно использовать Ubuntu, так как Python устанавливается по умолчанию. В противном случае см. список в разделе [Выбор и установка интерпретатора Python](../../installing-python-interpreters.md) с перечнем дополнительных расположений скачиваемых файлов Python.

Дополнительные сведения о создании правила брандмауэра для виртуальной машины Azure см. в статье [Открытие портов для виртуальной машины в Azure с помощью портала Azure](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Подготовка скрипта к отладке

1. Создайте на удаленном компьютере файл Python *guessing-game.py* со следующим кодом:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. Установите в своей среде пакет `debugpy` с помощью команды `pip3 install debugpy`.
   >[!NOTE]
   >Рекомендуется записать устанавливаемую версию debugpy на случай необходимости устранения неполадок. Доступные версии также можно найти в [списке debugpy](https://pypi.org/project/debugpy/).

1. Включите удаленную отладку, добавив в файл *guessing-game.py* приведенный ниже код. Он должен размещаться как можно раньше, до любого другого кода. (Это не является строгим требованием, но для всех фоновых потоков, созданных до вызова функции `listen`, отладка невозможна).

   ```python
   import debugpy
   debugpy.listen(5678)
   ```

1. Сохраните файл и запустите `python3 guessing-game.py`. Вызов `listen` выполняется в фоновом режиме и ожидает входящих подключений, если вы каким-либо другим способом не взаимодействуете с программой. При необходимости после `listen` можно вызвать функцию `wait_for_client`, чтобы заблокировать выполнение программы до подключения отладчика.

> [!Tip]
> Помимо `listen` и `wait_for_client`, debugpy предоставляет вспомогательную функцию `breakpoint`, которая обрабатывается как программная точка останова, если присоединен отладчик. Существует также функция `is_client_connected`, которая возвращает значение `True`, если присоединен отладчик (но вы не обязаны проверять этот результат, прежде чем вызывать любые другие функции `debugpy`).

## <a name="attach-remotely-from-python-tools"></a>Удаленное подключение с помощью инструментов Python

В следующем примере мы устанавливаем простую точку останова, чтобы прервать выполнение удаленного процесса.

1. Скопируйте удаленный файл на локальный компьютер и откройте его в Visual Studio. Вы можете разместить этот файл в любом каталоге, но его имя должно совпадать с именем скрипта на удаленном компьютере.

1. Чтобы технология IntelliSense для debugpy работала на локальном компьютере, установите пакет debugpy в среде Python (необязательно).

1. Выберите **Отладка** > **Присоединение к процессу**.

1. В открывшемся диалоговом окне **Присоединение к процессу** задайте для параметра **Тип подключения** значение **Python remote (debugpy)** (Удаленная отладка Python (debugpy)).

1. В поле **Цель подключения** введите `tcp://<ip_address>:5678`, где `<ip_address>` — IP-адрес удаленного компьютера (может быть явным адресом или именем, например myvm.cloudapp.net), а `:5678` — номер порта удаленной отладки.

1. Нажмите клавишу **ВВОД**, чтобы заполнить список доступных процессов debugpy на этом компьютере:

    ![Ввод цели подключения и заполнение списка процессов](../../media/remote-debugging-attach.png)

    Если после заполнения этого списка вы запускаете другую программу на удаленном компьютере, нажмите кнопку **Обновить**.

1. Выберите процесс для отладки, а затем нажмите **Присоединить**, либо дважды щелкните процесс.

1. Visual Studio переключается в режим отладки, а скрипт продолжает выполняться на удаленном компьютере, предоставляя все обычные возможности [отладки](../../debugging-python-in-visual-studio.md). Например, установите точку останова в строке `if guess < number:`, затем переключитесь на удаленный компьютер и введите другую догадку. После этого Visual Studio на локальном компьютере останавливается в этой точке останова, показывает локальные переменные и т. д.

    ![Visual Studio приостанавливает отладку при попадании в точку останова](../../media/remote-debugging-breakpoint-hit.png)

1. При остановке отладки Visual Studio отключается от программы, которая продолжает выполняться на удаленном компьютере. Библиотека debugpy также продолжает прослушивать присоединение отладчиков, поэтому можно повторно присоединиться к процессу в любое время.

### <a name="connection-troubleshooting"></a>Устранение неполадок при подключении

1. Убедитесь, что для параметра **Тип подключения** выбрано значение **Python remote (debugpy)** (Удаленная отладка Python (debugpy)).
1. Убедитесь, что секрет в поле **Цель подключения** точно соответствует секрету в удаленном коде.
1. Убедитесь, что IP-адрес в поле **Цель подключения** точно совпадает с IP-адресом удаленного компьютера.
1. Убедитесь, что на удаленном компьютере открыт порт удаленной отладки, а в целевой объект соединения включен суффикс порта, такой как `:5678`.
    - Чтобы использовать другой порт, укажите его в `listen`, как в `debugpy.listen((host, port))`. В этом случае откройте соответствующий порт в брандмауэре.
1. Убедитесь, что установленная версия debugpy на удаленном компьютере, возвращенная `pip3 list`, соответствует используемой версии инструментов Python в Visual Studio в таблице ниже. При необходимости обновите debugpy на удаленном компьютере.

    | Версия Visual Studio | Версия инструментов Python или debugpy |
    | --- | --- |
    | 2019 16.6 | 1.0.0b5 |
    | 2019 16.5 | 1.0.0b1 |

> [!NOTE]
> В Visual Studio 2019 версий 16.0–16.4 использовалась ptvsd, а не debugpy. Процесс в этом пошаговом руководстве для этих версий аналогичен, но имена функций отличаются. В Visual Studio 2019 версии 16.5 используется debugpy, но имена функций совпадают с именами в ptvsd. Вместо `listen` используется `enable_attach`. Вместо `wait_for_client` используется `wait_for_attach`. Вместо `breakpoint` используется `break_into_debugger`.

## <a name="using-ptvsd-3x-for-legacy-debugging"></a>Использование ptvsd версии 3.x для отладки в прежних версиях
Visual Studio 2017 версии 15.8 и более поздних версий использует отладчик на основе ptvsd версии 4.1 и более поздних. Visual Studio 2019 версии 16.5 и последующих версий использует отладчик на основе debugpy. Эти версии отладчика совместимы с Python 2.7, а также Python 3.5 и последующих версий. Если вы используете Python 2.6 и 3.1–3.4 или IronPython, Visual Studio отображает ошибку **Debugger does not support this Python environment** (Отладчик не поддерживает эту среду Python). Следующие сведения относятся только к удаленной отладке с помощью ptvsd версии 3.x.

1. При использовании ptvsd 3.x функции `enable_attach` требуется передавать "секрет" в качестве первого аргумента, который ограничивает доступ к выполняющемуся скрипту. Этот секрет нужно ввести при присоединении удаленного отладчика. Хотя это не рекомендуется, можно разрешить подключаться любым пользователям с помощью `enable_attach(secret=None)`.

1. Целевой URL-адрес подключения — `tcp://<secret>@<ip_address>:5678`, где `<secret>` — это функция `enable_attach`, передаваемая в виде строки в коде Python.

По умолчанию подключение к серверу удаленной отладки ptvsd 3.x защищено только с помощью секрета, а все данные передаются в виде обычного текста. Для более безопасного соединения ptvsd 3.x поддерживает SSL с использованием протокола `tcsp`, который настраивается следующим образом.

1. На удаленном компьютере создайте отдельный самозаверяющий сертификат и файлы ключа, используя openssl:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    При появлении запроса openssl укажите имя узла или IP-адрес (то, что вы использовали для подключения) в качестве **общего имени**.

    (Дополнительные сведения см. в разделе [Самозаверяющие сертификаты](https://docs.python.org/3/library/ssl.html#self-signed-certificates) документации по модулю Python `ssl`. Обратите внимание, что команда в этой документации создает только один объединенный файл.)

1. В коде измените вызов `enable_attach` для включения аргументов `certfile` и `keyfile`, используя имена файлов в качестве значений аргументов (эти аргументы имеют то же значение, что и для стандартной функции Python `ssl.wrap_socket`).

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    То же изменение можно внести в файл кода на локальном компьютере, но так как этот код не выполнялся, делать это необязательно.

1. Перезапустите программу Python на удаленном компьютере, подготовив ее к отладке.

1. Обеспечьте безопасность канала, добавив сертификат в доверенный корневой ЦС на компьютере с ОС Windows, где установлена Visual Studio:

    1. Скопируйте файл сертификата с удаленного компьютера на локальный.
    1. Откройте **панель управления** и перейдите к компоненту **Администрирование** > **Управление сертификатами компьютера**.
    1. В открывшемся окне в левой части разверните узел **Доверенные корневые центры сертификации**, правой кнопкой мыши щелкните **Сертификаты** и выберите пункты **Все задачи** > **Импорт**.
    1. Найдите и выберите файл *CER*, скопированный с удаленного компьютера, а затем выполните действия, описанные в диалоговых окнах, чтобы завершить импорт.

1. Повторите процесс присоединения в Visual Studio, как было описано ранее, используя `tcps://` в качестве протокола для параметра **Цель подключения** (или **Квалификатор**).

    ![Выбор транспорта удаленной отладки с использованием протокола SSL](../../media/remote-debugging-qualifier-ssl.png)

1. Visual Studio выведет предупреждение о возможных проблемах с сертификатами при подключении по протоколу SSL. Можно игнорировать эти предупреждения и продолжить работу. Но несмотря на то, что канал по-прежнему шифруется от перехвата, он может быть уязвим для атак "злоумышленник в середине".

    1. Если отображается предупреждение о том, что **удаленный сертификат не является доверенным**, это означает, что для доверенного корневого ЦС не был правильно добавлен сертификат. Проверьте эти действия и повторите попытку.

        ![Предупреждение о доверенном сертификате SSL](../../media/remote-debugging-ssl-warning.png)

    1. Если выводится предупреждение о том, что **имя удаленного сертификата не соответствует имени узла**, это означает, что при создании сертификата использовалось неправильное имя узла или IP-адрес в качестве **общего имени**.

        ![Предупреждение об имени узла сертификата SSL](../../media/remote-debugging-ssl-warning2.png)
