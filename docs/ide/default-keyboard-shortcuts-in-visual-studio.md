---
title: Сочетания клавиш по умолчанию
description: Сведения о сочетаниях клавиш по умолчанию в Visual Studio, которые позволяют выполнять различные команды и открывать разные окна.
ms.custom: SEO-VS-2020
ms.date: 06/21/2021
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dec9f76f2b21e11cc79bc55efc4a2de6fb7dedc3
ms.sourcegitcommit: 15821c790d6498210f30b3268402ffad6bb70c7c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2021
ms.locfileid: "113725525"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Сочетания клавиш по умолчанию в Visual Studio

Сочетания клавиш позволяют получать доступ к различным [командам](reference/visual-studio-commands.md) и окнам Visual Studio. В этом разделе перечислены сочетания клавиш по умолчанию для команд в профиле **обычных параметров**, который мог быть выбран при установке Visual Studio. Независимо от выбранного профиля сочетание клавиш для той или иной команды можно [определить](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md), открыв диалоговое окно **Параметры**, развернув узел **Среда** и выбрав элемент **Клавиатура**. Кроме того, сочетания клавиш можно настраивать, назначая командам другие сочетания клавиш.

Список распространенных сочетаний клавиш и другие сведения о средствах повышения производительности см. в следующих статьях:

- [Советы по использованию клавиатуры](../ide/productivity-shortcuts.md)
- [Советы по повышению производительности](../ide/productivity-features.md).

Подробные сведения о специальных возможностях в Visual Studio см. в статьях [Советы и рекомендации по специальным возможностям для Visual Studio](../ide/reference/accessibility-tips-and-tricks.md) и [Практическое руководство. Работа только с клавиатуры](../ide/reference/how-to-use-the-keyboard-exclusively.md).

<a name="popular"></a>
## <a name="popular-keyboard-shortcuts-for-visual-studio"></a>Популярные сочетания клавиш в Visual Studio

Все сочетания клавиш в этом разделе применяются глобально, если не указано иное. *Глобальный* контекст означает, что сочетание применяется в любом окне инструментов в Visual Studio.

> [!NOTE]
> Сочетание клавиш для той или иной команды можно [определить](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md), открыв диалоговое окно **Параметры**, развернув узел **Среда** и выбрав элемент **Клавиатура**.


#### <a name="build-popular-shortcuts"></a>Сборка: популярные сочетания клавиш

|Команды|Сочетания клавиш |Идентификатор команды|
|-|-|-|
|Построить решение|**CTRL+SHIFT+B** | Build.BuildSolution |
|Отменить|**CTRL+BREAK** | Build.Cancel |
|Компилятор|**CTRL+F7** | Build.Compile |
|Выполнить анализ кода в решении|**ALT+F11**| Build.RunCodeAnalysisonSolution |

#### <a name="debug-popular-shortcuts"></a>Отладка: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|Идентификатор команды|
|-|-|-|
|Прерывание на функции|**CTRL+B**| Debug.BreakatFunction |
|Приостановить все|**CTRL+ALT+BREAK**| Debug.BreakAll |
|Удаление всех точек останова|**CTRL+SHIFT+F9**| Debug.DeleteAllBreakpoints |
|Исключения|**CTRL+ALT+E**| Debug.Exceptions |
|Быстрая проверка|**CTRL+ALT+Q**<br /><br />или **Shift + F9**| Debug.QuickWatch |
|Перезагрузить|**CTRL+SHIFT+F5**| Debug.Restart |
|Выполнить до текущей позиции|**CTRL+F10**| Debug.RunToCursor |
|Установка следующей инструкции|**CTRL+SHIFT+F10**| Debug.SetNextStatement |
|Начать|**F5**| Debug.Start |
|Запуск без отладки|**CTRL+F5**| Debug.StartWithoutDebugging |
|Шаг с заходом|**F11**| Debug.StepInto |
|Шаг с выходом|**SHIFT+F11**| Debug.StepOut |
|Шаг с обходом|**F10**| Debug.StepOver |
|Остановка отладки|**SHIFT+F5**| Debug.StopDebugging |
|Переключить точку останова|**F9**| Debug.ToggleBreakpoint |

#### <a name="edit-popular-shortcuts"></a>Редактирование: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|Идентификатор команды|
|-|-|-|
|Разрыв строки|**ВВОД** [текстовый редактор, конструктор отчетов, конструктор Windows Forms]<br /><br />или **SHIFT+ВВОД** [текстовый редактор]| Edit.BreakLine |
|Свернуть в определения|**CTRL+M**, **CTRL+O** [текстовый редактор]| Edit.CollapseToDefinitions |
|Закомментировать выделенный фрагмент|**CTRL+K**, **CTRL+C** [текстовый редактор]| Edit.CommentSelection |
|Дополнить слово|**ALT+СТРЕЛКА ВПРАВО** [текстовый редактор, конструктор рабочих процессов]<br /><br />или **CTRL+ПРОБЕЛ** [текстовый редактор, конструктор рабочих процессов]<br /><br />или **CTRL+K**, **W** [конструктор рабочих процессов]<br /><br />или **CTRL+K, CTRL+W** [конструктор рабочих процессов]| Edit.CompleteWord |
|Копировать|**CTRL+C**<br /><br />или **Ctrl + Insert**| Edit.Copy |
|Вырезать|**CTRL+X**<br /><br />или **SHIFT + DELETE**| Edit.Cut |
|Удалить|**DELETE** [Team Explorer]<br /><br />или **SHIFT+DELETE** [схема последовательностей, схема действий UML, схема слоев]<br /><br />или **CTRL+DELETE** [схема классов]| Edit.Delete |
|Поиск|**CTRL+F**| Edit.Find |
|Найти все ссылки|**SHIFT+F12**| Edit.FindAllReferences |
|Поиск в файлах|**CTRL+SHIFT+F**| Edit.FindinFiles |
|Найти далее|**F3**| Edit.FindNext |
|Найти следующий выделенный фрагмент|**CTRL+F3**| Edit.FindNextSelected |
|Форматировать документ|**CTRL+K, CTRL+D** [текстовый редактор]| Edit.FormatDocument |
|форматирование выделенного фрагмента;|**CTRL+K, CTRL+F** [текстовый редактор]| Edit.FormatSelection |
|Перейти|**CTRL+G**| Edit.GoTo |
|Перейти к объявлению|**CTRL+F12**| Edit.GoToDeclaration |
|Перейти к определению|**F12**| Edit.GoToDefinition |
|Перейти к полю поиска со списком|**CTRL+D**| Edit.GoToFindCombo |
|Перейти к следующему расположению|**F8**| Edit.GoToNextLocation |
|Вставить фрагмент|**Ctrl + K**, **Ctrl + X**| Edit.InsertSnippet |
|Вкладка «Вставить»|**TAB** [конструктор отчетов, конструктор Windows Forms, текстовый редактор]| Edit.InsertTab |
|Вырезать строку|**CTRL+L** [текстовый редактор]| Edit.LineCut |
|Выделить строку вниз по столбцу|**SHIFT+ALT+СТРЕЛКА ВНИЗ** [текстовый редактор]| Edit.LineDownExtendColumn |
|Открыть строку выше|**CTRL+ВВОД** [текстовый редактор]| Edit.LineOpenAbove |
|Показать список элементов|**CTRL+J** [текстовый редактор, конструктор рабочих процессов]<br /><br />или **CTRL+K, CTRL+L** [конструктор рабочих процессов]<br /><br />или **CTRL+K, L** [конструктор рабочих процессов]| Edit.ListMembers |
|Перейти к|**CTRL+,**| Edit.NavigateTo |
|Открывает файл|**CTRL+SHIFT+G**| Edit.OpenFile |
|Режим замены|**INSERT** [текстовый редактор]| Edit.OvertypeMode |
|Сведения о параметрах|**CTRL+SHIFT+ПРОБЕЛ** [текстовый редактор, конструктор рабочих процессов]<br /><br />или **CTRL+K, CTRL+P** [конструктор рабочих процессов]<br /><br />или **CTRL+K, P** [конструктор рабочих процессов]| Edit.ParameterInfo |
|Вставить|**CTRL+V**<br /><br />или **SHIFT + INSERT**| Edit.Paste |
|Показать определение|**ALT+F12** [текстовый редактор]| Edit.PeekDefinition |
|Повторить|**CTRL+Y**<br /><br />или **SHIFT + ALT + BACKSPACE**<br /><br />или **CTRL + SHIFT + Z**| Edit.Redo |
|Заменить|**CTRL+H**| Edit.Replace |
|Выбрать все|**CTRL+A**| Edit.SelectAll |
|Выбрать текущее слово|**CTRL+W** [текстовый редактор]| Edit.SelectCurrentWord |
|Отмена выделения|**ESC** [текстовый редактор, конструктор отчетов, конструктор параметров, конструктор Windows Forms, редактор управляемых ресурсов]| Edit.SelectionCancel |
|Окружить|**CTRL+K, CTRL+S**| Edit.SurroundWith |
|На один знак табуляции влево|**SHIFT+TAB** [текстовый редактор, конструктор отчетов, конструктор Windows Forms]| Edit.TabLeft |
|Свернуть/развернуть все сегменты|**CTRL+M, CTRL+L** [текстовый редактор]| Edit.ToggleAllOutlining |
|Переключить закладку|**CTRL+K, CTRL+K** [текстовый редактор]| Edit.ToggleBookmark |
|Переключить режим завершения|**CTRL+ALT+ПРОБЕЛ** [текстовый редактор]| Edit.ToggleCompletionMode |
|Свернуть/развернуть сегмент|**CTRL+M, CTRL+M** [текстовый редактор]| Edit.ToggleOutliningExpansion |
|Раскомментировать выделенный фрагмент|**CTRL+K, CTRL+U** [текстовый редактор]| Edit.UncommentSelection |
|Отменить|**CTRL+Z**<br /><br />или **ALT + BACKSPACE**| Edit.Undo |
|Удалить до конца слова|**CTRL+DELETE** [текстовый редактор]| Edit.WordDeleteToEnd |
|Удалить до начала слова|**CTRL+BACKSPACE** [текстовый редактор]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a>Файл: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|Идентификатор команды|
|-|-|-|
|Выход|**ALT+F4**| File.Exit |
|Создание файла|**CTRL+N**| File.NewFile |
|Новый проект|**CTRL+SHIFT+N**| File.NewProject |
|Новый веб-сайт|**SHIFT+ALT+N**| File.NewWebSite |
|Открывает файл|**CTRL+O**| File.OpenFile |
|Открытие проекта|**CTRL+SHIFT+O**| File.OpenProject |
|Открыть веб-сайт|**Shift+Alt+O**| File.OpenWebSite |
|Переименовать|**F2** [Team Explorer]| File.Rename |
|Сохранить все|**CTRL+SHIFT+S**| File.SaveAll |
|Сохранить выбранные элементы|**CTRL+S**| File.SaveSelectedItems |
|Просмотр в браузере|**CTRL+SHIFT+W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a>Проект: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|Идентификатор команды|
|-|-|-|
|Добавить существующий элемент|**SHIFT+ALT+A**| Project.AddExistingItem |
|Добавление нового элемента|**CTRL+SHIFT+A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a>Рефакторинг: популярные сочетания клавиш

|Команда|Сочетание клавиш [специальные контексты]|Идентификатор команды|
|-|-|-|
|Извлечение метода|**CTRL+R, CTRL+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a>Средства: популярные сочетания клавиш

|Команда|Сочетание клавиш [специальные контексты]|Идентификатор команды|
|-|-|-|
|Присоединение к процессу|**CTRL+ALT+P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a>Представление: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|Идентификатор команды|
|-|-|-|
|Окно классов|**CTRL+SHIFT+C**| View.ClassView |
|Изменить метку|**F2**| View.EditLabel |
|Список ошибок|**CTRL+\\, CTRL+E**<br /><br />или **CTRL +\\, E**| View.ErrorList |
|Перейти назад|**CTRL+-**| View.NavigateBackward |
|Перейти вперед|**CTRL+SHIFT+-**| View.NavigateForward |
|Обозреватель объектов|**CTRL+ALT+J**| View.ObjectBrowser |
|Выходные данные|**CTRL+ALT+O**| View.Output |
|Окно "Свойства"|**F4**| View.PropertiesWindow |
|Обновить|**F5** [Team Explorer]| View.Refresh |
|Обозреватель серверов|**CTRL+ALT+S**| View.ServerExplorer |
|Показать смарт-тег|**CTRL+.**<br /><br />или **SHIFT + ALT + F10** [HTML-редактор в конструкторе]| View.ShowSmartTag |
|Обозреватель решений|**CTRL+ALT+L**| View.SolutionExplorer |
|TFS Team Explorer|**CTRL+\\, CTRL+M**| View.TfsTeamExplorer |
|Панель элементов|**CTRL+ALT+X**| View.Toolbox |
|Просмотреть код|**ВВОД** [схема классов]<br /><br />или **F7** [конструктор параметров]| View.ViewCode |
|Конструктор представлений|**SHIFT+F7** [HTML-редактор в представлении кода]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a>Окно: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|Идентификатор команды|
|-|-|-|
|Активировать окно документа|**ESC**| Window.ActivateDocumentWindow |
|Закрыть окно документа|**CTRL+F4**| Window.CloseDocumentWindow |
|Следующее окно документа|**CTRL+F6**| Window.NextDocumentWindow |
|Следующая панель навигации окна документа|**CTRL+TAB**| Window.NextDocumentWindowNav |
|Следующая область разделения|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>Глобальные сочетания клавиш

Следующие сочетания клавиш являются *глобальными*. Это означает, что их можно использовать в любом окне Visual Studio, которое находится в фокусе.

- [Анализ](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)
- [Правка](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)
- [Project](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)
- [Тест](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)
- [Архитектура](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)
- [Контекстные меню редактора](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)
- [Контекстные меню проекта и решения](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)
- [Обозреватель тестов](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [Сборка](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)
- [Файл](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)
- [Рефакторинг](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)
- [Инструменты](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)
- [Контекстные меню представления классов](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)
- [Справка](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)
- [Обозреватель решений](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [Вид](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)
- [Отладка](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)
- [Нагрузочный тест](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)
- [Команда](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)
- [Окно](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)
- [Контекстные меню отладчика](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)
- [Другие контекстные меню](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)
- [Контекстные меню Team Foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)
- [Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)
- [Центр диагностики](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)

### <a name="analyze"></a><a name="bkmk_analyze"></a> Анализ

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Перейти назад|**SHIFT+ALT+3**| Analyze.NavigateBackward |
|Перейти вперед|**SHIFT+ALT+4**| Analyze.NavigateForward |

### <a name="architecture"></a><a name="bkmk_architecture"></a> Архитектура

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Создать схему|**CTRL+\\, CTRL+N**| Architecture.NewDiagram |

### <a name="build"></a><a name="bkmk_build"></a> Сборка

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Выделение построения|**CTRL+B** (Visual Studio 2019)| Build.BuildSelection |
|Построить решение|**CTRL+SHIFT+B**| Build.BuildSolution |
|Отменить|**CTRL+BREAK**| Build.Cancel |
|Компилятор|**CTRL+F7**| Build.Compile |
|Выполнить анализ кода в решении|**ALT+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus"></a><a name="bkmk_classview"></a> Контекстные меню представления классов

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Свойства|**ALT+ВВОД**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug"></a><a name="bkmk_debug"></a> Отладка

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Применить изменения кода|**ALT+F10**| Debug.ApplyCodeChanges |
|Подключить к процессу|**CTRL+ALT+P**| Debug.AttachtoProcess |
|Автоматические|**CTRL+ALT+V, A**| Debug.Autos |
|Приостановить все|**CTRL+ALT+BREAK**| Debug.BreakAll |
|Точки останова|**CTRL+ALT+B**| Debug.Breakpoints |
|Стек вызовов|**CTRL+ALT+C**| Debug.CallStack |
|Удаление всех точек останова|**CTRL+SHIFT+F9**| Debug.DeleteAllBreakpoints |
|Launch|**ALT+F2**| Debug.DiagnosticsHub.Launch |
|Дизассемблированный код|**CTRL+ALT+D**| Debug.Disassembly |
|Проводник DOM|**CTRL+ALT+V, D**| Debug.DOMExplorer |
|Включение точки останова|**CTRL+F9**| Debug.EnableBreakpoint |
|Исключения|**CTRL+ALT+E**| Debug.Exceptions |
|Точка останова в функции|**CTRL+K, B** (Visual Studio 2019)<br />**CTRL**+**B** (Visual Studio 2017)| Debug.FunctionBreakpoint |
|Перейти к предыдущему вызову или событию IntelliTrace|**CTRL+SHIFT+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|Начать диагностику|**ALT+F5**| Debug.Graphics.StartDiagnostics |
|Интерпретация|**CTRL+ALT+I**| Debug.Immediate |
|Вызовы IntelliTrace|**CTRL+ALT+Y, T**| Debug.IntelliTraceCalls |
|События IntelliTrace|**CTRL+ALT+Y, F**| Debug.IntelliTraceEvents |
|Консоль JavaScript|**CTRL+ALT+V, C**| Debug.JavaScriptConsole |
|Локальные|**CTRL+ALT+V, L**| Debug.Locals |
|Поле со списком процессов|**CTRL+5**| Debug.LocationToolbar.ProcessCombo |
|Поле со списком кадров стека|**CTRL+7**| Debug.LocationToolbar.StackFrameCombo |
|Поле со списком потоков|**CTRL+6**| Debug.LocationToolbar.ThreadCombo |
|Переключить помеченное состояние текущего потока|**CTRL+8**| Debug.LocationToolbar.ToggleCurrentThreadFlaggedState |
|Переключить помеченные потоки|**CTRL+9**| Debug.LocationToolbar.ToggleFlaggedThreads |
|Память 1|**CTRL+ALT+M, 1**| Debug.Memory1 |
|Память 2|**CTRL+ALT+M, 2**| Debug.Memory2 |
|Память 3|**CTRL+ALT+M, 3**| Debug.Memory3 |
|Память 4|**CTRL+ALT+M, 4**| Debug.Memory4 |
|Модули|**CTRL+ALT+U**| Debug.Modules |
|Параллельные стеки|**CTRL+SHIFT+D, S**| Debug.ParallelStacks |
|Параллельное контрольное значение 1|**CTRL+SHIFT+D, 1**| Debug.ParallelWatch1 |
|Параллельное контрольное значение 2|**CTRL+SHIFT+D, 2**| Debug.ParallelWatch2 |
|Параллельное контрольное значение 3|**CTRL+SHIFT+D, 3**| Debug.ParallelWatch3 |
|Параллельное контрольное значение 4|**CTRL+SHIFT+D, 4**| Debug.ParallelWatch4 |
|Процессы|**CTRL+ALT+Z**| Debug.Processes |
|Быстрая проверка|**SHIFT+F9** или **CTRL+ALT+Q**| Debug.QuickWatch |
|Снова подключиться к процессу|**SHIFT+ALT+P**| Debug.ReattachtoProcess |
|Обновить приложение Windows|**CTRL+SHIFT+R**| Debug.RefreshWindowsapp |
|Регистры|**CTRL+ALT+G**| Debug.Registers |
|Перезагрузить|**CTRL+SHIFT+F5**| Debug.Restart |
|Выполнить до текущей позиции|**CTRL+F10**| Debug.RunToCursor |
|Установка следующей инструкции|**CTRL+SHIFT+F10**| Debug.SetNextStatement |
|Показать стек вызовов на карте кода|**CTRL+SHIFT+`**| Debug.ShowCallStackonCodeMap |
|Отображение следующей инструкции|**ALT+NUM** *| Debug.ShowNextStatement |
|Начать|**F5**| Debug.Start |
|Запустить анализ приложения Windows Phone|**ALT+F1**| Debug.StartWindowsPhoneApplicationAnalysis |
|Запуск без отладки|**CTRL+F5**| Debug.StartWithoutDebugging |
|Шаг с заходом|**F11**| Debug.StepInto |
|Выполнить по шагам текущий процесс|**CTRL+ALT+F11**| Debug.StepIntoCurrentProcess |
|Выполнить по шагам конкретный фрагмент|**SHIFT+ALT+F11**| Debug.StepIntoSpecific |
|Шаг с выходом|**SHIFT+F11**| Debug.StepOut |
|Шаг с выходом для текущего процесса|**CTRL+SHIFT+ALT+F11**| Debug.StepOutCurrentProcess |
|Шаг с обходом|**F10** (при отладке выполняет шаг с обходом)| Debug.StepOver |
|Шаг с обходом|**F10** (если отладка не выполнялась, запускает ее и приостанавливает на первой строке пользовательского кода)| Debug.StepOver |
|Шаг с обходом (текущий процесс)|**CTRL+ALT+F10**| Debug.StepOverCurrentProcess |
|Остановка отладки|**SHIFT+F5**| Debug.StopDebugging |
|Остановить анализ производительности|**SHIFT+ALT+F2**| Debug.StopPerformanceAnalysis |
|Задачи|**CTRL+SHIFT+D, K**| Debug.Tasks |
|Потоки|**CTRL+ALT+H**| Debug.Threads |
|Переключить точку останова|**F9**| Debug.ToggleBreakpoint |
|Переключить дизассемблирование|**CTRL+F11**| Debug.ToggleDisassembly |
|Контрольное значение 1|**CTRL+ALT+W, 1**| Debug.Watch1 |
|Контрольное значение 2|**CTRL+ALT+W, 2**| Debug.Watch2 |
|Контрольное значение 3|**CTRL+ALT+W, 3**| Debug.Watch3 |
|Контрольное значение 4|**CTRL+ALT+W, 4**| Debug.Watch4 |

### <a name="debugger-context-menus"></a><a name="bkmk_debugger"></a> Контекстные меню отладчика

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Удалить|**ALT+F9, D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|Перейти к дизассемблированию|**ALT+F9, A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|Перейти к исходному коду|**ALT+F9, S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub"></a><a name="bkmk_diagnostics"></a> Концентратор диагностики

|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Остановка сбора|**CTRL+ALT+F2**| DiagnosticsHub.StopCollection |

### <a name="edit"></a><a name="bkmk_edit"></a> Правка

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Копировать|**CTRL+C**<br /><br /> or<br /><br /> **CTRL+INS**| Edit.Copy |
|Вырезать|**CTRL+X**<br /><br /> or<br /><br /> **SHIFT+DELETE**| Edit.Cut |
|Зациклить кольцо буфера обмена|**CTRL+SHIFT+V**<br /><br /> or<br /><br /> **CTRL+SHIFT+INS**| Edit.CycleClipboardRing |
|Удалить|**Удалить**| Edit.Delete |
|Дублирование|**CTRL+D**| Edit.Duplicate |
|Поиск|**CTRL+F**| Edit.Find |
|Найти все ссылки|**SHIFT+F12**| Edit.FindAllReferences |
|Поиск в файлах|**CTRL+SHIFT+F**| Edit.FindinFiles |
|Найти далее|**F3**| Edit.FindNext |
|Найти следующий выделенный фрагмент|**CTRL+F3**| Edit.FindNextSelected |
|Найти ранее|**SHIFT+F3**| Edit.FindPrevious |
|Найти предыдущий выделенный фрагмент|**CTRL+SHIFT+F3**| Edit.FindPreviousSelected |
|Создание метода|**CTRL+K, CTRL+M**| Edit.GenerateMethod |
|Перейти|**CTRL+G**| Edit.GoTo |
|Перейти ко всем|**CTRL+,** или **CTRL+T**| Edit.GoToAll |
|Перейти к объявлению|**CTRL+F12**| Edit.GoToDeclaration |
|Перейти к определению|**F12**| Edit.GoToDefinition |
|Перейти к элементу|**CTRL+1, CTRL+M**, **CTRL+1, M** или **ALT+\\**| Edit.GoToMember |
|Перейти к следующему расположению|**F8** (Следующая ошибка в списке ошибок или окне вывода)| Edit.GoToNextLocation |
|Перейти к предыдущему расположению|**SHIFT+F8** (Предыдущая ошибка в списке ошибок или окне вывода)| Edit.GoToPrevLocation |
|Вставить фрагмент|**CTRL+K, CTRL+X**| Edit.InsertSnippet |
|Переместить элемент вниз|**CTRL+СТРЕЛКА ВНИЗ**| Edit.MoveControlDown |
|Переместить элемент вниз по сетке|**СТРЕЛКА ВНИЗ**| Edit.MoveControlDownGrid |
|Переместить элемент влево|**CTRL+СТРЕЛКА ВЛЕВО**| Edit.MoveControlLeft |
|Переместить элемент влево по сетке|**СТРЕЛКА ВЛЕВО**| Edit.MoveControlLeftGrid |
|Переместить элемент вправо|**CTRL+СТРЕЛКА ВПРАВО**| Edit.MoveControlRight |
|Переместить элемент вправо по сетке|**СТРЕЛКА ВПРАВО**| Edit.MoveControlRightGrid |
|Переместить элемент вверх|**CTRL+СТРЕЛКА ВВЕРХ**| Edit.MoveControlUp |
|Переместить элемент вверх по сетке|**СТРЕЛКА ВВЕРХ**| Edit.MoveControlUpGrid |
|Перейти к следующей закладке|**CTRL+K, CTRL+N**| Edit.NextBookmark |
|Следующая закладка в папке|**CTRL+SHIFT+K, CTRL+SHIFT+N**| Edit.NextBookmarkInFolder |
|Открывает файл|**CTRL+SHIFT+G** (Открывается файл, на имя которого наведен курсор)| Edit.OpenFile |
|Вставить|**CTRL+V**<br /><br /> or<br /><br /> **SHIFT+INS**| Edit.Paste |
|Перейти к предыдущей закладке|**CTRL+K, CTRL+P**| Edit.PreviousBookmark |
|Предыдущая закладка в папке|**CTRL+SHIFT+K, CTRL+SHIFT+P**| Edit.PreviousBookmarkInFolder |
|Быстрый поиск символа|**SHIFT+ALT+F12**| Edit.QuickFindSymbol |
|Повторить|**CTRL+Y**<br /><br /> or<br /><br /> **CTRL+SHIFT+Z**<br /><br /> or<br /><br /> **SHIFT+ALT+BACKSPACE**| Edit.Redo |
|Обновить удаленные ссылки|**CTRL+SHIFT+J**| Edit.RefreshRemoteReferences |
|Заменить|**CTRL+H**| Edit.Replace |
|Заменить в файлах|**CTRL+SHIFT+H**| Edit.ReplaceinFiles |
|Выбрать все|**CTRL+A**| Edit.SelectAll |
|Выбрать следующий элемент управления|**TAB**| Edit.SelectNextControl |
|Выбрать предыдущий элемент управления|**SHIFT+TAB**| Edit.SelectPreviousControl |
|Показывать сетку фрагментов|**ВВОД**| Edit.ShowTileGrid |
|Изменить размер элемента управления внизу|**CTRL+SHIFT+СТРЕЛКА ВНИЗ**| Edit.SizeControlDown |
|Изменить размер элемента управления вниз по сетке|**SHIFT+СТРЕЛКА ВНИЗ**| Edit.SizeControlDownGrid |
|Изменить размер элемента управления слева|**CTRL+SHIFT+СТРЕЛКА ВЛЕВО**| Edit.SizeControlLeft |
|Изменить размер элемента управления влево по сетке|**SHIFT+СТРЕЛКА ВЛЕВО**| Edit.SizeControlLeftGrid |
|Изменить размер элемента управления справа|**CTRL+SHIFT+СТРЕЛКА ВПРАВО**| Edit.SizeControlRight |
|Изменить размер элемента управления справа по сетке|**SHIFT+СТРЕЛКА ВПРАВО**| Edit.SizeControlRightGrid |
|Изменить размер элемента управления сверху|**CTRL+SHIFT+СТРЕЛКА ВВЕРХ**| Edit.SizeControlUp |
|Изменить размер элемента управления вверх по сетке|**SHIFT+СТРЕЛКА ВВЕРХ**| Edit.SizeControlUpGrid |
|Остановить поиск|**ALT+F3, S**| Edit.StopSearch |
|Окружить|**CTRL+K, CTRL+S**| Edit.SurroundWith |
|Отменить|**CTRL+Z**<br /><br /> or<br /><br /> **ALT+BACKSPACE**| Edit.Undo |

### <a name="editor-context-menus"></a><a name="bkmk_editorContext"></a> Контекстные меню редактора

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Условия точки останова|**ALT+F9, C**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointConditions |
|Метки изменения точки останова|**ALT+F9, L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|Показать элемент|**CTRL+`**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|Execute|**CTRL+ALT+F5**| EditorContextMenus.CodeWindow.Execute |
|Перейти к представлению|**CTRL+M, CTRL+G**| EditorContextMenus.CodeWindow.GoToView |
|Переключить файл заголовков кода|**CTRL+K, CTRL+O** (латинская буква O)| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|Просмотр иерархии вызовов|**CTRL+K, CTRL+T**<br /><br /> or<br /><br /> **CTRL+K, T**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file"></a><a name="bkmk_file"></a> Файл

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Выход|**ALT+F4**| File.Exit |
|Создание файла|**CTRL+N**| File.NewFile |
|Новый проект|**CTRL+SHIFT+N**| File.NewProject |
|Новый веб-сайт|**SHIFT+ALT+N**| File.NewWebSite |
|Открывает файл|**CTRL+O** (латинская буква O)| File.OpenFile |
|Открытие проекта|**CTRL+SHIFT+O** (латинская буква O)| File.OpenProject |
|Открыть веб-сайт|**SHIFT+ALT+O** (латинская буква O)| File.OpenWebSite |
|Печать|**CTRL+P**| File.Print |
|Сохранить все|**CTRL+SHIFT+S**| File.SaveAll |
|Сохранить выбранные элементы|**CTRL+S**| File.SaveSelectedItems |
|Просмотр в браузере|**CTRL+SHIFT+W**| File.ViewinBrowser |

### <a name="help"></a><a name="bkmk_help"></a> Справка

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Добавить и удалить содержимое справки|**CTRL+ALT+F1**| Help.AddandRemoveHelpContent |
|Справка F1|**F1**| Help.F1Help |
|Посмотреть справку|**CTRL+F1**| Help.ViewHelp |
|Справка окна|**SHIFT+F1**| Help.WindowHelp |

### <a name="load-test"></a><a name="bkmk_loadtest"></a> Нагрузочное тестирование

|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Перейти в область счетчиков|**CTRL+R, Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus"></a><a name="bkmk_otherContext"></a> Другие контекстные меню

|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Добавить новую диаграмму|**Вставить**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project"></a><a name="bkmk_project"></a> Проект

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Добавить существующий элемент|**SHIFT+ALT+A**| Project.AddExistingItem |
|Добавление нового элемента|**CTRL+SHIFT+A**| Project.AddNewItem |
|Мастер классов|**CTRL+SHIFT+X**| Project.ClassWizard |
|Переопределение|**CTRL+ALT+INS**| Project.Override |
|Предварительный просмотр изменений|**ALT+;** затем **ALT+C**| Project.Previewchanges |
|Опубликовать выбранные файлы|**ALT+;** затем **ALT+P**| Project.Publishselectedfiles |
|Заменить выбранные файлы с сервера|**ALT+;** затем **ALT+R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus"></a><a name="bkmk_projectContext"></a> Контекстные меню проекта и решения

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Переместить вниз|**ALT+СТРЕЛКА ВНИЗ**| ProjectandSolutionContextMenus.Item.MoveDown |
|Переместить вверх|**ALT+СТРЕЛКА ВВЕРХ**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor"></a><a name="bkmk_refactor"></a> Рефакторинг

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Инкапсуляция поля|**CTRL+R, CTRL+E**| Refactor.EncapsulateField |
|Извлечение интерфейса|**CTRL+R, CTRL+I**| Refactor.ExtractInterface |
|Извлечение метода|**CTRL+R, CTRL+M**| Refactor.ExtractMethod |
|Удалить параметры|**CTRL+R, CTRL+V**| Refactor.RemoveParameters |
|Переименовать|**CTRL+R, CTRL+R**| Refactor.Rename |
|Упорядочить параметры|**CTRL+R, CTRL+O** (латинская буква O)| Refactor.ReorderParameters |

### <a name="solution-explorer"></a><a name="bkmk_solutionexplorerGLOBAL"></a> Обозреватель решений

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Открыть фильтр файлов|**CTRL+[** , **O** (латинская буква O)<br /><br /> or<br /><br /> **CTRL+[** , **CTRL+O** (латинская буква O)| SolutionExplorer.OpenFilesFilter |
|Фильтр ожидающих изменений|**CTRL+[** , **P**<br /><br /> or<br /><br /> **CTRL+[** , **CTRL+P**| SolutionExplorer.PendingChangesFilter |
|Синхронизировать с активным документом|**CTRL+[** , **S**<br /><br /> or<br /><br /> **CTRL+[** , **CTRL+S**| SolutionExplorer.SyncWithActiveDocument |

### <a name="team"></a><a name="bkmk_team"></a> Команда

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Перейти к веткам Git|**CTRL+0** (ноль), **CTRL+N**<br /><br /> or<br /><br /> **CTRL+0, N**| Team.Git.GoToGitBranches |
|Перейти к изменениям Git|**CTRL+0** (ноль), **CTRL+G**<br /><br /> or<br /><br /> **CTRL+0, G**| Team.Git.GoToGitChanges |
|Перейти к фиксациям Git|**CTRL+0** (ноль), **CTRL+O** (латинская буква O)<br /><br /> or<br /><br /> **CTRL+0, O**| Team.Git.GoToGitCommits |
|Поиск по Team Explorer|**CTRL+'**| Team.TeamExplorerSearch |

### <a name="team-foundation-context-menus"></a><a name="bkmk_TFcontext"></a> Контекстные меню Team Foundation

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Перейти к сборкам|**CTRL+0** (ноль), **CTRL+B**<br /><br /> or<br /><br /> **CTRL+0, B**| TeamFoundationContextMenus.Commands.GoToBuilds |
|Перейти к подключению|**CTRL+0** (ноль), **CTRL+C**<br /><br /> or<br /><br /> **CTRL+0, C**| TeamFoundationContextMenus.Commands.GoToConnect |
|Перейти к документам|**CTRL+0** (ноль), **CTRL+D**<br /><br /> or<br /><br /> **CTRL+0, D**| TeamFoundationContextMenus.Commands.GoToDocuments |
|На главную|**CTRL+0** (ноль), **CTRL+H**<br /><br /> or<br /><br /> **CTRL+0, H**| TeamFoundationContextMenus.Commands.GoToHome |
|К моей работе|**CTRL+0** (ноль), **CTRL+M**<br /><br /> or<br /><br /> **CTRL+0, M**| TeamFoundationContextMenus.Commands.GoToMyWork |
|В ожидающие изменения|**CTRL+0** (ноль), **CTRL+P**<br /><br /> or<br /><br /> **CTRL+0, P**| TeamFoundationContextMenus.Commands.GoToPendingChanges |
|Перейти к отчетам|**CTRL+0** (ноль), **CTRL+R**<br /><br /> or<br /><br /> **CTRL+0, R**| TeamFoundationContextMenus.Commands.GoToReports |
|Открыть параметры|**CTRL+0** (ноль), **CTRL+S**<br /><br /> or<br /><br /> **CTRL+0, S**| TeamFoundationContextMenus.Commands.GoToSettings |
|Перейти к Web Access|**CTRL+0** (ноль), **CTRL+A**<br /><br /> or<br /><br /> **CTRL+0, A**| TeamFoundationContextMenus.Commands.GoToWebAccess |
|Перейти к рабочим элементам|**CTRL+0** (ноль), **CTRL+W**<br /><br /> or<br /><br /> **CTRL+0, W**| TeamFoundationContextMenus.Commands.GoToWorkItems |

### <a name="test"></a><a name="bkmk_test"></a> Тест

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Использовать построитель закодированных тестов пользовательского интерфейса|**CTRL+\\, CTRL+C**| Test.UseCodedUITestBuilder |
|Использовать существующую запись действий|**CTRL+\\, CTRL+A**| Test.UseExistingActionRecording |

### <a name="test-explorer"></a><a name="bkmk_testexplorerGLOBAL"></a> Обозреватель тестов

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Отладить все тесты|**CTRL+R, CTRL+A**| TestExplorer.DebugAllTests |
|Отладить все тесты в контексте|**CTRL+R, CTRL+T**| TestExplorer.DebugAllTestsInContext |
|Отладить последний запуск|**CTRL+R, D**| TestExplorer.DebugLastRun |
|Повторить последний запуск|**CTRL+R, L**| TestExplorer.RepeatLastRun |
|Запустить все тесты|**CTRL+R, A**| TestExplorer.RunAllTests |
|Запустить все тесты в контексте|**CTRL+R, T**| TestExplorer.RunAllTestsInContext |
|Показать обозреватель тестов|**CTRL+E, T**| TestExplorer.ShowTestExplorer |
|Открыть вкладку|**CTRL+E, L**| LiveUnitTesting.OpenTab |
|Результаты покрытия кода|**CTRL+E, C**| Test.CodeCoverageResults |

### <a name="tools"></a><a name="bkmk_tools"></a> Инструменты

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Присоединение к процессу|**CTRL+ALT+P**| Tools.AttachtoProcess |
|Диспетчер фрагментов кода|**CTRL+K, CTRL+B**| Tools.CodeSnippetsManager |
|Принудительная сборка мусора|**CTRL+SHIFT+ALT+F12, CTRL+SHIFT+ALT+F12**| Tools.ForceGC |

### <a name="view"></a><a name="bkmk_view"></a> Вид

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Все окна|**SHIFT+ALT+M**| View.AllWindows |
|Обозреватель архитектуры|**CTRL+\\, CTRL+R**| View.ArchitectureExplorer |
|Назад|**ALT+СТРЕЛКА ВЛЕВО** (Работает не так, как View.NavigateBackward в текстовом редакторе)| View.Backward |
|Окно "Закладки"|**CTRL+K, CTRL+W**| View.BookmarkWindow |
|Далее|**CTRL+SHIFT+1**| View.BrowseNext |
|Назад|**CTRL+SHIFT+2**| View.BrowsePrevious |
|Иерархия вызовов|**CTRL+ALT+K**| View.CallHierarchy |
|Окно классов|**CTRL+SHIFT+C**| View.ClassView |
|Поле со списком для поиска в представлении классов|**CTRL+K, CTRL+V**| View.ClassViewGoToSearchCombo |
|Окно определения кода|**CTRL+\\, D**<br /><br /> or<br /><br /> **CTRL+\\, CTRL+D**| View.CodeDefinitionWindow |
|Командное окно|**CTRL+ALT+A**| View.CommandWindow |
|Источники данных|**SHIFT+ALT+D**| View.DataSources |
|Структура документа|**CTRL+ALT+T**| View.DocumentOutline |
|Изменить метку|**F2**| View.EditLabel |
|Список ошибок|**CTRL+\\, E**<br /><br /> or<br /><br /> **CTRL+\\, CTRL+E**| View.ErrorList |
|F# interactive|**CTRL+ALT+F**| View.F#Interactive |
|Результаты поиска символа|**CTRL+ALT+F12**| View.FindSymbolResults |
|Вперед|**ALT+СТРЕЛКА ВПРАВО** (Работает не так, как View.NavigateForward в текстовом редакторе)| View.Forward |
|Контекст перехода вперед|**CTRL+SHIFT+7**| View.ForwardBrowseContext |
|Во весь экран|**SHIFT+ALT+ВВОД**| View.FullScreen |
|Перейти назад|**CTRL+-**| View.NavigateBackward |
|Перейти вперед|**CTRL+SHIFT+-**| View.NavigateForward |
|Следующая ошибка|**CTRL+SHIFT+F12**| View.NextError |
|Уведомления|**CTRL+W, N**<br /><br /> or<br /><br /> **CTRL+W, CTRL+N**| View.Notifications |
|Обозреватель объектов|**CTRL+ALT+J**| View.ObjectBrowser |
|Поле со списком для поиска в обозревателе объектов|**CTRL+K, CTRL+R**| View.ObjectBrowserGoToSearchCombo |
|Выходные данные|**CTRL+ALT+O** (латинская буква O)| View.Output |
|Отобразить контекст просмотра|**CTRL+SHIFT+8** (Только C++)| View.PopBrowseContext |
|Окно "Свойства"|**F4**| View.PropertiesWindow |
|страницы свойств|**SHIFT+F4**| View.PropertyPages |
|Представление ресурсов|**CTRL+SHIFT+E**| View.ResourceView |
|Обозреватель серверов|**CTRL+ALT+S**| View.ServerExplorer |
|Показать смарт-тег|**SHIFT+ALT+F10**<br /><br /> or<br /><br /> **CTRL+.**| View.ShowSmartTag |
|Обозреватель решений|**CTRL+ALT+L**| View.SolutionExplorer |
|Обозреватель объектов SQL Server|**CTRL+\\, CTRL+S**| View.SQLServerObjectExplorer |
|Список задач|**CTRL+\\, T**<br /><br /> or<br /><br /> **CTRL+\\, CTRL+T**| View.TaskList |
|TFS Team Explorer|**CTRL+\\, CTRL+M**| View.TfsTeamExplorer |
|Панель элементов|**CTRL+ALT+X**| View.Toolbox |
|Обозреватель моделей UML|**CTRL+\\, CTRL+U**| View.UMLModelExplorer |
|Просмотреть код|**F7**| View.ViewCode |
|Конструктор представлений|**SHIFT+F7**| View.ViewDesigner |
|браузер|**CTRL+ALT+R**| View.WebBrowser |
|Увеличение масштаба.|**CTRL+SHIFT+.**| View.ZoomIn |
|Уменьшение масштаба.|**CTRL+SHIFT+,**| View.ZoomOut |
|Показать обозреватель тестов|**CTRL+E, T**| TestExplorer.ShowTestExplorer |

### <a name="window"></a><a name="bkmk_window"></a> Окно

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Активировать окно документа|**ESC**| Window.ActivateDocumentWindow |
|Добавить вкладку в выделенный фрагмент|**CTRL+SHIFT+ALT+ПРОБЕЛ**| Window.AddTabtoSelection |
|Закрыть окно документа|**CTRL+F4**| Window.CloseDocumentWindow |
|Закрыть окно инструментов|**SHIFT+ESC**| Window.CloseToolWindow |
|Не закрывать вкладку|**CTRL+ALT+HOME**| Window.KeepTabOpen |
|Перейти к панели навигации|**CTRL+F2**| Window.MovetoNavigationBar |
|Следующее окно документа|**CTRL+F6**| Window.NextDocumentWindow |
|Следующая панель навигации окна документа|**CTRL+TAB**| Window.NextDocumentWindowNav |
|Следующая область|**ALT+F6**| Window.NextPane |
|Следующая область разделения|**F6**| Window.NextSplitPane |
|Следующая вкладка|**CTRL+ALT+PGDN**<br /><br /> or<br /><br /> **CTRL+PGDN**| Window.NextTab |
|Следующая вкладка и добавление к выделенному фрагменту|**CTRL+SHIFT+ALT+PGDN**| Window.NextTabandAddtoSelection |
|Следующая панель навигации окна инструментов|**ALT+F7**| Window.NextToolWindowNav |
|Предыдущее окно документа|**CTRL+SHIFT+F6**| Window.PreviousDocumentWindow |
|Предыдущая панель навигации окна документа|**CTRL+SHIFT+TAB**| Window.PreviousDocumentWindowNav |
|Предыдущая область|**SHIFT+ALT+F6**| Window.PreviousPane |
|Предыдущая область разделения|**SHIFT+F6**| Window.PreviousSplitPane |
|Предыдущая вкладка|**CTRL+ALT+PGUP**<br /><br /> or<br /><br /> **CTRL+PGUP**| Window.PreviousTab |
|Предыдущая вкладка и добавить к выделенному фрагменту|**CTRL+SHIFT+ALT+PGUP**| Window.PreviousTabandAddtoSelection |
|Предыдущая панель навигации окна инструментов|**SHIFT+ALT+F7**| Window.PreviousToolWindowNav |
|Быстрый запуск|**CTRL+Q**| Window.QuickLaunch |
|Быстрый запуск предыдущей категории|**Ctrl+Shift+Q**| Window.QuickLaunchPreviousCategory |
|Отобразить меню закрепления|**ALT+-**| Window.ShowDockMenu |
|Отобразить список файлов Ex MDI|**CTRL+ALT+СТРЕЛКА ВНИЗ**| Window.ShowEzMDIFileList |
|Искать в обозревателе решений|**CTRL+;**| Window.SolutionExplorerSearch |
|Поиск окна|**ALT+`**| Window.WindowSearch |

### <a name="azure"></a><a name="bkmk_windowsazure"></a> Azure

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Повторить операцию скрипта мобильной службы|**CTRL+NUM \*, CTRL+R**| WindowsAzure.RetryMobileServiceScriptOperation |
|Показать сведения об ошибке скрипта мобильной службы|**CTRL+NUM \*, CTRL+D**| WindowsAzure.ShowMobileServiceScriptErrorDetails |

## <a name="context-specific-shortcuts"></a>Сочетания клавиш, зависящие от контекста


### <a name="adonet-entity-data-model-designer"></a>Конструктор моделей EDM ADO.NET

Ниже приведены сочетания клавиш, относящиеся к этому контексту.

|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Down|**ALT+СТРЕЛКА ВНИЗ**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down |
|Вниз на 5|**ALT+PGDN**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5 |
|Вниз|**ALT+END**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom |
|Наверх|**ALT+HOME**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop |
|Up|**ALT+СТРЕЛКА ВВЕРХ**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up |
|Вверх на 5|**ALT+PGUP**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|Переименовать|**CTRL+R, R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|Удалить из схемы|**SHIFT+DEL**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|Обозреватель модели EDM|**CTRL+1**| View.EntityDataModelBrowser |
|Сведения о сопоставления модели EDM|**CTRL+2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram"></a>Схема классов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Свернуть|**NUM -**| ClassDiagram.Collapse |
|Разверните|**NUM +**| ClassDiagram.Expand |
|Удалить|**CTRL+DEL**| Edit.Delete |
|Развернуть или свернуть список базовых типов|**SHIFT+ALT+B**| Edit.ExpandCollapseBaseTypeList |
|Перейти к интерфейсу без описания операций|**SHIFT+ALT+L**| Edit.NavigateToLollipop |
|Удалить из схемы|**Удалить**| Edit.RemovefromDiagram |
|Просмотреть код|**ВВОД**| View.ViewCode |

### <a name="coded-ui-test-editor"></a>Редактор закодированных тестов пользовательского интерфейса

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Скопировать ссылку в буфер обмена|**CTRL+C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|Вставить задержку перед|**CTRL+ALT+D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|Найти все|**SHIFT+ALT+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|Найти элемент управления пользовательского интерфейса|**CTRL+SHIFT+L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|Перенос кода|**CTRL+ALT+C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|Разделить и поместить в новый метод|**CTRL+SHIFT+T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor"></a>Редактор наборов данных

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Вставить столбец|**Вставить**| OtherContextMenus.ColumnContext.InsertColumn |
|Столбец|**CTRL+L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer"></a>Средство просмотра различий

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Игнорировать обрезку пробелов|**CTRL+\\, CTRL+ПРОБЕЛ**| Diff.IgnoreTrimWhitespace |
|Встроенное представление|**CTRL+\\, CTRL+1**| Diff.InlineView |
|Только представление слева|**CTRL+\\, CTRL+3**| Diff.LeftOnlyView |
|Следующее различие|**F8**| Diff.NextDifference |
|Предыдущее различие|**SHIFT+F8**| Diff.PreviousDifference |
|Только представление справа|**CTRL+\\, CTRL+4**| Diff.RightOnlyView |
|Параллельные представления|**CTRL+\\, CTRL+2**| Diff.SideBySideView |
|Переключиться между левым и правым|**CTRL+\\, CTRL+TAB**| Diff.SwitchBetweenLeftAndRight |
|Синхронизировать переключатель представлений|**CTRL+\\, CTRL+СТРЕЛКА ВНИЗ**| Diff.SynchronizeViewToggle |
|Добавить комментарий|**CTRL+SHIFT+K**| EditorContextMenus.CodeWindow.AddComment |
|Изменить локальный файл|**CTRL+SHIFT+P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer"></a>Обозреватель DOM

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Обновить|**F5**| DOMExplorer.Refresh |
|Выбор элемента|**CTRL+B**| DOMExplorer.SelectElement |
|Показать макет|**CTRL+SHIFT+I**| DOMExplorer.ShowLayout |

### <a name="f-interactive"></a>F# interactive

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Отменить интерактивное вычисление|**CTRL+BREAK**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor"></a>Редактор документов диаграмм

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Добавить узел|**Вставить**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|Оба типа зависимостей|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|Входящие зависимости|**I**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|Исходящие зависимости|**O**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|Создать примечание|**CTRL+SHIFT+K**<br /><br /> or<br /><br /> **CTRL+E, C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|Удалить|**Удалить**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|Переименовать|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics"></a>Диагностика графики

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Захватить кадр|None| Debug.Graphics.CaptureFrame |
|Переместить выбор пикселя вниз|**SHIFT+ALT+СТРЕЛКА ВНИЗ**| Graphics.MovePixelSelectionDown |
|Переместить выбор пикселя влево|**SHIFT+ALT+СТРЕЛКА ВЛЕВО**| Graphics.MovePixelSelectionLeft |
|Переместить выбор пикселя вправо|**SHIFT+ALT+СТРЕЛКА ВПРАВО**| Graphics.MovePixelSelectionRight |
|Переместить выбор пикселя вверх|**SHIFT+ALT+СТРЕЛКА ВВЕРХ**| Graphics.MovePixelSelectionUp |
|Масштабирование до фактического размера|**SHIFT+ALT+0** (ноль)| Graphics.ZoomToActualSize |
|Вписать в окно|**SHIFT+ALT+9**| Graphics.ZoomToFitInWindow |
|Увеличение масштаба.|**SHIFT+ALT+=**| Graphics.ZoomIn |
|Уменьшение масштаба.|**SHIFT+ALT+-**| Graphics.ZoomOut |

### <a name="html-editor"></a>Редактор HTML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Перейти к контроллеру|**CTRL+M, CTRL+G**| OtherContextMenus.HTMLContext.GoToController |

### <a name="html-editor-design-view"></a>Представления конструирования HTML-редактора

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Переместить элемент вниз|**CTRL+СТРЕЛКА ВНИЗ**| Edit.MoveControlDown |
|Переместить элемент вверх|**CTRL+СТРЕЛКА ВВЕРХ**| Edit.MoveControlUp |
|Полужирный|**CTRL+B**| Format.Bold |
|Преобразовать в гиперссылку|**CTRL+L**| Format.ConverttoHyperlink |
|Вставить закладку|**CTRL+SHIFT+L**| Format.InsertBookmark |
|Курсив|**CTRL+I**| Format.Italic |
|Underline|**CTRL+U**| Format.Underline |
|Добавить страницу содержимого|**CTRL+M, CTRL+C**| Project.AddContentPage |
|Столбец влево|**CTRL+ALT+СТРЕЛКА ВЛЕВО**| Table.ColumntotheLeft |
|Столбец вправо|**CTRL+ALT+СТРЕЛКА ВПРАВО**| Table.ColumntotheRight |
|Строка выше|**CTRL+ALT+СТРЕЛКА ВВЕРХ**| Table.RowAbove |
|Строка ниже|**CTRL+ALT+СТРЕЛКА ВНИЗ**| Table.RowBelow |
|Невидимые элементы управления NET|**CTRL+SHIFT+N**| View.ASP.NETNonvisualControls |
|Изменить мастер|**CTRL+M, CTRL+M**| View.EditMaster |
|Следующее представление|**CTRL+PGDN**| View.NextView |
|Показать смарт-тег|**SHIFT+ALT+F10**| View.ShowSmartTag |
|Разметка представления|**SHIFT+F7**| View.ViewMarkup |
|Предыдущая вкладка|**CTRL+PGUP**| Window.PreviousTab |

### <a name="html-editor-source-view"></a>Представление кода HTML-редактора

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Перейти к контроллеру|**CTRL+M, CTRL+G**| OtherContextMenus.HTMLContext.GoToController |
|Следующее представление|**CTRL+PGDN**| View.NextView |
|Синхронизировать представления|**CTRL+SHIFT+Y**| View.SynchronizeViews |
|Конструктор представлений|**SHIFT+F7**| View.ViewDesigner |
|Предыдущая вкладка|**CTRL+PGUP**| Window.PreviousTab |

### <a name="layer-diagram"></a>Схема слоев

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Удалить|**SHIFT+DELETE**| Edit.Delete |

### <a name="managed-resources-editor"></a>Редактор управляемых ресурсов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Изменить ячейку|**F2**| Edit.EditCell |
|Удалить|**Удалить**| Edit.Remove |
|Удаление строки|**CTRL+DELETE**| Edit.RemoveRow |
|Отмена выделения|**ESCAPE**| Edit.SelectionCancel |
|Аудио|**CTRL+4**| Resources.Audio |
|Файлы|**CTRL+5**| Resources.Files |
|Значки|**CTRL+3**| Resources.Icons |
|Изображения|**CTRL+2**| Resources.Images |
|Другое|**CTRL+6**| Resources.Other |
|Строки|**CTRL+1**| Resources.Strings |

### <a name="merge-editor-window"></a>Окно редактора слияния

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Задать фокус на левое окно|**ALT+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|Задать фокус на окно результатов|**ALT+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|Задать фокус на правое окно|**ALT+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare"></a>Средства работы с данными Microsoft SQL Server, сравнение схем

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Сравнение схемы SSDT|**SHIFT+ALT+C**| SQL.SSDTSchemaCompareCompare |
|Создание скрипта сравнения схем SSDT|**SHIFT+ALT+G**| SQL.SSDTSchemaCompareGenerateScript |
|Следующее изменение в сравнении схем SSDT|**SHIFT+ALT+.**| SQL.SSDTSchemaCompareNextChange |
|Предыдущее изменение в сравнении схем SSDT|**SHIFT+ALT+,**| SQL.SSDTSchemaComparePreviousChange |
|Остановка сравнения схем SSDT|**ALT+BREAK**| SQL.SSDTSchemaCompareStop |
|Обновление записи сравнения схем SSDT|**SHIFT+ALT+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer"></a>Средства работы с данными Microsoft SQL Server, конструктор таблиц

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|CommitAllEdits|**SHIFT+ALT+U**|
|Развернуть подстановочные знаки|**CTRL+R, E**<br /><br /> or<br /><br /> **CTRL+R, CTRL+E**| SQL.ExpandWildcards |
|Использовать полные имена|**CTRL+R, Q**<br /><br /> or<br /><br /> **CTRL+R, CTRL+Q**| SQL.FullyqualifyNames |
|Переместить в схему|**CTRL+R, M**<br /><br /> or<br /><br /> **CTRL+R, CTRL+M**| SQL.MovetoSchema |
|Переименовать|**F2**<br /><br /> or<br /><br /> **CTRL+R, R**<br /><br /> or<br /><br /> **CTRL+R, CTRL+R**| SQL.Rename |
|ViewFileInScriptPanel|**SHIFT+ALT+PGDN**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Средства работы с данными Microsoft SQL Server, редактор T-SQL

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|CommitAllEdits|**SHIFT+ALT+U**|
|Выполнить с отладчиком|**ALT+F5**| SQL.ExecuteWithDebugger |
|Развернуть подстановочные знаки|**CTRL+R, E**<br /><br /> or<br /><br /> **CTRL+R, CTRL+E**| SQL.ExpandWildcards |
|Использовать полные имена|**CTRL+R, Q**<br /><br /> or<br /><br /> **CTRL+R, CTRL+Q**| SQL.FullyqualifyNames |
|Переместить в схему|**CTRL+R, M**<br /><br /> or<br /><br /> **CTRL+R, CTRL+M**| SQL.MovetoSchema |
|Переименовать|**F2**<br /><br /> or<br /><br /> **CTRL+R, R**<br /><br /> or<br /><br /> **CTRL+R, CTRL+R**| SQL.Rename |
|Отмена запроса в редакторе T-SQL|**ALT+BREAK**| SQL.TSqlEditorCancelQuery |
|Выполнение запроса в редакторе T-SQL|**CTRL+SHIFT+E**| SQL.TSqlEditorExecuteQuery |
|Результаты редактора T-SQL в виде файла|**CTRL+D, F**| SQL.TSqlEditorResultsAsFile |
|Результаты редактора T-SQL в виде сетки|**CTRL+D, G**| SQL.TSqlEditorResultsAsGrid |
|Результаты редактора T-SQL в виде текста|**CTRL+D, T**| SQL.TSqlEditorResultsAsText |
|Предполагаемый план в редакторе T-SQL|**CTRL+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|Переключение плана выполнения в редакторе T-SQL|**CTRL+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|Переключение области результатов в редакторе T-SQL|**CTRL+D, R**| SQL.TSqlEditorToggleResultsPane |
|Клонирование запроса в редакторе T-SQL|**CTRL+ALT+N**|SQL.TSqlEditorCloneQuery |
|Поле со списком для базы данных редактора T-SQL|**SHIFT+ALT+PGDN**|SQL.TSqlEditorDatabaseCombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Средства работы с данными Microsoft SQL Server, редактор T-SQL PDW

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Отмена запроса в редакторе T-SQL|**ALT+BREAK**| SQL.TSqlEditorCancelQuery |
|Выполнение запроса в редакторе T-SQL|**CTRL+SHIFT+E**| SQL.TSqlEditorExecuteQuery |
|Результаты редактора T-SQL в виде файла|**CTRL+D, F**| SQL.TSqlEditorResultsAsFile |
|Результаты редактора T-SQL в виде сетки|**CTRL+D, G**| SQL.TSqlEditorResultsAsGrid |
|Результаты редактора T-SQL в виде текста|**CTRL+D, T**| SQL.TSqlEditorResultsAsText |
|Предполагаемый план в редакторе T-SQL|**CTRL+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|Переключение плана выполнения в редакторе T-SQL|**CTRL+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|Переключение области результатов в редакторе T-SQL|**CTRL+D, R**| SQL.TSqlEditorToggleResultsPane |
|Клонирование запроса в редакторе T-SQL|**CTRL+ALT+N**|SQL.TSqlEditorCloneQuery |
|Клонирование запроса в редакторе T-SQL|**SHIFT+ALT+PGDN**|SQL.TSqlEditorCloneQuery |

### <a name="page-inspector"></a>Инспектор страниц

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Свернуть|**F12**| PageInspector.Minimize |

### <a name="query-designer"></a>Конструктор запросов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Отмена получения данных|**CTRL+T**| QueryDesigner.CancelRetrievingData |
|Критерии|**CTRL+2**| QueryDesigner.Criteria |
|Схема|**CTRL+1**| QueryDesigner.Diagram |
|Выполнение инструкций SQL|**CTRL+R**| QueryDesigner.ExecuteSQL |
|Перейти к строке|**CTRL+G**| QueryDesigner.GotoRow |
|Режим присоединения|**CTRL+SHIFT+J**| QueryDesigner.JoinMode |
|Результаты|**CTRL+4**| QueryDesigner.Results |
|SQL|**CTRL+3**| QueryDesigner.SQL |

### <a name="query-results"></a>Результаты запроса

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Новая строка результатов запроса|**ALT+END**| SQL.QueryResultsNewRow |
|Обновление результатов запроса|**SHIFT+ALT+R**| SQL.QueryResultsRefresh |
|Остановка результатов запросов|**ALT+BREAK**| SQL.QueryResultsStop |

### <a name="report-designer"></a>Конструктор отчетов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Разрыв строки|**ВВОД**| Edit.BreakLine |
|На один знак влево|**СТРЕЛКА ВЛЕВО**| Edit.CharLeft |
|Выделить знак слева|**SHIFT+СТРЕЛКА ВЛЕВО**| Edit.CharLeftExtend |
|На один знак вправо|**СТРЕЛКА ВПРАВО**| Edit.CharRight |
|Выделить знак справа|**SHIFT+СТРЕЛКА ВПРАВО**| Edit.CharRightExtend |
|Вкладка «Вставить»|**TAB**| Edit.InsertTab |
|На строку вниз|**СТРЕЛКА ВНИЗ**| Edit.LineDown |
|Выделить строку снизу|**SHIFT+СТРЕЛКА ВНИЗ**| Edit.LineDownExtend |
|На строку вверх|**СТРЕЛКА ВВЕРХ**| Edit.LineUp |
|Выделить строку сверху|**SHIFT+СТРЕЛКА ВВЕРХ**| Edit.LineUpExtend |
|Переместить элемент вниз|**CTRL+СТРЕЛКА ВНИЗ**| Edit.MoveControlDown |
|Переместить элемент влево|**CTRL+СТРЕЛКА ВЛЕВО**| Edit.MoveControlLeft |
|Переместить элемент вправо|**CTRL+СТРЕЛКА ВПРАВО**| Edit.MoveControlRight |
|Переместить элемент вверх|**CTRL+СТРЕЛКА ВВЕРХ**| Edit.MoveControlUp |
|Отмена выделения|**ESC**| Edit.SelectionCancel |
|Изменить размер элемента управления внизу|**CTRL+SHIFT+СТРЕЛКА ВНИЗ**| Edit.SizeControlDown |
|Изменить размер элемента управления слева|**CTRL+SHIFT+СТРЕЛКА ВЛЕВО**| Edit.SizeControlLeft |
|Изменить размер элемента управления справа|**CTRL+SHIFT+СТРЕЛКА ВПРАВО**| Edit.SizeControlRight |
|Изменить размер элемента управления сверху|**CTRL+SHIFT+СТРЕЛКА ВВЕРХ**| Edit.SizeControlUp |
|На один знак табуляции влево|**SHIFT+TAB**| Edit.TabLeft |
|данных отчета|**CTRL+ALT+D**| View.ReportData |

### <a name="sequence-diagram"></a>Схема последовательностей

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Перейти к коду|**F12**| ArchitectureDesigner.Sequence.NavigateToCode |
|Удалить|**SHIFT+DEL**| Edit.Delete |

### <a name="settings-designer"></a>Конструктор параметров

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Изменить ячейку|**F2**| Edit.EditCell |
|Удаление строки|**CTRL+DELETE**| Edit.RemoveRow |
|Отмена выделения|**ESC**| Edit.SelectionCancel |
|Просмотреть код|**F7**| View.ViewCode |

### <a name="solution-explorer"></a>обозреватель решений

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Просмотреть в инспекторе страниц|**CTRL+K, CTRL+G**| ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector |

### <a name="team-explorer"></a>Командный обозреватель

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Удалить|**Удалить**| Edit.Delete |
|Переименовать|**F2**| File.Rename |
|Перейти к навигации в Team Explorer|**ALT+HOME**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation |
|Перейти к содержимому следующего раздела в Team Explorer|**ALT+СТРЕЛКА ВНИЗ**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent |
|Перейти к содержимому страниц Team Explorer|**ALT+0** (ноль)| TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent |
|Перейти к содержимому предыдущего раздела в Team Explorer|**ALT+СТРЕЛКА ВВЕРХ**| TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent |
|Перейти к содержимому раздела 1 в Team Explorer|**ALT+1**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content |
|Перейти к содержимому раздела 2 в Team Explorer|**ALT+2**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content |
|Перейти к содержимому раздела 3 в Team Explorer|**ALT+3**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content |
|Перейти к содержимому раздела 4 в Team Explorer|**ALT+4**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content |
|Перейти к содержимому раздела 5 в Team Explorer|**ALT+5**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content |
|Перейти к содержимому раздела 6 в Team Explorer|**ALT+6**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content |
|Перейти к содержимому раздела 7 в Team Explorer|**ALT+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|Перейти к содержимому раздела 8 в Team Explorer|**ALT+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|Перейти к содержимому раздела 9 в Team Explorer|**ALT+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Перейти назад в Team Explorer|**ALT+СТРЕЛКА ВЛЕВО**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Перейти вперед в Team Explorer|**ALT+СТРЕЛКА ВПРАВО**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|Создать копию рабочего элемента на странице моей работы в контексте TFS|**SHIFT+ALT+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|Новый связанный рабочий элемент на странице моей работы в контексте TFS|**SHIFT+ALT+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|Обновить|**F5**| View.Refresh |

### <a name="test-explorer"></a>Обозреватель тестов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Открыть тест|**F12**| TestExplorer.OpenTest |

### <a name="text-editor"></a>Текстовый редактор

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


| Команды | Сочетания клавиш |Идентификатор команды|
|-|-|-|
|Разрыв строки| **ВВОД**<br /><br /> or<br /><br /> **SHIFT+ВВОД** | Edit.BreakLine |
|На один знак влево| **СТРЕЛКА ВЛЕВО** | Edit.CharLeft |
|Выделить знак слева| **SHIFT+СТРЕЛКА ВЛЕВО** | Edit.CharLeftExtend |
|Расширить столбец на знак влево| **SHIFT+ALT+СТРЕЛКА ВЛЕВО** | Edit.CharLeftExtendColumn |
|На один знак вправо| **СТРЕЛКА ВПРАВО** | Edit.CharRight |
|Выделить знак справа| **SHIFT+СТРЕЛКА ВПРАВО** | Edit.CharRightExtend |
|Расширить столбец на знак вправо| **SHIFT+ALT+СТРЕЛКА ВПРАВО** | Edit.CharRightExtendColumn |
|Очистить закладки| **CTRL+K, CTRL+L** | Edit.ClearBookmarks |
|Свернуть все структуры| **CTRL+M, CTRL+A** | Edit.CollapseAllOutlining |
|Свернуть текущий регион| **CTRL+M, CTRL+S** | Edit.CollapseCurrentRegion |
|Свернуть тег| **CTRL+M, CTRL+T** | Edit.CollapseTag |
|Свернуть в определения| **CTRL+M, CTRL+O** (латинская буква O) | Edit.CollapseToDefinitions |
|Свернуть выделение| **SHIFT+ALT+-** | Edit.ContractSelection |
|Закомментировать выделенный фрагмент| **CTRL+K, CTRL+C** | Edit.CommentSelection |
|Дополнить слово| **CTRL+ПРОБЕЛ**<br /><br /> or<br /><br /> **ALT+СТРЕЛКА ВПРАВО** | Edit.CompleteWord |
|Копирование подсказки к параметру| **CTRL+SHIFT+ALT+C** | Edit.CopyParameterTip |
|Уменьшить уровень фильтра| **ALT+,** | Edit.DecreaseFilterLevel |
|Удалить в обратную сторону| **BACKSPACE**<br /><br /> or<br /><br /> **SHIFT+BKSPCE** | Edit.DeleteBackwards |
|Удалить горизонтальный пробел| **CTRL+K, CTRL+\\** | Edit.DeleteHorizontalWhiteSpace |
|Конец документа| **CTRL+END** | Edit.DocumentEnd |
|Выделить до конца документа| **CTRL+SHIFT+END** | Edit.DocumentEndExtend |
|Начало документа| **CTRL+HOME** | Edit.DocumentStart |
|Выделить до начала документа| **CTRL+SHIFT+HOME** | Edit.DocumentStartExtend |
|Развернуть все структуры| **CTRL+M, CTRL+X** | Edit.ExpandAllOutlining |
|Развернуть текущий регион| **CTRL+M, CTRL+E** | Edit.ExpandCurrentRegion |
|Расширение выбора| **SHIFT+ALT+=** | Edit.ExpandSelection |
|Развернуть выделенный фрагмент до содержащего блока| **Shift+Alt+]** | Edit.ExpandSelectiontoContainingBlock |
|Форматировать документ| **CTRL+K, CTRL+D** | Edit.FormatDocument |
|форматирование выделенного фрагмента;| **CTRL+K, CTRL+F** | Edit.FormatSelection |
|Перейти ко всем| **CTRL+T**<br /><br /> or<br /><br /> **CTRL+,** | Edit.GotoAll |
|Перейти к фигурной скобке| **CTRL+]** | Edit.GotoBrace |
|Выделить до скобки| **CTRL+SHIFT+]** | Edit.GotoBraceExtend |
|Перейти к последнему| **CTRL + T, R** | Edit.GotoRecent |
|Перейти к следующей проблеме в файле| **ALT+PGDN** | Edit.GotoNextIssueinFile |
|Перейти к предыдущей проблеме в файле| **ALT+PGUP** | Edit.GotoPreviousIssueinFile |
|Скрытие выделения| **CTRL+M, CTRL+H** | Edit.HideSelection |
|Увеличить уровень фильтра| **ALT+.** | Edit.IncreaseFilterLevel |
|Последовательный поиск| **CTRL+I** | Edit.IncrementalSearch |
|Вставить курсоры для всех совпадений| **SHIFT+ALT+;** | Edit.InsertCaretsatAllMatching |
|Вставить следующий соответствующий курсор| **SHIFT+ALT+.** | Edit.InsertNextMatchingCaret |
|Вкладка «Вставить»| **TAB** | Edit.InsertTab |
|Вырезать строку| **CTRL+L** | Edit.LineCut |
|Удалить строку| **CTRL+SHIFT+L** | Edit.LineDelete |
|На строку вниз| **СТРЕЛКА ВНИЗ** | Edit.LineDown |
|Выделить строку снизу| **SHIFT+СТРЕЛКА ВНИЗ** | Edit.LineDownExtend |
|Выделить строку вниз по столбцу| **SHIFT+ALT+СТРЕЛКА ВНИЗ** | Edit.LineDownExtendColumn |
|Конец строки| **END** | Edit.LineEnd |
|Выделить до конца строки| **SHIFT+END** | Edit.LineEndExtend |
|Выделить до конца строки в столбце| **SHIFT+ALT+END** | Edit.LineEndExtendColumn |
|Открыть строку выше| **CTRL+ВВОД** | Edit.LineOpenAbove |
|Открыть строку ниже| **CTRL+SHIFT+ВВОД** | Edit.LineOpenBelow |
|Начало строки| **Корневая папка** | Edit.LineStart |
|Выделить до начала строки| **SHIFT+HOME** | Edit.LineStartExtend |
|Выделить до начала строки в столбце| **SHIFT+ALT+HOME** | Edit.LineStartExtendColumn |
|Транспонировать строку| **SHIFT+ALT+T** | Edit.LineTranspose |
|На строку вверх| **СТРЕЛКА ВВЕРХ** | Edit.LineUp |
|Выделить строку сверху| **SHIFT+СТРЕЛКА ВВЕРХ** | Edit.LineUpExtend |
|Выделить строку сверху по столбцу| **SHIFT+ALT+СТРЕЛКА ВВЕРХ** | Edit.LineUpExtendColumn |
|Показать список элементов| **CTRL+J** | Edit.ListMembers |
|Все строчные| **CTRL+U** | Edit.MakeLowercase |
|Все прописные| **CTRL+SHIFT+U** | Edit.MakeUppercase |
|Переместить выбранные строки вниз| **ALT+СТРЕЛКА ВНИЗ** | Edit.MoveSelectedLinesDown |
|Переместить выбранные строки вверх| **ALT+СТРЕЛКА ВВЕРХ** | Edit.MoveSelectedLinesUp |
|Следующая выделенная ссылка| **CTRL+SHIFT+СТРЕЛКА ВНИЗ** | Edit.NextHighlightedReference |
|Режим замены| **Вставить** | Edit.OvertypeMode |
|На страницу вниз| **PGDN** | Edit.PageDown |
|Выделить страницу снизу| **SHIFT+PGDN** | Edit.PageDownExtend |
|На страницу вверх| **PGUP** | Edit.PageUp |
|Выделить страницу сверху| **SHIFT+PGUP** | Edit.PageUpExtend |
|Сведения о параметрах| **CTRL+SHIFT+ПРОБЕЛ** | Edit.ParameterInfo |
|Вставка подсказки к параметру| **CTRL+SHIFT+ALT+P** | Edit.PasteParameterTip |
|Просмотр назад| **CTRL+ALT+-** | Edit.PeekBackward |
|Показать определение| **ALT+F12** | Edit.PeekDefinition |
|Просмотр вперед| **CTRL+ALT+=** | Edit.PeekForward |
|Предыдущая выделенная ссылка| **CTRL+SHIFT+СТРЕЛКА ВВЕРХ** | Edit.PreviousHighlightedReference |
|Вывод кратких сведений| **CTRL+K, CTRL+I** | Edit.QuickInfo |
|Обратный последовательный поиск| **CTRL+SHIFT+I** | Edit.ReverseIncrementalSearch |
|Прокрутить на строку вниз| **CTRL+СТРЕЛКА ВНИЗ** | Edit.ScrollLineDown |
|Прокрутить на строку вверх| **CTRL+СТРЕЛКА ВВЕРХ** | Edit.ScrollLineUp |
|Выбрать текущее слово| **CTRL+W** | Edit.SelectCurrentWord |
|Отмена выделения| **ESCAPE** | Edit.SelectionCancel |
|Выбрать до последнего возврата| **CTRL+=** | Edit.SelectToLastGoBack |
|Отобразить меню лупы для кода| **CTRL+K, CTRL+\`** | Edit.ShowCodeLensMenu |
|Отобразить меню навигации| **ALT+\`** | Edit.ShowNavigateMenu |
|Прервать скрытие текущей области| **CTRL+M, CTRL+U** | Edit.StopHidingCurrent |
|Прекратить показ структуры| **CTRL+M, CTRL+P** | Edit.StopOutlining |
|Переставить закрепление| **CTRL+K, CTRL+A** | Edit.SwapAnchor |
|На один знак табуляции влево| **SHIFT+TAB** | Edit.TabLeft |
|Свернуть/развернуть все сегменты| **CTRL+M, CTRL+L** | Edit.ToggleAllOutlining |
|Переключить закладку| **CTRL+K, CTRL+K** | Edit.ToggleBookmark |
|Переключить режим завершения| **CTRL+ALT+ПРОБЕЛ** | Edit.ToggleCompletionMode |
|Свернуть/развернуть сегмент| **CTRL+M, CTRL+M** | Edit.ToggleOutliningExpansion |
|Переключить ярлык списка задач| **CTRL+K, CTRL+H** | Edit.ToggleTaskListShortcut |
|Переключить перенос по словам| **CTRL+E, CTRL+W** | Edit.ToggleWordWrap |
|Раскомментировать выделенный фрагмент| **CTRL+K, CTRL+U** | Edit.UncommentSelection |
|Перейти вниз| **CTRL+PGDN** | Edit.ViewBottom |
|Выделить до конца| **CTRL+SHIFT+PGDN** | Edit.ViewBottomExtend |
|Перейти наверх| **CTRL+PGUP** | Edit.ViewTop |
|Выделить до верхнего края| **CTRL+SHIFT+PGUP** | Edit.ViewTopExtend |
|Показать пробел| **CTRL+R, CTRL+W** | Edit.ViewWhiteSpace |
|Удалить до конца слова| **CTRL+DELETE** | Edit.WordDeleteToEnd |
|Удалить до начала слова| **CTRL+BACKSPACE** | Edit.WordDeleteToStart |
|Следующее слово| **CTRL+СТРЕЛКА ВПРАВО** | Edit.WordNext |
|Выделить следующее слово| **CTRL+SHIFT+СТРЕЛКА ВПРАВО** | Edit.WordNextExtend |
|Выделить следующее слово в столбце| **CTRL+SHIFT+ALT+СТРЕЛКА ВПРАВО** | Edit.WordNextExtendColumn |
|Предыдущее слово| **CTRL+СТРЕЛКА ВЛЕВО** | Edit.WordPrevious |
|Выделить предыдущее слово| **CTRL+SHIFT+СТРЕЛКА ВЛЕВО** | Edit.WordPreviousExtend |
|Выделить предыдущее слово в столбце| **CTRL+SHIFT+ALT+СТРЕЛКА ВЛЕВО** | Edit.WordPreviousExtendColumn |
|Транспонирование слов| **CTRL+SHIFT+T** | Edit.WordTranspose |
|Выполнить в интерактивном режиме| **ALT+ВВОД** | EditorContextMenus.CodeWindow.ExecuteInInteractive |
|Выполнить строку в интерактивном режиме| **ALT+'** | EditorContextMenus.CodeWindow.ExecuteLineInInteractive |
|Просмотреть в инспекторе страниц| **CTRL+K, CTRL+G** | OtherContextMenus.HTMLContext.ViewinPageInspector |
|Следующий регион перемещения заметок TFS| **ALT+PGDN** | TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion |
|Предыдущий регион перемещения заметок TFS| **ALT+PGUP** | TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |

### <a name="uml-activity-diagram"></a>Схема активности UML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Удалить|**SHIFT+DEL**| Edit.Delete |

### <a name="uml-class-diagram"></a>UML-схема классов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Удалить из модели|**SHIFT+DEL**| Edit.DeleteFromModel |

### <a name="uml-component-diagram"></a>Схема компонентов UML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Удалить из модели|**SHIFT+DEL**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram"></a>Схема вариантов использования UML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Удалить из модели|**SHIFT+DEL**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor"></a>Редактор сочетаний клавиш VC

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Новый ускоритель|**Вставить**| Edit.NewAccelerator |
|Следующая введенная клавиша|**CTRL+W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor"></a>Редактор диалоговых окон VC

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Переместить элемент вниз|**СТРЕЛКА ВНИЗ**| Edit.MoveControlDown |
|Переместить элемент влево|**СТРЕЛКА ВЛЕВО**| Edit.MoveControlLeft |
|Переместить элемент вправо|**СТРЕЛКА ВПРАВО**| Edit.MoveControlRight |
|Переместить элемент вверх|**СТРЕЛКА ВВЕРХ**| Edit.MoveControlUp |
|Прокрутить столбец влево|**CTRL+СТРЕЛКА ВЛЕВО**| Edit.ScrollColumnLeft |
|Прокрутить столбец вправо|**CTRL+СТРЕЛКА ВПРАВО**| Edit.ScrollColumnRight |
|Прокрутить на строку вниз|**CTRL+СТРЕЛКА ВНИЗ**| Edit.ScrollLineDown |
|Прокрутить на строку вверх|**CTRL+СТРЕЛКА ВВЕРХ**| Edit.ScrollLineUp |
|Изменить размер элемента управления внизу|**SHIFT+СТРЕЛКА ВНИЗ**| Edit.SizeControlDown |
|Изменить размер элемента управления слева|**SHIFT+СТРЕЛКА ВЛЕВО**| Edit.SizeControlLeft |
|Изменить размер элемента управления справа|**SHIFT+СТРЕЛКА ВПРАВО**| Edit.SizeControlRight |
|Изменить размер элемента управления сверху|**SHIFT+СТРЕЛКА ВВЕРХ**| Edit.SizeControlUp |
|Выравнивание нижних границ|**CTRL+SHIFT+СТРЕЛКА ВНИЗ**| Format.AlignBottoms |
|Выравнивание по центру|**SHIFT+F9**| Format.AlignCenters |
|Выравнивание левых границ|**CTRL+SHIFT+СТРЕЛКА ВЛЕВО**| Format.AlignLefts |
|Выравнивание по середине|**F9**| Format.AlignMiddles |
|Выравнивание правых границ|**CTRL+SHIFT+СТРЕЛКА ВПРАВО**| Format.AlignRights |
|Выравнивание верхних границ|**CTRL+SHIFT+СТРЕЛКА ВВЕРХ**| Format.AlignTops |
|Кнопка внизу|**CTRL+B**| Format.ButtonBottom |
|Кнопка справа|**CTRL+R**| Format.ButtonRight |
|Центрировать по горизонтали|**CTRL+SHIFT+F9**| Format.CenterHorizontal |
|Центрировать по вертикали|**CTRL+F9**| Format.CenterVertical |
|Проверка назначенных клавиш|**CTRL+M**| Format.CheckMnemonics |
|Изменить размер в соответствии с содержимым|**SHIFT+F7**| Format.SizetoContent |
|Смещение по горизонтали|**ALT+СТРЕЛКА ВПРАВО**<br /><br /> or<br /><br /> **ALT+СТРЕЛКА ВЛЕВО**| Format.SpaceAcross |
|Смещение по вертикали|**ALT+СТРЕЛКА ВВЕРХ**<br /><br /> or<br /><br /> **ALT+СТРЕЛКА ВНИЗ**| Format.SpaceDown |
|Последовательность перехода|**CTRL+D**| Format.TabOrder |
|Диалоговое окно тестирования|**CTRL+T**| Format.TestDialog |
|Направляющие|**CTRL+G**| Format.ToggleGuides |

### <a name="vc-image-editor"></a>Редактор изображений VC

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Распылитель|**CTRL+A**| Image.AirbrushTool |
|Кисть|**CTRL+B**| Image.BrushTool |
|Копировать и обвести выделенный фрагмент|**CTRL+SHIFT+U**| Image.CopyandOutlineSelection |
|Непрозрачное рисование|**CTRL+J**| Image.DrawOpaque |
|Инструмент эллипса|**ALT+P**| Image.EllipseTool |
|Инструмент стирания|**CTRL+SHIFT+I**| Image.EraseTool |
|Эллипс с заливкой|**CTRL+SHIFT+ALT+P**| Image.FilledEllipseTool |
|Прямоугольник с заливкой|**CTRL+SHIFT+ALT+R**| Image.FilledRectangleTool |
|Скругленный прямоугольник с заливкой|**CTRL+SHIFT+ALT+W**| Image.FilledRoundedRectangleTool |
|Заполнить - инструмент|**CTRL+F**| Image.FillTool |
|Отразить по горизонтали|**CTRL+H**| Image.FlipHorizontal |
|Отразить по вертикали|**SHIFT+ALT+H**| Image.FlipVertical |
|Крупная кисть|**CTRL+=**| Image.LargerBrush |
|Линия|**CTRL+L**| Image.LineTool |
|Лупа|**CTRL+M**| Image.MagnificationTool |
|Увеличить|**CTRL+SHIFT+M**| Image.Magnify |
|Новый тип изображения|**Вставить**| Image.NewImageType |
|Следующий цвет|**CTRL+]**<br /><br /> or<br /><br /> **CTRL+СТРЕЛКА ВПРАВО**| Image.NextColor |
|Следующий цвет справа|**CTRL+SHIFT+]**<br /><br /> or<br /><br /> **CTRL+SHIFT+СТРЕЛКА ВПРАВО**| Image.NextRightColor |
|Контур эллипса|**SHIFT+ALT+P**| Image.OutlinedEllipseTool |
|Контур прямоугольника|**SHIFT+ALT+R**| Image.OutlinedRectangleTool |
|Контур скругленного прямоугольника|**SHIFT+ALT+W**| Image.OutlinedRoundedRectangleTool |
|Карандаш|**CTRL+I**| Image.PencilTool |
|Предыдущий цвет|**CTRL+[**<br /><br /> or<br /><br /> **CTRL+СТРЕЛКА ВЛЕВО**| Image.PreviousColor |
|Предыдущий цвет справа|**CTRL+SHIFT+[**<br /><br /> or<br /><br /> **CTRL+SHIFT+СТРЕЛКА ВЛЕВО**| Image.PreviousRightColor |
|Выделение прямоугольником|**SHIFT+ALT+S**| Image.RectangleSelectionTool |
|Прямоугольник|**ALT+R**| Image.RectangleTool |
|Повернуть на 90 градусов|**CTRL+SHIFT+H**| Image.Rotate90Degrees |
|Скругленный прямоугольник|**ALT+W**| Image.RoundedRectangleTool |
|Показать сетку|**CTRL+ALT+S**| Image.ShowGrid |
|Показывать сетку фрагментов|**CTRL+SHIFT+ALT+S**| Image.ShowTileGrid |
|Маленькая кисть|**CTRL+.**| Image.SmallBrush |
|Уменьшенная кисть|**CTRL+-**| Image.SmallerBrush |
|Текст|**CTRL+T**| Image.TextTool |
|Использовать выделенный фрагмент в качестве кисти|**CTRL+U**| Image.UseSelectionasBrush |
|Увеличение масштаба.|**CTRL+SHIFT+.**<br /><br /> or<br /><br /> **CTRL+СТРЕЛКА ВВЕРХ**| Image.ZoomIn |
|Уменьшение масштаба.|**CTRL+SHIFT+,**<br /><br /> or<br /><br /> **CTRL+СТРЕЛКА ВНИЗ**| Image.ZoomOut |

### <a name="vc-string-editor"></a>Редактор строк VC

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Новая строка|**Вставить**| Edit.NewString |

### <a name="view-designer"></a>Конструктор представлений

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Отмена получения данных|**CTRL+T**| QueryDesigner.CancelRetrievingData |
|Критерии|**CTRL+2**| QueryDesigner.Criteria |
|Схема|**CTRL+1**| QueryDesigner.Diagram |
|Выполнение инструкций SQL|**CTRL+R**| QueryDesigner.ExecuteSQL |
|Перейти к строке|**CTRL+G**| QueryDesigner.GotoRow |
|Режим присоединения|**CTRL+SHIFT+J**| QueryDesigner.JoinMode |
|Результаты|**CTRL+4**| QueryDesigner.Results |
|SQL|**CTRL+3**| QueryDesigner.SQL |

### <a name="visual-studio"></a>Visual Studio

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|Идентификатор команды|
|-|-|-|
|Скрыть область методов|**CTRL+1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

### <a name="windows-forms-designer"></a>Конструктор Windows Forms

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Разрыв строки|**ВВОД**| Edit.BreakLine |
|На один знак влево|**СТРЕЛКА ВЛЕВО**| Edit.CharLeft |
|Выделить знак слева|**SHIFT+СТРЕЛКА ВЛЕВО**| Edit.CharLeftExtend |
|На один знак вправо|**СТРЕЛКА ВПРАВО**| Edit.CharRight |
|Выделить знак справа|**SHIFT+СТРЕЛКА ВПРАВО**| Edit.CharRightExtend |
|Конец документа|**END**| Edit.DocumentEnd |
|Выделить до конца документа|**SHIFT+END**| Edit.DocumentEndExtend |
|Начало документа|**Корневая папка**| Edit.DocumentStart |
|Выделить до начала документа|**SHIFT+HOME**| Edit.DocumentStartExtend |
|Вкладка «Вставить»|**TAB**| Edit.InsertTab |
|На строку вниз|**СТРЕЛКА ВНИЗ**| Edit.LineDown |
|Выделить строку снизу|**SHIFT+СТРЕЛКА ВВЕРХ**| Edit.LineDownExtend |
|На строку вверх|**СТРЕЛКА ВВЕРХ**| Edit.LineUp |
|Выделить строку сверху|**SHIFT+СТРЕЛКА ВНИЗ**| Edit.LineUpExtend |
|Переместить элемент вниз|**CTRL+СТРЕЛКА ВНИЗ**| Edit.MoveControlDown |
|Переместить элемент влево|**CTRL+СТРЕЛКА ВЛЕВО**| Edit.MoveControlLeft |
|Переместить элемент вправо|**CTRL+СТРЕЛКА ВПРАВО**| Edit.MoveControlRight |
|Переместить элемент вверх|**CTRL+СТРЕЛКА ВВЕРХ**| Edit.MoveControlUp |
|Отмена выделения|**ESCAPE**| Edit.SelectionCancel |
|Изменить размер элемента управления внизу|**CTRL+SHIFT+СТРЕЛКА ВНИЗ**| Edit.SizeControlDown |
|Изменить размер элемента управления слева|**CTRL+SHIFT+СТРЕЛКА ВЛЕВО**| Edit.SizeControlLeft |
|Изменить размер элемента управления справа|**CTRL+SHIFT+СТРЕЛКА ВПРАВО**| Edit.SizeControlRight |
|Изменить размер элемента управления сверху|**CTRL+SHIFT+СТРЕЛКА ВВЕРХ**| Edit.SizeControlUp |
|На один знак табуляции влево|**SHIFT+TAB**| Edit.TabLeft |

### <a name="work-item-editor"></a>Редактор рабочих элементов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Создать копию рабочего элемента|**SHIFT+ALT+C**| Edit.CreateCopyofWorkItem |
|Обновить рабочий элемент|**F5**| Edit.RefreshWorkItem |
|Новый связанный рабочий элемент|**SHIFT+ALT+L**| Team.NewLinkedWorkItem |

### <a name="work-item-query-view"></a>Представление запросов рабочих элементов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Создать копию рабочего элемента|**SHIFT+ALT+C**| Edit.CreateCopyofWorkItem |
|Отступ|**SHIFT+ALT+СТРЕЛКА ВПРАВО**| Edit.Indent |
|Повышение уровня|**SHIFT+ALT+СТРЕЛКА ВЛЕВО**| Edit.Outdent |
|Новый связанный рабочий элемент|**SHIFT+ALT+L**| Team.NewLinkedWorkItem |
|Обновить|**F5**| Team.Refresh |
|Переключение|**SHIFT+ALT+V**| Window.Toggle |

### <a name="work-item-results-view"></a>Представление результатов рабочих элементов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Создать копию рабочего элемента|**SHIFT+ALT+C**| Edit.CreateCopyofWorkItem |
|Отступ|**SHIFT+ALT+СТРЕЛКА ВПРАВО**| Edit.Indent |
|Повышение уровня|**SHIFT+ALT+СТРЕЛКА ВЛЕВО**| Edit.Outdent |
|Переход к следующему рабочему элементу|**SHIFT+ALT+N**| Team.GotoNextWorkItem |
|Переход к предыдущему рабочему элементу|**SHIFT+ALT+P**| Team.GotoPreviousWorkItem |
|Новый связанный рабочий элемент|**SHIFT+ALT+L**| Team.NewLinkedWorkItem |
|Обновить|**F5**| Team.Refresh |
|Переключение|**SHIFT+ALT+V**| Window.Toggle |

### <a name="workflow-designer"></a>Конструктор рабочих процессов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Дополнить слово|**CTRL+K, W**<br /><br /> or<br /><br /> **CTRL+K, CTRL+W**<br /><br /> or<br /><br /> **CTRL+ПРОБЕЛ**<br /><br /> or<br /><br /> **ALT+СТРЕЛКА ВПРАВО**| Edit.CompleteWord |
|Уменьшить уровень фильтра|**ALT+,**| Edit.DecreaseFilterLevel |
|Увеличить уровень фильтра|**ALT+.**| Edit.IncreaseFilterLevel |
|Показать список элементов|**CTRL+K, L**<br /><br /> or<br /><br /> **CTRL+K, CTRL+L**<br /><br /> or<br /><br /> **CTRL+J**| Edit.ListMembers |
|Сведения о параметрах|**CTRL+K, P**<br /><br /> or<br /><br /> **CTRL+K, CTRL+P**<br /><br /> or<br /><br /> **CTRL+SHIFT+ПРОБЕЛ**| Edit.ParameterInfo |
|Вывод кратких сведений|**CTRL+K, I**<br /><br /> or<br /><br /> **CTRL+K, CTRL+I**| Edit.QuickInfo |
|Свернуть|**CTRL+E, CTRL+C**<br /><br /> or<br /><br /> **CTRL+E, C**| WorkflowDesigner.Collapse |
|Свернуть все|или| WorkflowDesigner.CollapseAll |
|Подключить узлы|**CTRL+E, CTRL+F**<br /><br /> or<br /><br /> **CTRL+E, F**| WorkflowDesigner.ConnectNodes |
|Создать переменную|**CTRL+E, CTRL+N**<br /><br /> or<br /><br /> **CTRL+E, N**| WorkflowDesigner.CreateVariable |
|Развернуть все|**CTRL+E, CTRL+X**<br /><br /> or<br /><br /> **CTRL+E, X**| WorkflowDesigner.ExpandAll |
|Развернуть на месте|**CTRL+E, CTRL+E**<br /><br /> or<br /><br /> **CTRL+E, E**| WorkflowDesigner.ExpandInPlace |
|Перейти к родительскому элементу|**CTRL+E, CTRL+P**<br /><br /> or<br /><br /> **CTRL+E, P**| WorkflowDesigner.GoToParent |
|Переместить фокус|**CTRL+E, CTRL+M**<br /><br /> or<br /><br /> **CTRL+E, M**| WorkflowDesigner.MoveFocus |
|Навигация по конструктору|**CTRL+ALT+F6**| WorkflowDesigner.NavigateThroughDesigner |
|Восстановить|**CTRL+E, CTRL+R**<br /><br /> or<br /><br /> **CTRL+E, R**| WorkflowDesigner.Restore |
|Показать/скрыть конструктор аргументов|**CTRL+E, CTRL+A**<br /><br /> or<br /><br /> **CTRL+E, A**| WorkflowDesigner.ShowHideArgumentDesigner |
|Показать/скрыть конструктор импорта|**CTRL+E, CTRL+I**<br /><br /> or<br /><br /> **CTRL+E, I**| WorkflowDesigner.ShowHideImportsDesigner |
|Показать/скрыть карту обзора|**CTRL+E, CTRL+O** (латинская буква O)<br /><br /> or<br /><br /> **CTRL+E, O**| WorkflowDesigner.ShowHideOverviewMap |
|Показать/скрыть конструктор переменных|**CTRL+E, CTRL+V**<br /><br /> or<br /><br /> **CTRL+E, V**| WorkflowDesigner.ShowHideVariableDesigner |
|Выбор или отмена выбора|**CTRL+E, CTRL+S**<br /><br /> or<br /><br /> **CTRL+E, S**| WorkflowDesigner.ToggleSelection |
|Увеличение масштаба.|**CTRL+NUM +**| WorkflowDesigner.ZoomIn |
|Уменьшение масштаба.|**CTRL+NUM -**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer"></a>Конструктор XAML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Вписать все|**CTRL+0** (ноль)| Design.FitAll |
|Показать дескрипторы|**F9**| Design.ShowHandles |
|Увеличение масштаба.|**CTRL+ALT+=**| Design.ZoomIn |
|Уменьшение масштаба.|**CTRL+ALT+-**| Design.ZoomOut |
|Параметры конструктора|**CTRL+SHIFT+;**|
|Редактирование текста|**F2**| Format.EditText |
|Все|**CTRL+SHIFT+R**| Format.ResetLayout.All |
|Выполнить код проекта|**CTRL+F9**|
|Скрыть (только в режиме смешения)|**CTRL+H**| Timeline.Hide (только в режиме смешения) |
|Блокировать (только в режиме смешения)|**CTRL+L**| Timeline.Lock (только в режиме смешения) |
|Показать (только в режиме смешения)|**CTRL+SHIFT+H**| Timeline.Show (только в режиме смешения) |
|Разблокировать (только в режиме смешения)|**CTRL+SHIFT+L**| Timeline.Unlock (только в режиме смешения) |
|Смещение левого края влево|**CTRL+SHIFT+,**| View.EdgeLeftMoveLeft |
|Смещение левого края вправо|**CTRL+SHIFT+.**| View.EdgeLeftMoveRight |
|Смещение правого края влево|**CTRL+SHIFT+ALT+,**| View.EdgeRightMoveLeft |
|Смещение правого края вправо|**CTRL+SHIFT+ALT+.**| View.EdgeRightMoveRight |
|Показывать меню меток свойств|**CTRL+ПРОБЕЛ**| View.ShowPropertyMarkerMenu |

### <a name="xml-text-editor"></a>XML-редактор (текстовый)

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Начать отладку XSLT|**ALT+F5**| XML.StartXSLTDebugging |
|Запустить XSLT без отладки|**CTRL+ALT+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer"></a>Конструктор схемы XML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|Идентификатор команды|
|-|-|-|
|Снизу вверх|**ALT+СТРЕЛКА ВВЕРХ**| GraphView.BottomtoTop |
|Слева направо|**ALT+СТРЕЛКА ВПРАВО**| GraphView.LefttoRight |
|Справа налево|**ALT+СТРЕЛКА ВЛЕВО**| GraphView.RighttoLeft |
|Сверху вниз|**ALT+СТРЕЛКА ВНИЗ**| GraphView.ToptoBottom |
|Удалить из рабочей области|**Удалить**| OtherContextMenus.GraphView.RemovefromWorkspace |
|Показать представление модели содержимого|**CTRL+2**| XsdDesigner.ShowContentModelView |
|Показать представление графика|**CTRL+3**| XsdDesigner.ShowGraphView |
|Показать начальное представление|**CTRL+1**| XsdDesigner.ShowStartView |

## <a name="see-also"></a>См. также

- [Команды Visual Studio](reference/visual-studio-commands.md)
