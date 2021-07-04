---
title: Установка средств поддержки Python
description: Инструкции по установке средств Python для Visual Studio (PTVS) в Visual Studio 2017, 2015, 2013, 2012 и 2010, включая параметры и расположения установки.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09fb452d579130cdf6597ada3af509b35f24ff43
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254814"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Как установить поддержку Python в Visual Studio под управлением Windows

Чтобы установить поддержку Python для Visual Studio (Инструменты Python для Visual Studio или PTVS), выполните инструкции из раздела, который соответствует вашей версии Visual Studio:

- [Visual Studio 2017 и Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 и более ранние версии](#visual-studio-2013-and-earlier)

Чтобы быстро проверить поддержку Python после установки, откройте **интерактивное окно Python**. Для этого нажмите клавиши **ALT**+**I** и введите `2+2`. Если вы не увидите результат `4`, проверьте выполненные действия.

> [!Tip]
> Рабочая нагрузка Python содержит полезное расширение Cookiecutter, которое предоставляет графический пользовательский интерфейс для поиска шаблонов, ввода параметров шаблонов и создания проектов и файлов. Дополнительные сведения см. в статье [Использование расширения Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Сейчас Python не поддерживается в Visual Studio для Mac, однако доступен в Mac и Linux посредством Visual Studio Code. См. [вопросы и ответы](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 и Visual Studio 2017

1. Скачайте и запустите последнюю версию Visual Studio Installer. Если вы уже установили Visual Studio, запустите Visual Studio Installer, выберите вариант **Изменить** (см. раздел [Изменение Visual Studio](../install/modify-visual-studio.md)) и перейдите к шагу 2.

    > [!div class="nextstepaction"]
    > [Установка Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Выпуск Community предназначен для индивидуальных разработчиков, использования при аудиторном обучении и в научных исследованиях, а также разработки решений с открытым кодом. Если программу планируется использовать в других целях, установите [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) или [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. В установщике предлагается список рабочих нагрузок, то есть групп связанных параметров для определенных целей разработки. Для Python выберите рабочую нагрузку **Разработка на Python**.

    ![Рабочая нагрузка разработки Python в установщике Visual Studio](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Необязательно: если вы занимаетесь обработкой и анализом данных, также рекомендуется установить рабочую нагрузку **Приложения для обработки и анализа данных и аналитические приложения**. Эта рабочая нагрузка включает в себя поддержку языков Python, R и F#. Дополнительные сведения см. в разделе [Рабочая нагрузка "Приложения для обработки и анализа данных и аналитические приложения"](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Рабочие нагрузки для Python и обработки и анализа данных доступны только в Visual Studio2017 версии 15.2 и выше.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Необязательно: если вы занимаетесь обработкой и анализом данных, также рекомендуется установить рабочую нагрузку **Приложения для обработки и анализа данных и аналитические приложения**. Эта рабочая нагрузка включает в себя поддержку Python и F#. Дополнительные сведения см. в разделе [Рабочая нагрузка "Приложения для обработки и анализа данных и аналитические приложения"](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. В правой области установщика при необходимости выберите дополнительные параметры. Чтобы принять параметры по умолчанию, пропустите этот шаг.

    ::: moniker range="vs-2017"
    ![Параметры разработки Python в установщике Visual Studio](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Параметры разработки Python в установщике Visual Studio 2019](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Параметр | Описание |
    | --- | --- |
    | Дистрибутивы Python | Выберите любое сочетание доступных дистрибутивов 32- и 64-разрядных версий Python 2, Python 3, Miniconda, Anaconda2 и Anaconda3, с которыми вы планируете работать. Каждый дистрибутив включает в себя интерпретатор, среду выполнения и библиотеки. В частности, Anaconda — это открытая платформа обработки и анализа данных, которая включает в себя множество предварительно установленных пакетов. (Вы можете в любой момент вернуться в установщик Visual Studio, чтобы добавить или удалить дистрибутивы.)  **Примечание**. Если вы установили дистрибутив без использования установщика Visual Studio, вам не нужно выполнять дополнительные действия. Visual Studio автоматически определяет существующие установки Python. См. [Окно "Окружения Python"](managing-python-environments-in-visual-studio.md#the-python-environments-window). Кроме того, если доступна более новая версия Python, чем показанная в установщике, то вы можете установить эту версию отдельно, и Visual Studio обнаружит ее. |
    | **Поддержка шаблонов Cookiecutter** | Устанавливает графический пользовательский интерфейс Cookiecutter для поиска шаблонов, ввода их параметров и создания проектов и файлов. См. раздел [Использование расширения Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Поддержка веб-приложений Python** | Устанавливает средства для разработки веб-приложений, включая поддержку редактирования кода HTML, CSS и JavaScript, а также шаблоны проектов на основе платформ Bottle, Flask и Django. См. статью [Шаблоны веб-проектов Python](python-web-application-project-templates.md). |
    | **Поддержка Интернета вещей для Python** | Поддерживает разработку для Windows IoT Core с помощью Python. |
    | **Встроенные средства разработки Python** | Устанавливает компилятор C++ и другие компоненты, необходимые для разработки собственных расширений для Python. См. статью [Создание расширения C++ для Python](working-with-c-cpp-python-in-visual-studio.md). Чтобы обеспечить полную поддержку С++, установите рабочую нагрузку **Разработка классических приложений на C++** . |
    | **Основные инструменты облачных служб Azure** | Обеспечивает дополнительную поддержку для разработки облачных служб Azure на Python. См. статью [Проекты облачных служб Azure](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Параметр | Описание |
    | --- | --- |
    | Дистрибутивы Python | Выберите любое сочетание доступных дистрибутивов 32- и 64-разрядных версий Python 2, Python 3, Miniconda, Anaconda2 и Anaconda3, с которыми вы планируете работать. Каждый дистрибутив включает в себя интерпретатор, среду выполнения и библиотеки. В частности, Anaconda — это открытая платформа обработки и анализа данных, которая включает в себя множество предварительно установленных пакетов. (Вы можете в любой момент вернуться в установщик Visual Studio, чтобы добавить или удалить дистрибутивы.)  **Примечание**. Если вы установили дистрибутив без использования установщика Visual Studio, вам не нужно выполнять дополнительные действия. Visual Studio автоматически определяет существующие установки Python. См. [Окно "Окружения Python"](managing-python-environments-in-visual-studio.md#the-python-environments-window). Кроме того, если доступна более новая версия Python, чем показанная в установщике, то вы можете установить эту версию отдельно, и Visual Studio обнаружит ее. |
    | **Поддержка шаблонов Cookiecutter** | Устанавливает графический пользовательский интерфейс Cookiecutter для поиска шаблонов, ввода их параметров и создания проектов и файлов. См. раздел [Использование расширения Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Поддержка веб-приложений Python** | Устанавливает средства для разработки веб-приложений, включая поддержку редактирования кода HTML, CSS и JavaScript, а также шаблоны проектов на основе платформ Bottle, Flask и Django. См. статью [Шаблоны веб-проектов Python](python-web-application-project-templates.md). |
    | **Встроенные средства разработки Python** | Устанавливает компилятор C++ и другие компоненты, необходимые для разработки собственных расширений для Python. См. статью [Создание расширения C++ для Python](working-with-c-cpp-python-in-visual-studio.md). Чтобы обеспечить полную поддержку С++, установите рабочую нагрузку **Разработка классических приложений на C++** . |
    ::: moniker-end

1. После установки в установщике предлагаются команды для изменения, запуска, восстановления и удаления Visual Studio. Если доступны обновления для установленных компонентов Visual Studio, кнопка **Изменить** меняется на **Обновить**. (Команду **Изменить** в этом случае можно выбрать в раскрывающемся меню.) Запускать среду Visual Studio и установщик можно также из меню **Пуск** в Windows. Для этого выполните поиск по запросу "Visual Studio".

    ![Запуск, изменение или удаление Visual Studio посредством установщика](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Устранение неполадок

Если у вас возникли проблемы при установке или запуске Python в Visual Studio, попробуйте сделать следующее:

- Определите, возникает ли та же ошибка при использовании Python CLI, то есть при запуске *python.exe* из командной строки.
- Воспользуйтесь [**восстановлением**](../install/repair-visual-studio.md) Visual Studio.
- Восстановите или переустановите Python через **Параметры** > **Приложения и компоненты** в Windows.

**Пример ошибки**. Не удалось запустить интерактивный процесс: System.ComponentModel.Win32Exception (0x80004005): Неизвестная ошибка (0xc0000135) в Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Чтобы запустить установщик Visual Studio, откройте **Панель управления > Программы и компоненты**, затем выберите **Microsoft Visual Studio 2015** и нажмите кнопку **Изменить**.

1. В самом установщике выберите действие **Изменить**.

1. Выберите **Языки программирования** > **Инструменты Python для Visual Studio** и щелкните **Далее**:

    ![Выбор PTVS в установщике Visual Studio 2015](media/installation-vs2015.png)

1. Когда завершится работа установщика Visual Studio, [установите любой интерпретатор Python на свой выбор](installing-python-interpreters.md). Visual Studio 2015 поддерживает только Python версии 3.5 и более ранних. При использовании более поздних версий отображается сообщение об ошибке, например **Неподдерживаемая версия Python 3.6**). Если интерпретатор уже установлен, но Visual Studio не обнаруживает его автоматически, см. руководство по [определению существующего окружения вручную](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 и более ранние версии

1. Установите версию Инструментов Python для Visual Studio, соответствующую вашей версии Visual Studio.

    - Visual Studio 2013: [PTVS 2.2.2 для Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2) В Visual Studio 2013 этот процесс можно запустить через диалоговое окно **Файл** > **Новый проект**.
    - Visual Studio 2010 и 2012: [PTVS 2.1.1 для Visual Studio 2010 и 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Selecting and installing Python interpreters](installing-python-interpreters.md) (Установка и настройка интерпретаторов Python). Если интерпретатор уже установлен, но Visual Studio не обнаруживает его автоматически, см. руководство по [определению существующего окружения вручную](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Расположения установки

По умолчанию поддержка Python устанавливается для всех пользователей на компьютере.

В Visual Studio 2019 и Visual Studio 2017 рабочая нагрузка Python устанавливается в каталог *%ProgramFiles(x86)%\Microsoft Visual Studio\\<версия_Visual_Studio>\\<выпуск_Visual_Studio>Common7\IDE\Extensions\Microsoft\Python*, где &lt;версия_Visual_Studio&gt; — это 2019 или 2017, а &lt;выпуск_Visual_Studio&gt; — Community, Professional или Enterprise.

В Visual Studio 2015 и более ранних версиях используются такие пути установки:

- 32-разрядная версия.
  - Путь: *%Program Files(x86)%\Microsoft Visual Studio \<VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<версия_PTVS>*
  - Расположение пути в реестре: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<версия_Visual_Studio>\InstallDir**
- 64-разрядная версия.
  - Путь: *%Program Files%\Microsoft Visual Studio \<VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<версия_PTVS>*
  - Расположение пути в реестре: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<версия_Visual_Studio>\InstallDir**

Здесь:

- &lt;VS_ver&gt; принимает одно из этих значений:
  - 14.0 for Visual Studio 2015
  - 12.0 for Visual Studio 2013
  - 11.0 for Visual Studio 2012
  - 10.0 for Visual Studio 2010
- &lt;PTVS_ver&gt; — это номер версии, например 2.2.2, 2.1.1, 2.0, 1.5, 1.1 или 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Пользовательские установки (для версии 1.5 и более ранних)

Инструменты Python для Visual Studio 1.5 и более ранних версий можно установить только для текущего пользователя. Путь установки будет выглядеть так: *%LocalAppData%\Microsoft\VisualStudio\\<версия_Visual_Studio>\Extensions\Microsoft\Python Tools for Visual Studio\\<версия_PTVS>* . Здесь &lt;версия_Visual_Studio&gt; и &lt;версия_PTVS&gt; имеют то же значение, которое описано выше.
