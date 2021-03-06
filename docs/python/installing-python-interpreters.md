---
title: Выбор и установка интерпретаторов Python
description: Полный список интерпретаторов Python, поддерживаемых в Visual Studio, с краткими инструкциями по поиску их установщиков.
ms.date: 06/05/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8070bb93a1dd76ad29832afae15d83788300ae7a
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2021
ms.locfileid: "107941114"
---
# <a name="install-python-interpreters"></a>Установка интерпретаторов Python

По умолчанию при установке рабочей нагрузки Python для разработки в Visual Studio 2017 и более поздних версий также устанавливается Python 3 (64-разрядная версия). При необходимости вы можете установить 32-разрядную и 64-разрядную версии Python 2, Python 3 вместе с Miniconda (Visual Studio 2019) или Anaconda 2/Anaconda 3 (Visual Studio 2017), как описано в руководстве по [установке](installing-python-support-in-visual-studio.md).

::: moniker range=">=vs-2019"
Кроме того, вы можете установить стандартные интерпретаторы из диалогового окна **Add Environment** (Добавление среды). Выберите команду **Add Environment** (Добавление среды) в окне **Python Environments** (Среды Python) или в панели инструментов Python, выберите вкладку **Python installation** (Установка Python), укажите интерпретаторы для установки и нажмите **Install** (Установить).
::: moniker-end

Кроме того, любой интерпретатор из приведенной ниже таблицы можно установить вручную, не используя Visual Studio Installer. Например, если вы установили Anaconda 3 еще до установки Visual Studio, нет необходимости снова устанавливать этот дистрибутив с помощью Visual Studio Installer. Вы также можете установить интерпретатор вручную, если, например, доступна новая версия, которая пока что не отображается в установщике Visual Studio.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio поддерживает Python версии 2.7, а также версии 3.5–3.7. Visual Studio можно использовать для редактирования кода, написанного на языке Python других версий, но эти версии официально не поддерживаются, а функции, такие как IntelliSense и отладка, могут не работать.
::: moniker-end

Для **Visual Studio 2015 и более ранних версий** нужно вручную установить один из интерпретаторов.

Visual Studio (любой версии) автоматически обнаруживает все установленные интерпретаторы Python и окружения для них, проверяя значения в реестре (согласно [описанию регистрации Python в реестре Windows 514 PEP](https://www.python.org/dev/peps/pep-0514/)). Установки Python обычно находятся в разделе **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-разрядная версия) и **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-разрядная версия), затем в узлах для распределения, таких как **PythonCore** (CPython) и **ContinuumAnalytics** (Anaconda).

Если Visual Studio не сможет обнаружить установленное окружение, см. раздел [Указание существующего окружения вручную](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio отображает все известные окружения в окне [**Окружения Python**](managing-python-environments-in-visual-studio.md#the-python-environments-window) и автоматически обнаруживает обновления для существующих интерпретаторов.

| Интерпретатор | Описание |
| --- | --- |
| [CPython](https://www.python.org/) | Собственный и самый используемый интерпретатор доступен в 32- и 64-разрядных версиях (рекомендуется 32-разрядная). Он предоставляет последние возможности языка, максимальную совместимость пакета Python, полную поддержку отладки и взаимодействие с [IPython](https://ipython.org/). См. также статью о [сравнении Python 2 и Python 3](https://wiki.python.org/moin/Python2orPython3). Имейте в виду, что Visual Studio 2015 и более ранние версии не поддерживают Python 3.6, и в них может появиться ошибка **Неподдерживаемая версия Python 3.6**. Используйте Python 3.5 или более раннюю версию. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Реализация .NET для Python (доступна 32- и 64-разрядная версия), обеспечивающая взаимодействие с C#, F# и Visual Basic, доступ к API-интерфейсам .NET, стандартную отладку Python (но не отладку в смешанном режиме C++) и отладку в смешанном режиме IronPython и C#. Однако IronPython не поддерживает виртуальные среды. |
| [Anaconda](https://www.continuum.io) | Открытая платформа для анализа и обработки данных на базе Python, которая включает в себя последнюю версию CPython и большинство пакетов со сложной установкой. Рекомендуем использовать этот интерпретатор, если вы не можете определиться. |
| [PyPy](https://www.pypy.org/) | Реализация JIT для Python с высокопроизводительной трассировкой, которая хорошо подходит для долго выполняющихся программ и ситуаций, когда вы обнаружили проблемы с производительностью, которые не удается устранить другими способами. Работает с Visual Studio, но имеет ограниченную поддержку расширенных возможностей отладки. |
| [Jython](https://www.jython.org/) | Реализация Python на виртуальной машине Java (JVM). Аналогично IronPython, код, выполняемый в Jython, может взаимодействовать с классами и библиотеками Java, но не может использовать многие библиотеки, предназначенные для CPython. Работает с Visual Studio, но имеет ограниченную поддержку расширенных возможностей отладки. |

Сведения о новых способах обнаружения сред Python см. в статье [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Обнаружение среды PTVS) на сайте github.com.

## <a name="move-an-interpreter"></a>Перемещение интерпретатора

Если вы переместите существующий интерпретатор в новое расположение с помощью средств файловой системы, Visual Studio не сможет отследить изменение автоматически.

- Если изначально вы указали расположение интерпретатора в окне **Окружения Python**, укажите новое расположение, изменив параметры окружения на вкладке **Настройка** в этом же окне. См. раздел [Указание существующего окружения вручную](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Если вы установили интерпретатор с помощью установщика, выполните следующие действия для переустановки интерпретатора в новом расположении:

  1. Верните интерпретатор Python в исходное расположение.
  2. Удалите интерпретатор с помощью установщика, который очистит записи в реестре.
  3. Установите интерпретатор заново в нужном расположении.
  4. Перезапустите Visual Studio и убедитесь, что новое расположение обнаружено автоматически и указано вместо старого.

Такой процесс позволяет гарантировать, что в реестре правильно обновятся записи о расположении интерпретатора, которое использует Visual Studio. Также установщик устраняет все возможные побочные эффекты.

## <a name="see-also"></a>См. также

- [Управление средами Python](managing-python-environments-in-visual-studio.md)
- [Выбор интерпретатора для проекта](selecting-a-python-environment-for-a-project.md)
- [Использование файла requirements.txt для зависимостей](managing-required-packages-with-requirements-txt.md)
- [Пути поиска](search-paths.md)
- [Справочная информация по окну "Окружения Python"](python-environments-window-tab-reference.md)
