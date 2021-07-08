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
ms.openlocfilehash: 182102d4de3a2acbec8be82f69650c708817e54c
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222972"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Сочетания клавиш по умолчанию в Visual Studio

Сочетания клавиш позволяют получать доступ к различным [командам](reference/visual-studio-commands.md) и окнам Visual Studio. В этом разделе перечислены сочетания клавиш по умолчанию для команд в профиле **обычных параметров**, который мог быть выбран при установке Visual Studio. Независимо от выбранного профиля сочетание клавиш для той или иной команды можно [определить](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md), открыв диалоговое окно **Параметры**, развернув узел **Среда** и выбрав элемент **Клавиатура**. Кроме того, сочетания клавиш можно настраивать, назначая командам другие сочетания клавиш.

Список распространенных сочетаний клавиш и другие сведения о средствах повышения производительности см. в следующих статьях:

- [Советы по использованию клавиатуры](../ide/productivity-shortcuts.md)
- [Советы по повышению производительности](../ide/productivity-features.md).

Подробные сведения о специальных возможностях в Visual Studio см. в статьях [Советы и рекомендации по специальным возможностям для Visual Studio](../ide/reference/accessibility-tips-and-tricks.md) и [Практическое руководство. Работа только с клавиатуры](../ide/reference/how-to-use-the-keyboard-exclusively.md).

<!---## Printable shortcut cheatsheet

Download and print our Visual Studio shortcut cheatsheet.

[ ![Visual Studio Cheatsheet.](media/default-keyboard-shortcuts-in-visual-studio/visual-studio-shortcut-cheatsheet.png)](media/default-keyboard-shortcuts-in-visual-studio/visual-studio-shortcut-cheatsheet-extended.png#lightbox)
-->
## <a name="most-popular-keyboard-shortcuts"></a>Наиболее популярные сочетания клавиш

Все сочетания клавиш в этом разделе применяются глобально, если не указано иное. *Глобальный* контекст означает, что сочетание применяется в любом окне инструментов в Visual Studio.

> [!NOTE]
> Сочетание клавиш для той или иной команды можно [определить](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md), открыв диалоговое окно **Параметры**, развернув узел **Среда** и выбрав элемент **Клавиатура**.


#### <a name="build-popular-shortcuts"></a>Сборка: популярные сочетания клавиш

|Команды|Сочетания клавиш |
|--------------| - |
|Build.BuildSolution|**CTRL+SHIFT+B** |
|Build.Cancel|**CTRL+BREAK** |
|Build.Compile|**CTRL+F7** |
|Build.RunCodeAnalysisonSolution|**ALT+F11**|

#### <a name="debug-popular-shortcuts"></a>Отладка: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|
|--------------| - |
|Debug.BreakatFunction|**CTRL+B**|
|Debug.BreakAll|**CTRL+ALT+BREAK**|
|Debug.DeleteAllBreakpoints|**CTRL+SHIFT+F9**|
|Debug.Exceptions|**CTRL+ALT+E**|
|Debug.QuickWatch|**CTRL+ALT+Q**<br /><br />или **Shift + F9**|
|Debug.Restart|**CTRL+SHIFT+F5**|
|Debug.RunToCursor|**CTRL+F10**|
|Debug.SetNextStatement|**CTRL+SHIFT+F10**|
|Debug.Start|**F5**|
|Debug.StartWithoutDebugging|**CTRL+F5**|
|Debug.StepInto|**F11**|
|Debug.StepOut|**SHIFT+F11**|
|Debug.StepOver|**F10**|
|Debug.StopDebugging|**SHIFT+F5**|
|Debug.ToggleBreakpoint|**F9**|

#### <a name="edit-popular-shortcuts"></a>Редактирование: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|
|--------------| - |
|Edit.BreakLine|**ВВОД** [текстовый редактор, конструктор отчетов, конструктор Windows Forms]<br /><br />или **SHIFT+ВВОД** [текстовый редактор]|
|Edit.CollapseToDefinitions|**CTRL+M**, **CTRL+O** [текстовый редактор]|
|Edit.CommentSelection|**CTRL+K**, **CTRL+C** [текстовый редактор]|
|Edit.CompleteWord|**ALT+СТРЕЛКА ВПРАВО** [текстовый редактор, конструктор рабочих процессов]<br /><br />или **CTRL+ПРОБЕЛ** [текстовый редактор, конструктор рабочих процессов]<br /><br />или **CTRL+K**, **W** [конструктор рабочих процессов]<br /><br />или **CTRL+K, CTRL+W** [конструктор рабочих процессов]|
|Edit.Copy|**CTRL+C**<br /><br />или **Ctrl + Insert**|
|Edit.Cut|**CTRL+X**<br /><br />или **SHIFT + DELETE**|
|Edit.Delete|**DELETE** [Team Explorer]<br /><br />или **SHIFT+DELETE** [схема последовательностей, схема действий UML, схема слоев]<br /><br />или **CTRL+DELETE** [схема классов]|
|Edit.Find|**CTRL+F**|
|Edit.FindAllReferences|**SHIFT+F12**|
|Edit.FindinFiles|**CTRL+SHIFT+F**|
|Edit.FindNext|**F3**|
|Edit.FindNextSelected|**CTRL+F3**|
|Edit.FormatDocument|**CTRL+K, CTRL+D** [текстовый редактор]|
|Edit.FormatSelection|**CTRL+K, CTRL+F** [текстовый редактор]|
|Edit.GoTo|**CTRL+G**|
|Edit.GoToDeclaration|**CTRL+F12**|
|Edit.GoToDefinition|**F12**|
|Edit.GoToFindCombo|**CTRL+D**|
|Edit.GoToNextLocation|**F8**|
|Edit.InsertSnippet|**Ctrl + K**, **Ctrl + X**|
|Edit.InsertTab|**TAB** [конструктор отчетов, конструктор Windows Forms, текстовый редактор]|
|Edit.LineCut|**CTRL+L** [текстовый редактор]|
|Edit.LineDownExtendColumn|**SHIFT+ALT+СТРЕЛКА ВНИЗ** [текстовый редактор]|
|Edit.LineOpenAbove|**CTRL+ВВОД** [текстовый редактор]|
|Edit.ListMembers|**CTRL+J** [текстовый редактор, конструктор рабочих процессов]<br /><br />или **CTRL+K, CTRL+L** [конструктор рабочих процессов]<br /><br />или **CTRL+K, L** [конструктор рабочих процессов]|
|Edit.NavigateTo|**CTRL+,**|
|Edit.OpenFile|**CTRL+SHIFT+G**|
|Edit.OvertypeMode|**INSERT** [текстовый редактор]|
|Edit.ParameterInfo|**CTRL+SHIFT+ПРОБЕЛ** [текстовый редактор, конструктор рабочих процессов]<br /><br />или **CTRL+K, CTRL+P** [конструктор рабочих процессов]<br /><br />или **CTRL+K, P** [конструктор рабочих процессов]|
|Edit.Paste|**CTRL+V**<br /><br />или **SHIFT + INSERT**|
|Edit.PeekDefinition|**ALT+F12** [текстовый редактор]|
|Edit.Redo|**CTRL+Y**<br /><br />или **SHIFT + ALT + BACKSPACE**<br /><br />или **CTRL + SHIFT + Z**|
|Edit.Replace|**CTRL+H**|
|Edit.SelectAll|**CTRL+A**|
|Edit.SelectCurrentWord|**CTRL+W** [текстовый редактор]|
|Edit.SelectionCancel|**ESC** [текстовый редактор, конструктор отчетов, конструктор параметров, конструктор Windows Forms, редактор управляемых ресурсов]|
|Edit.SurroundWith|**CTRL+K, CTRL+S**|
|Edit.TabLeft|**SHIFT+TAB** [текстовый редактор, конструктор отчетов, конструктор Windows Forms]|
|Edit.ToggleAllOutlining|**CTRL+M, CTRL+L** [текстовый редактор]|
|Edit.ToggleBookmark|**CTRL+K, CTRL+K** [текстовый редактор]|
|Edit.ToggleCompletionMode|**CTRL+ALT+ПРОБЕЛ** [текстовый редактор]|
|Edit.ToggleOutliningExpansion|**CTRL+M, CTRL+M** [текстовый редактор]|
|Edit.UncommentSelection|**CTRL+K, CTRL+U** [текстовый редактор]|
|Edit.Undo|**CTRL+Z**<br /><br />или **ALT + BACKSPACE**|
|Edit.WordDeleteToEnd|**CTRL+DELETE** [текстовый редактор]|
|Edit.WordDeleteToStart|**CTRL+BACKSPACE** [текстовый редактор]|

#### <a name="file-popular-shortcuts"></a>Файл: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|
|--------------| - |
|File.Exit|**ALT+F4**|
|File.NewFile|**CTRL+N**|
|File.NewProject|**CTRL+SHIFT+N**|
|File.NewWebSite|**SHIFT+ALT+N**|
|File.OpenFile|**CTRL+O**|
|File.OpenProject|**CTRL+SHIFT+O**|
|File.OpenWebSite|**Shift+Alt+O**|
|File.Rename|**F2** [Team Explorer]|
|File.SaveAll|**CTRL+SHIFT+S**|
|File.SaveSelectedItems|**CTRL+S**|
|File.ViewinBrowser|**CTRL+SHIFT+W**|

#### <a name="project-popular-shortcuts"></a>Проект: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|
|--------------| - |
|Project.AddExistingItem|**SHIFT+ALT+A**|
|Project.AddNewItem|**CTRL+SHIFT+A**|

#### <a name="refactor-popular-shortcuts"></a>Рефакторинг: популярные сочетания клавиш

|Команда|Сочетание клавиш [специальные контексты]|
|-------------| - |
|Refactor.ExtractMethod|**CTRL+R, CTRL+M**|

#### <a name="tools-popular-shortcuts"></a>Средства: популярные сочетания клавиш

|Команда|Сочетание клавиш [специальные контексты]|
|-------------| - |
|Tools.AttachtoProcess|**CTRL+ALT+P**|

#### <a name="view-popular-shortcuts"></a>Представление: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|
|--------------| - |
|View.ClassView|**CTRL+SHIFT+C**|
|View.EditLabel|**F2**|
|View.ErrorList|**CTRL+\\, CTRL+E**<br /><br />или **CTRL +\\, E**|
|View.NavigateBackward|**CTRL+-**|
|View.NavigateForward|**CTRL+SHIFT+-**|
|View.ObjectBrowser|**CTRL+ALT+J**|
|View.Output|**CTRL+ALT+O**|
|View.PropertiesWindow|**F4**|
|View.Refresh|**F5** [Team Explorer]|
|View.ServerExplorer|**CTRL+ALT+S**|
|View.ShowSmartTag|**CTRL+.**<br /><br />или **SHIFT + ALT + F10** [HTML-редактор в конструкторе]|
|View.SolutionExplorer|**CTRL+ALT+L**|
|View.TfsTeamExplorer|**CTRL+\\, CTRL+M**|
|View.Toolbox|**CTRL+ALT+X**|
|View.ViewCode|**ВВОД** [схема классов]<br /><br />или **F7** [конструктор параметров]|
|View.ViewDesigner|**SHIFT+F7** [HTML-редактор в представлении кода]|

#### <a name="window-popular-shortcuts"></a>Окно: популярные сочетания клавиш

|Команды|Сочетания клавиш [специальные контексты]|
|--------------| - |
|Window.ActivateDocumentWindow|**ESC**|
|Window.CloseDocumentWindow|**CTRL+F4**|
|Window.NextDocumentWindow|**CTRL+F6**|
|Window.NextDocumentWindowNav|**CTRL+TAB**|
|Window.NextSplitPane|**F6**|


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

|Команды|Сочетания клавиш|
|--------------| - |
|Analyze.NavigateBackward|**SHIFT+ALT+3**|
|Analyze.NavigateForward|**SHIFT+ALT+4**|

### <a name="architecture"></a><a name="bkmk_architecture"></a> Архитектура

|Команды|Сочетания клавиш|
|--------------| - |
|Architecture.NewDiagram|**CTRL+\\, CTRL+N**|

### <a name="build"></a><a name="bkmk_build"></a> Сборка

|Команды|Сочетания клавиш|
|--------------| - |
|Build.BuildSelection|**CTRL+B** (Visual Studio 2019)|
|Build.BuildSolution|**CTRL+SHIFT+B**|
|Build.Cancel|**CTRL+BREAK**|
|Build.Compile|**CTRL+F7**|
|Build.RunCodeAnalysisonSolution|**ALT+F11**|

### <a name="class-view-context-menus"></a><a name="bkmk_classview"></a> Контекстные меню представления классов

|Команды|Сочетания клавиш|
|--------------| - |
|ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties|**ALT+ВВОД**|

### <a name="debug"></a><a name="bkmk_debug"></a> Отладка

|Команды|Сочетания клавиш|
|--------------| - |
|Debug.ApplyCodeChanges|**ALT+F10**|
|Debug.AttachtoProcess |**CTRL+ALT+P**|
|Debug.Autos|**CTRL+ALT+V, A**|
|Debug.BreakAll|**CTRL+ALT+BREAK**|
|Debug.Breakpoints|**CTRL+ALT+B**|
|Debug.CallStack|**CTRL+ALT+C**|
|Debug.DeleteAllBreakpoints|**CTRL+SHIFT+F9**|
|Debug.DiagnosticsHub.Launch|**ALT+F2**|
|Debug.Disassembly|**CTRL+ALT+D**|
|Debug.DOMExplorer|**CTRL+ALT+V, D**|
|Debug.EnableBreakpoint|**CTRL+F9**|
|Debug.Exceptions|**CTRL+ALT+E**|
|Debug.FunctionBreakpoint|**CTRL+K, B** (Visual Studio 2019)<br />**CTRL**+**B** (Visual Studio 2017)|
|Debug.GoToPreviousCallorIntelliTraceEvent|**CTRL+SHIFT+F11**|
|Debug.Graphics.StartDiagnostics|**ALT+F5**|
|Debug.Immediate|**CTRL+ALT+I**|
|Debug.IntelliTraceCalls|**CTRL+ALT+Y, T**|
|Debug.IntelliTraceEvents|**CTRL+ALT+Y, F**|
|Debug.JavaScriptConsole|**CTRL+ALT+V, C**|
|Debug.Locals|**CTRL+ALT+V, L**|
|Debug.LocationToolbar.ProcessCombo|**CTRL+5**|
|Debug.LocationToolbar.StackFrameCombo|**CTRL+7**|
|Debug.LocationToolbar.ThreadCombo|**CTRL+6**|
|Debug.LocationToolbar.ToggleCurrentThreadFlaggedState|**CTRL+8**|
|Debug.LocationToolbar.ToggleFlaggedThreads|**CTRL+9**|
|Debug.Memory1|**CTRL+ALT+M, 1**|
|Debug.Memory2|**CTRL+ALT+M, 2**|
|Debug.Memory3|**CTRL+ALT+M, 3**|
|Debug.Memory4|**CTRL+ALT+M, 4**|
|Debug.Modules|**CTRL+ALT+U**|
|Debug.ParallelStacks|**CTRL+SHIFT+D, S**|
|Debug.ParallelWatch1|**CTRL+SHIFT+D, 1**|
|Debug.ParallelWatch2|**CTRL+SHIFT+D, 2**|
|Debug.ParallelWatch3|**CTRL+SHIFT+D, 3**|
|Debug.ParallelWatch4|**CTRL+SHIFT+D, 4**|
|Debug.Processes|**CTRL+ALT+Z**|
|Debug.QuickWatch|**SHIFT+F9** или **CTRL+ALT+Q**|
|Debug.ReattachtoProcess|**SHIFT+ALT+P**|
|Debug.RefreshWindowsapp|**CTRL+SHIFT+R**|
|Debug.Registers|**CTRL+ALT+G**|
|Debug.Restart|**CTRL+SHIFT+F5**|
|Debug.RunToCursor|**CTRL+F10**|
|Debug.SetNextStatement|**CTRL+SHIFT+F10**|
|Debug.ShowCallStackonCodeMap|**CTRL+SHIFT+`**|
|Debug.ShowNextStatement|**ALT+NUM** *|
|Debug.Start|**F5**|
|Debug.StartWindowsPhoneApplicationAnalysis|**ALT+F1**|
|Debug.StartWithoutDebugging|**CTRL+F5**|
|Debug.StepInto|**F11**|
|Debug.StepIntoCurrentProcess|**CTRL+ALT+F11**|
|Debug.StepIntoSpecific|**SHIFT+ALT+F11**|
|Debug.StepOut|**SHIFT+F11**|
|Debug.StepOutCurrentProcess|**CTRL+SHIFT+ALT+F11**|
|Debug.StepOver|**F10** (при отладке выполняет шаг с обходом)|
|Debug.StepOver|**F10** (если отладка не выполнялась, запускает ее и приостанавливает на первой строке пользовательского кода)|
|Debug.StepOverCurrentProcess|**CTRL+ALT+F10**|
|Debug.StopDebugging|**SHIFT+F5**|
|Debug.StopPerformanceAnalysis|**SHIFT+ALT+F2**|
|Debug.Tasks|**CTRL+SHIFT+D, K**|
|Debug.Threads|**CTRL+ALT+H**|
|Debug.ToggleBreakpoint|**F9**|
|Debug.ToggleDisassembly|**CTRL+F11**|
|Debug.Watch1|**CTRL+ALT+W, 1**|
|Debug.Watch2|**CTRL+ALT+W, 2**|
|Debug.Watch3|**CTRL+ALT+W, 3**|
|Debug.Watch4|**CTRL+ALT+W, 4**|

### <a name="debugger-context-menus"></a><a name="bkmk_debugger"></a> Контекстные меню отладчика

|Команды|Сочетания клавиш|
|--------------| - |
|DebuggerContextMenus.BreakpointsWindow.Delete|**ALT+F9, D**|
|DebuggerContextMenus.BreakpointsWindow.GoToDisassembly|**ALT+F9, A**|
|DebuggerContextMenus.BreakpointsWindow.GoToSourceCode|**ALT+F9, S**|

### <a name="diagnostics-hub"></a><a name="bkmk_diagnostics"></a> Концентратор диагностики

|Команда|Сочетание клавиш|
|-------------| - |
|DiagnosticsHub.StopCollection|**CTRL+ALT+F2**|

### <a name="edit"></a><a name="bkmk_edit"></a> Правка

|Команды|Сочетания клавиш|
|--------------|-|
|Edit.Copy|**CTRL+C**<br /><br /> or<br /><br /> **CTRL+INS**|
|Edit.Cut|**CTRL+X**<br /><br /> or<br /><br /> **SHIFT+DELETE**|
|Edit.CycleClipboardRing|**CTRL+SHIFT+V**<br /><br /> or<br /><br /> **CTRL+SHIFT+INS**|
|Edit.Delete|**Удалить**|
|Edit.Duplicate|**CTRL+D**|
|Edit.Find|**CTRL+F**|
|Edit.FindAllReferences|**SHIFT+F12**|
|Edit.FindinFiles|**CTRL+SHIFT+F**|
|Edit.FindNext|**F3**|
|Edit.FindNextSelected|**CTRL+F3**|
|Edit.FindPrevious|**SHIFT+F3**|
|Edit.FindPreviousSelected|**CTRL+SHIFT+F3**|
|Edit.GenerateMethod|**CTRL+K, CTRL+M**|
|Edit.GoTo|**CTRL+G**|
|Edit.GoToAll|**CTRL+,** или **CTRL+T**|
|Edit.GoToDeclaration|**CTRL+F12**|
|Edit.GoToDefinition|**F12**|
|Edit.GoToMember|**CTRL+1, CTRL+M**, **CTRL+1, M** или **ALT+\\**|
|Edit.GoToNextLocation|**F8** (Следующая ошибка в списке ошибок или окне вывода)|
|Edit.GoToPrevLocation|**SHIFT+F8** (Предыдущая ошибка в списке ошибок или окне вывода)|
|Edit.InsertSnippet|**CTRL+K, CTRL+X**|
|Edit.MoveControlDown|**CTRL+СТРЕЛКА ВНИЗ**|
|Edit.MoveControlDownGrid|**СТРЕЛКА ВНИЗ**|
|Edit.MoveControlLeft|**CTRL+СТРЕЛКА ВЛЕВО**|
|Edit.MoveControlLeftGrid|**СТРЕЛКА ВЛЕВО**|
|Edit.MoveControlRight|**CTRL+СТРЕЛКА ВПРАВО**|
|Edit.MoveControlRightGrid|**СТРЕЛКА ВПРАВО**|
|Edit.MoveControlUp|**CTRL+СТРЕЛКА ВВЕРХ**|
|Edit.MoveControlUpGrid|**СТРЕЛКА ВВЕРХ**|
|Edit.NextBookmark|**CTRL+K, CTRL+N**|
|Edit.NextBookmarkInFolder|**CTRL+SHIFT+K, CTRL+SHIFT+N**|
|Edit.OpenFile|**CTRL+SHIFT+G** (Открывается файл, на имя которого наведен курсор)|
|Edit.Paste|**CTRL+V**<br /><br /> or<br /><br /> **SHIFT+INS**|
|Edit.PreviousBookmark|**CTRL+K, CTRL+P**|
|Edit.PreviousBookmarkInFolder|**CTRL+SHIFT+K, CTRL+SHIFT+P**|
|Edit.QuickFindSymbol|**SHIFT+ALT+F12**|
|Edit.Redo|**CTRL+Y**<br /><br /> or<br /><br /> **CTRL+SHIFT+Z**<br /><br /> or<br /><br /> **SHIFT+ALT+BACKSPACE**|
|Edit.RefreshRemoteReferences|**CTRL+SHIFT+J**|
|Edit.Replace|**CTRL+H**|
|Edit.ReplaceinFiles|**CTRL+SHIFT+H**|
|Edit.SelectAll|**CTRL+A**|
|Edit.SelectNextControl|**TAB**|
|Edit.SelectPreviousControl|**SHIFT+TAB**|
|Edit.ShowTileGrid|**ВВОД**|
|Edit.SizeControlDown|**CTRL+SHIFT+СТРЕЛКА ВНИЗ**|
|Edit.SizeControlDownGrid|**SHIFT+СТРЕЛКА ВНИЗ**|
|Edit.SizeControlLeft|**CTRL+SHIFT+СТРЕЛКА ВЛЕВО**|
|Edit.SizeControlLeftGrid|**SHIFT+СТРЕЛКА ВЛЕВО**|
|Edit.SizeControlRight|**CTRL+SHIFT+СТРЕЛКА ВПРАВО**|
|Edit.SizeControlRightGrid|**SHIFT+СТРЕЛКА ВПРАВО**|
|Edit.SizeControlUp|**CTRL+SHIFT+СТРЕЛКА ВВЕРХ**|
|Edit.SizeControlUpGrid|**SHIFT+СТРЕЛКА ВВЕРХ**|
|Edit.StopSearch|**ALT+F3, S**|
|Edit.SurroundWith|**CTRL+K, CTRL+S**|
|Edit.Undo|**CTRL+Z**<br /><br /> or<br /><br /> **ALT+BACKSPACE**|

### <a name="editor-context-menus"></a><a name="bkmk_editorContext"></a> Контекстные меню редактора

|Команды|Сочетания клавиш|
|--------------| - |
|EditorContextMenus.CodeWindow.Breakpoint.BreakpointConditions|**ALT+F9, C**|
|EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels|**ALT+F9, L**|
|EditorContextMenus.CodeWindow.CodeMap.ShowItem|**CTRL+`**|
|EditorContextMenus.CodeWindow.Execute|**CTRL+ALT+F5**|
|EditorContextMenus.CodeWindow.GoToView|**CTRL+M, CTRL+G**|
|EditorContextMenus.CodeWindow.ToggleHeaderCodeFile|**CTRL+K, CTRL+O** (латинская буква O)|
|EditorContextMenus.CodeWindow.ViewCallHierarchy|**CTRL+K, CTRL+T**<br /><br /> or<br /><br /> **CTRL+K, T**|

### <a name="file"></a><a name="bkmk_file"></a> Файл

|Команды|Сочетания клавиш|
|--------------| - |
|File.Exit|**ALT+F4**|
|File.NewFile|**CTRL+N**|
|File.NewProject|**CTRL+SHIFT+N**|
|File.NewWebSite|**SHIFT+ALT+N**|
|File.OpenFile|**CTRL+O** (латинская буква O)|
|File.OpenProject|**CTRL+SHIFT+O** (латинская буква O)|
|File.OpenWebSite|**SHIFT+ALT+O** (латинская буква O)|
|File.Print|**CTRL+P**|
|File.SaveAll|**CTRL+SHIFT+S**|
|File.SaveSelectedItems|**CTRL+S**|
|File.ViewinBrowser|**CTRL+SHIFT+W**|

### <a name="help"></a><a name="bkmk_help"></a> Справка

|Команды|Сочетания клавиш|
|--------------| - |
|Help.AddandRemoveHelpContent|**CTRL+ALT+F1**|
|Help.F1Help|**F1**|
|Help.ViewHelp|**CTRL+F1**|
|Help.WindowHelp|**SHIFT+F1**|

### <a name="load-test"></a><a name="bkmk_loadtest"></a> Нагрузочное тестирование

|Команда|Сочетание клавиш|
|-------------| - |
|LoadTest.JumpToCounterPane|**CTRL+R, Q**|

### <a name="other-context-menus"></a><a name="bkmk_otherContext"></a> Другие контекстные меню

|Команда|Сочетание клавиш|
|-------------| - |
|OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram|**Вставить**|

### <a name="project"></a><a name="bkmk_project"></a> Проект

|Команды|Сочетания клавиш|
|--------------| - |
|Project.AddExistingItem|**SHIFT+ALT+A**|
|Project.AddNewItem|**CTRL+SHIFT+A**|
|Project.ClassWizard|**CTRL+SHIFT+X**|
|Project.Override|**CTRL+ALT+INS**|
|Project.Previewchanges|**ALT+;** затем **ALT+C**|
|Project.Publishselectedfiles|**ALT+;** затем **ALT+P**|
|Project.Replaceselectedfilesfromserver|**ALT+;** затем **ALT+R**|

### <a name="project-and-solution-context-menus"></a><a name="bkmk_projectContext"></a> Контекстные меню проекта и решения

|Команды|Сочетания клавиш|
|--------------| - |
|ProjectandSolutionContextMenus.Item.MoveDown|**ALT+СТРЕЛКА ВНИЗ**|
|ProjectandSolutionContextMenus.Item.MoveUp|**ALT+СТРЕЛКА ВВЕРХ**|

### <a name="refactor"></a><a name="bkmk_refactor"></a> Рефакторинг

|Команды|Сочетания клавиш|
|--------------| - |
|Refactor.EncapsulateField|**CTRL+R, CTRL+E**|
|Refactor.ExtractInterface|**CTRL+R, CTRL+I**|
|Refactor.ExtractMethod|**CTRL+R, CTRL+M**|
|Refactor.RemoveParameters|**CTRL+R, CTRL+V**|
|Refactor.Rename|**CTRL+R, CTRL+R**|
|Refactor.ReorderParameters|**CTRL+R, CTRL+O** (латинская буква O)|

### <a name="solution-explorer"></a><a name="bkmk_solutionexplorerGLOBAL"></a> Обозреватель решений

|Команды|Сочетания клавиш|
|--------------| - |
|SolutionExplorer.OpenFilesFilter|**CTRL+[** , **O** (латинская буква O)<br /><br /> or<br /><br /> **CTRL+[** , **CTRL+O** (латинская буква O)|
|SolutionExplorer.PendingChangesFilter|**CTRL+[** , **P**<br /><br /> or<br /><br /> **CTRL+[** , **CTRL+P**|
|SolutionExplorer.SyncWithActiveDocument|**CTRL+[** , **S**<br /><br /> or<br /><br /> **CTRL+[** , **CTRL+S**|

### <a name="team"></a><a name="bkmk_team"></a> Команда

|Команды|Сочетания клавиш|
|--------------| - |
|Team.Git.GoToGitBranches|**CTRL+0** (ноль), **CTRL+N**<br /><br /> or<br /><br /> **CTRL+0, N**|
|Team.Git.GoToGitChanges|**CTRL+0** (ноль), **CTRL+G**<br /><br /> or<br /><br /> **CTRL+0, G**|
|Team.Git.GoToGitCommits|**CTRL+0** (ноль), **CTRL+O** (латинская буква O)<br /><br /> or<br /><br /> **CTRL+0, O**|
|Team.TeamExplorerSearch|**CTRL+'**|

### <a name="team-foundation-context-menus"></a><a name="bkmk_TFcontext"></a> Контекстные меню Team Foundation

|Команды|Сочетания клавиш|
|--------------| - |
|TeamFoundationContextMenus.Commands.GoToBuilds|**CTRL+0** (ноль), **CTRL+B**<br /><br /> or<br /><br /> **CTRL+0, B**|
|TeamFoundationContextMenus.Commands.GoToConnect|**CTRL+0** (ноль), **CTRL+C**<br /><br /> or<br /><br /> **CTRL+0, C**|
|TeamFoundationContextMenus.Commands.GoToDocuments|**CTRL+0** (ноль), **CTRL+D**<br /><br /> or<br /><br /> **CTRL+0, D**|
|TeamFoundationContextMenus.Commands.GoToHome|**CTRL+0** (ноль), **CTRL+H**<br /><br /> or<br /><br /> **CTRL+0, H**|
|TeamFoundationContextMenus.Commands.GoToMyWork|**CTRL+0** (ноль), **CTRL+M**<br /><br /> or<br /><br /> **CTRL+0, M**|
|TeamFoundationContextMenus.Commands.GoToPendingChanges|**CTRL+0** (ноль), **CTRL+P**<br /><br /> or<br /><br /> **CTRL+0, P**|
|TeamFoundationContextMenus.Commands.GoToReports|**CTRL+0** (ноль), **CTRL+R**<br /><br /> or<br /><br /> **CTRL+0, R**|
|TeamFoundationContextMenus.Commands.GoToSettings|**CTRL+0** (ноль), **CTRL+S**<br /><br /> or<br /><br /> **CTRL+0, S**|
|TeamFoundationContextMenus.Commands.GoToWebAccess|**CTRL+0** (ноль), **CTRL+A**<br /><br /> or<br /><br /> **CTRL+0, A**|
|TeamFoundationContextMenus.Commands.GoToWorkItems|**CTRL+0** (ноль), **CTRL+W**<br /><br /> or<br /><br /> **CTRL+0, W**|

### <a name="test"></a><a name="bkmk_test"></a> Тест

|Команды|Сочетания клавиш|
|--------------| - |
|Test.UseCodedUITestBuilder|**CTRL+\\, CTRL+C**|
|Test.UseExistingActionRecording|**CTRL+\\, CTRL+A**|

### <a name="test-explorer"></a><a name="bkmk_testexplorerGLOBAL"></a> Обозреватель тестов

|Команды|Сочетания клавиш|
|--------------| - |
|TestExplorer.DebugAllTests|**CTRL+R, CTRL+A**|
|TestExplorer.DebugAllTestsInContext|**CTRL+R, CTRL+T**|
|TestExplorer.DebugLastRun|**CTRL+R, D**|
|TestExplorer.RepeatLastRun|**CTRL+R, L**|
|TestExplorer.RunAllTests|**CTRL+R, A**|
|TestExplorer.RunAllTestsInContext|**CTRL+R, T**|
|TestExplorer.ShowTestExplorer|**CTRL+E, T**|
|LiveUnitTesting.OpenTab|**CTRL+E, L**|
|Test.CodeCoverageResults|**CTRL+E, C**|

### <a name="tools"></a><a name="bkmk_tools"></a> Инструменты

|Команды|Сочетания клавиш|
|--------------| - |
|Tools.AttachtoProcess|**CTRL+ALT+P**|
|Tools.CodeSnippetsManager|**CTRL+K, CTRL+B**|
|Tools.ForceGC|**CTRL+SHIFT+ALT+F12, CTRL+SHIFT+ALT+F12**|

### <a name="view"></a><a name="bkmk_view"></a> Вид

|Команды|Сочетания клавиш|
|--------------| - |
|View.AllWindows|**SHIFT+ALT+M**|
|View.ArchitectureExplorer|**CTRL+\\, CTRL+R**|
|View.Backward|**ALT+СТРЕЛКА ВЛЕВО** (Работает не так, как View.NavigateBackward в текстовом редакторе)|
|View.BookmarkWindow|**CTRL+K, CTRL+W**|
|View.BrowseNext|**CTRL+SHIFT+1**|
|View.BrowsePrevious|**CTRL+SHIFT+2**|
|View.CallHierarchy|**CTRL+ALT+K**|
|View.ClassView|**CTRL+SHIFT+C**|
|View.ClassViewGoToSearchCombo|**CTRL+K, CTRL+V**|
|View.CodeDefinitionWindow|**CTRL+\\, D**<br /><br /> or<br /><br /> **CTRL+\\, CTRL+D**|
|View.CommandWindow|**CTRL+ALT+A**|
|View.DataSources|**SHIFT+ALT+D**|
|View.DocumentOutline|**CTRL+ALT+T**|
|View.EditLabel|**F2**|
|View.ErrorList|**CTRL+\\, E**<br /><br /> or<br /><br /> **CTRL+\\, CTRL+E**|
|View.F#Interactive|**CTRL+ALT+F**|
|View.FindSymbolResults|**CTRL+ALT+F12**|
|View.Forward|**ALT+СТРЕЛКА ВПРАВО** (Работает не так, как View.NavigateForward в текстовом редакторе)|
|View.ForwardBrowseContext|**CTRL+SHIFT+7**|
|View.FullScreen|**SHIFT+ALT+ВВОД**|
|View.NavigateBackward|**CTRL+-**|
|View.NavigateForward|**CTRL+SHIFT+-**|
|View.NextError|**CTRL+SHIFT+F12**|
|View.Notifications|**CTRL+W, N**<br /><br /> or<br /><br /> **CTRL+W, CTRL+N**|
|View.ObjectBrowser|**CTRL+ALT+J**|
|View.ObjectBrowserGoToSearchCombo|**CTRL+K, CTRL+R**|
|View.Output|**CTRL+ALT+O** (латинская буква O)|
|View.PopBrowseContext|**CTRL+SHIFT+8** (Только C++)|
|View.PropertiesWindow|**F4**|
|View.PropertyPages|**SHIFT+F4**|
|View.ResourceView|**CTRL+SHIFT+E**|
|View.ServerExplorer|**CTRL+ALT+S**|
|View.ShowSmartTag|**SHIFT+ALT+F10**<br /><br /> or<br /><br /> **CTRL+.**|
|View.SolutionExplorer|**CTRL+ALT+L**|
|View.SQLServerObjectExplorer|**CTRL+\\, CTRL+S**|
|View.TaskList|**CTRL+\\, T**<br /><br /> or<br /><br /> **CTRL+\\, CTRL+T**|
|View.TfsTeamExplorer|**CTRL+\\, CTRL+M**|
|View.Toolbox|**CTRL+ALT+X**|
|View.UMLModelExplorer|**CTRL+\\, CTRL+U**|
|View.ViewCode|**F7**|
|View.ViewDesigner|**SHIFT+F7**|
|View.WebBrowser|**CTRL+ALT+R**|
|View.ZoomIn|**CTRL+SHIFT+.**|
|View.ZoomOut|**CTRL+SHIFT+,**|
|TestExplorer.ShowTestExplorer|**CTRL+E, T**|

### <a name="window"></a><a name="bkmk_window"></a> Окно

|Команды|Сочетания клавиш|
|--------------| - |
|Window.ActivateDocumentWindow|**ESC**|
|Window.AddTabtoSelection|**CTRL+SHIFT+ALT+ПРОБЕЛ**|
|Window.CloseDocumentWindow|**CTRL+F4**|
|Window.CloseToolWindow|**SHIFT+ESC**|
|Window.KeepTabOpen|**CTRL+ALT+HOME**|
|Window.MovetoNavigationBar|**CTRL+F2**|
|Window.NextDocumentWindow|**CTRL+F6**|
|Window.NextDocumentWindowNav|**CTRL+TAB**|
|Window.NextPane|**ALT+F6**|
|Window.NextSplitPane|**F6**|
|Window.NextTab|**CTRL+ALT+PGDN**<br /><br /> or<br /><br /> **CTRL+PGDN**|
|Window.NextTabandAddtoSelection|**CTRL+SHIFT+ALT+PGDN**|
|Window.NextToolWindowNav|**ALT+F7**|
|Window.PreviousDocumentWindow|**CTRL+SHIFT+F6**|
|Window.PreviousDocumentWindowNav|**CTRL+SHIFT+TAB**|
|Window.PreviousPane|**SHIFT+ALT+F6**|
|Window.PreviousSplitPane|**SHIFT+F6**|
|Window.PreviousTab|**CTRL+ALT+PGUP**<br /><br /> or<br /><br /> **CTRL+PGUP**|
|Window.PreviousTabandAddtoSelection|**CTRL+SHIFT+ALT+PGUP**|
|Window.PreviousToolWindowNav|**SHIFT+ALT+F7**|
|Window.QuickLaunch|**CTRL+Q**|
|Window.QuickLaunchPreviousCategory|**Ctrl+Shift+Q**|
|Window.ShowDockMenu|**ALT+-**|
|Window.ShowEzMDIFileList|**CTRL+ALT+СТРЕЛКА ВНИЗ**|
|Window.SolutionExplorerSearch|**CTRL+;**|
|Window.WindowSearch|**ALT+`**|

### <a name="azure"></a><a name="bkmk_windowsazure"></a> Azure

|Команды|Сочетания клавиш|
|--------------| - |
|WindowsAzure.RetryMobileServiceScriptOperation|**CTRL+NUM \*, CTRL+R**|
|WindowsAzure.ShowMobileServiceScriptErrorDetails|**CTRL+NUM \*, CTRL+D**|

## <a name="context-specific-shortcuts"></a>Сочетания клавиш, зависящие от контекста


### <a name="adonet-entity-data-model-designer"></a>Конструктор моделей EDM ADO.NET

Ниже приведены сочетания клавиш, относящиеся к этому контексту.

|Команды|Сочетания клавиш|
|--------------| - |
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down|**ALT+СТРЕЛКА ВНИЗ**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5|**ALT+PGDN**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom|**ALT+END**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop|**ALT+HOME**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up|**ALT+СТРЕЛКА ВВЕРХ**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5|**ALT+PGUP**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename|**CTRL+R, R**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram|**SHIFT+DEL**|
|View.EntityDataModelBrowser|**CTRL+1**|
|View.EntityDataModelMappingDetails|**CTRL+2**|

### <a name="class-diagram"></a>Схема классов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|ClassDiagram.Collapse|**NUM -**|
|ClassDiagram.Expand|**NUM +**|
|Edit.Delete|**CTRL+DEL**|
|Edit.ExpandCollapseBaseTypeList|**SHIFT+ALT+B**|
|Edit.NavigateToLollipop|**SHIFT+ALT+L**|
|Edit.RemovefromDiagram|**Удалить**|
|View.ViewCode|**ВВОД**|

### <a name="coded-ui-test-editor"></a>Редактор закодированных тестов пользовательского интерфейса

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard|**CTRL+C**|
|OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore|**CTRL+ALT+D**|
|OtherContextMenus.UITestEditorContextMenu.LocateAll|**SHIFT+ALT+L**|
|OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl|**CTRL+SHIFT+L**|
|OtherContextMenus.UITestEditorContextMenu.Movecode|**CTRL+ALT+C**|
|OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod|**CTRL+SHIFT+T**|

### <a name="dataset-editor"></a>Редактор наборов данных

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|OtherContextMenus.ColumnContext.InsertColumn|**Вставить**|
|OtherContextMenus.DbTableContext.Add.Column|**CTRL+L**|

### <a name="difference-viewer"></a>Средство просмотра различий

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Diff.IgnoreTrimWhitespace|**CTRL+\\, CTRL+ПРОБЕЛ**|
|Diff.InlineView|**CTRL+\\, CTRL+1**|
|Diff.LeftOnlyView|**CTRL+\\, CTRL+3**|
|Diff.NextDifference|**F8**|
|Diff.PreviousDifference|**SHIFT+F8**|
|Diff.RightOnlyView|**CTRL+\\, CTRL+4**|
|Diff.SideBySideView|**CTRL+\\, CTRL+2**|
|Diff.SwitchBetweenLeftAndRight|**CTRL+\\, CTRL+TAB**|
|Diff.SynchronizeViewToggle|**CTRL+\\, CTRL+СТРЕЛКА ВНИЗ**|
|EditorContextMenus.CodeWindow.AddComment|**CTRL+SHIFT+K**|
|EditorContextMenus.CodeWindow.EditLocalFile|**CTRL+SHIFT+P**|

### <a name="dom-explorer"></a>Обозреватель DOM

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|DOMExplorer.Refresh|**F5**|
|DOMExplorer.SelectElement|**CTRL+B**|
|DOMExplorer.ShowLayout|**CTRL+SHIFT+I**|

### <a name="f-interactive"></a>F# interactive

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation|**CTRL+BREAK**|

### <a name="graph-document-editor"></a>Редактор документов диаграмм

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode|**Вставить**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies|**B**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies|**I**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies|**O**|
|ArchitectureContextMenus.DirectedGraphContextMenu.NewComment|**CTRL+SHIFT+K**<br /><br /> or<br /><br /> **CTRL+E, C**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Remove|**Удалить**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Rename|**F2**|

### <a name="graphics-diagnostics"></a>Диагностика графики

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Debug.Graphics.CaptureFrame|Отсутствуют|
|Graphics.MovePixelSelectionDown|**SHIFT+ALT+СТРЕЛКА ВНИЗ**|
|Graphics.MovePixelSelectionLeft|**SHIFT+ALT+СТРЕЛКА ВЛЕВО**|
|Graphics.MovePixelSelectionRight|**SHIFT+ALT+СТРЕЛКА ВПРАВО**|
|Graphics.MovePixelSelectionUp|**SHIFT+ALT+СТРЕЛКА ВВЕРХ**|
|Graphics.ZoomToActualSize|**SHIFT+ALT+0** (ноль)|
|Graphics.ZoomToFitInWindow|**SHIFT+ALT+9**|
|Graphics.ZoomIn|**SHIFT+ALT+=**|
|Graphics.ZoomOut|**SHIFT+ALT+-**|

### <a name="html-editor"></a>Редактор HTML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|OtherContextMenus.HTMLContext.GoToController|**CTRL+M, CTRL+G**|

### <a name="html-editor-design-view"></a>Представления конструирования HTML-редактора

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.MoveControlDown|**CTRL+СТРЕЛКА ВНИЗ**|
|Edit.MoveControlUp|**CTRL+СТРЕЛКА ВВЕРХ**|
|Format.Bold|**CTRL+B**|
|Format.ConverttoHyperlink|**CTRL+L**|
|Format.InsertBookmark|**CTRL+SHIFT+L**|
|Format.Italic|**CTRL+I**|
|Format.Underline|**CTRL+U**|
|Project.AddContentPage|**CTRL+M, CTRL+C**|
|Table.ColumntotheLeft|**CTRL+ALT+СТРЕЛКА ВЛЕВО**|
|Table.ColumntotheRight|**CTRL+ALT+СТРЕЛКА ВПРАВО**|
|Table.RowAbove|**CTRL+ALT+СТРЕЛКА ВВЕРХ**|
|Table.RowBelow|**CTRL+ALT+СТРЕЛКА ВНИЗ**|
|View.ASP.NETNonvisualControls|**CTRL+SHIFT+N**|
|View.EditMaster|**CTRL+M, CTRL+M**|
|View.NextView|**CTRL+PGDN**|
|View.ShowSmartTag|**SHIFT+ALT+F10**|
|View.ViewMarkup|**SHIFT+F7**|
|Window.PreviousTab|**CTRL+PGUP**|

### <a name="html-editor-source-view"></a>Представление кода HTML-редактора

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|OtherContextMenus.HTMLContext.GoToController|**CTRL+M, CTRL+G**|
|View.NextView|**CTRL+PGDN**|
|View.SynchronizeViews|**CTRL+SHIFT+Y**|
|View.ViewDesigner|**SHIFT+F7**|
|Window.PreviousTab|**CTRL+PGUP**|

### <a name="layer-diagram"></a>Схема слоев

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|Edit.Delete|**SHIFT+DELETE**|

### <a name="managed-resources-editor"></a>Редактор управляемых ресурсов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.EditCell|**F2**|
|Edit.Remove|**Удалить**|
|Edit.RemoveRow|**CTRL+DELETE**|
|Edit.SelectionCancel|**ESCAPE**|
|Resources.Audio|**CTRL+4**|
|Resources.Files|**CTRL+5**|
|Resources.Icons|**CTRL+3**|
|Resources.Images|**CTRL+2**|
|Resources.Other|**CTRL+6**|
|Resources.Strings|**CTRL+1**|

### <a name="merge-editor-window"></a>Окно редактора слияния

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow|**ALT+1**|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow|**ALT+2**|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow|**ALT+3**|

### <a name="microsoft-sql-server-data-tools-schema-compare"></a>Средства работы с данными Microsoft SQL Server, сравнение схем

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|SQL.SSDTSchemaCompareCompare|**SHIFT+ALT+C**|
|SQL.SSDTSchemaCompareGenerateScript|**SHIFT+ALT+G**|
|SQL.SSDTSchemaCompareNextChange|**SHIFT+ALT+.**|
|SQL.SSDTSchemaComparePreviousChange|**SHIFT+ALT+,**|
|SQL.SSDTSchemaCompareStop|**ALT+BREAK**|
|SQL.SSDTSchemaCompareWriteUpdates|**SHIFT+ALT+U**|

### <a name="microsoft-sql-server-data-tools-table-designer"></a>Средства работы с данными Microsoft SQL Server, конструктор таблиц

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|CommitAllEdits|**SHIFT+ALT+U**|
|SQL.ExpandWildcards|**CTRL+R, E**<br /><br /> or<br /><br /> **CTRL+R, CTRL+E**|
|SQL.FullyqualifyNames|**CTRL+R, Q**<br /><br /> or<br /><br /> **CTRL+R, CTRL+Q**|
|SQL.MovetoSchema|**CTRL+R, M**<br /><br /> or<br /><br /> **CTRL+R, CTRL+M**|
|SQL.Rename|**F2**<br /><br /> or<br /><br /> **CTRL+R, R**<br /><br /> or<br /><br /> **CTRL+R, CTRL+R**|
|ViewFileInScriptPanel|**SHIFT+ALT+PGDN**|

### <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Средства работы с данными Microsoft SQL Server, редактор T-SQL

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|CommitAllEdits|**SHIFT+ALT+U**|
|SQL.ExecuteWithDebugger|**ALT+F5**|
|SQL.ExpandWildcards|**CTRL+R, E**<br /><br /> or<br /><br /> **CTRL+R, CTRL+E**|
|SQL.FullyqualifyNames|**CTRL+R, Q**<br /><br /> or<br /><br /> **CTRL+R, CTRL+Q**|
|SQL.MovetoSchema|**CTRL+R, M**<br /><br /> or<br /><br /> **CTRL+R, CTRL+M**|
|SQL.Rename|**F2**<br /><br /> or<br /><br /> **CTRL+R, R**<br /><br /> or<br /><br /> **CTRL+R, CTRL+R**|
|SQL.TSqlEditorCancelQuery|**ALT+BREAK**|
|SQL.TSqlEditorExecuteQuery|**CTRL+SHIFT+E**|
|SQL.TSqlEditorResultsAsFile|**CTRL+D, F**|
|SQL.TSqlEditorResultsAsGrid|**CTRL+D, G**|
|SQL.TSqlEditorResultsAsText|**CTRL+D, T**|
|SQL.TSqlEditorShowEstimatedPlan|**CTRL+D, E**|
|SQL.TSqlEditorToggleExecutionPlan|**CTRL+D, A**|
|SQL.TSqlEditorToggleResultsPane|**CTRL+D, R**|
|TSqlEditorCloneQuery|**CTRL+ALT+N**|
|TSqlEditorDatabaseCombo|**SHIFT+ALT+PGDN**|

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Средства работы с данными Microsoft SQL Server, редактор T-SQL PDW

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|SQL.TSqlEditorCancelQuery|**ALT+BREAK**|
|SQL.TSqlEditorExecuteQuery|**CTRL+SHIFT+E**|
|SQL.TSqlEditorResultsAsFile|**CTRL+D, F**|
|SQL.TSqlEditorResultsAsGrid|**CTRL+D, G**|
|SQL.TSqlEditorResultsAsText|**CTRL+D, T**|
|SQL.TSqlEditorShowEstimatedPlan|**CTRL+D, E**|
|SQL.TSqlEditorToggleExecutionPlan|**CTRL+D, A**|
|SQL.TSqlEditorToggleResultsPane|**CTRL+D, R**|
|TSqlEditorCloneQuery|**CTRL+ALT+N**|
|TSqlEditorDatabaseCombo|**SHIFT+ALT+PGDN**|

### <a name="page-inspector"></a>Инспектор страниц

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|PageInspector.Minimize|**F12**|

### <a name="query-designer"></a>Конструктор запросов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|QueryDesigner.CancelRetrievingData|**CTRL+T**|
|QueryDesigner.Criteria|**CTRL+2**|
|QueryDesigner.Diagram|**CTRL+1**|
|QueryDesigner.ExecuteSQL|**CTRL+R**|
|QueryDesigner.GotoRow|**CTRL+G**|
|QueryDesigner.JoinMode|**CTRL+SHIFT+J**|
|QueryDesigner.Results|**CTRL+4**|
|QueryDesigner.SQL|**CTRL+3**|

### <a name="query-results"></a>Результаты запроса

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|SQL.QueryResultsNewRow|**ALT+END**|
|SQL.QueryResultsRefresh|**SHIFT+ALT+R**|
|SQL.QueryResultsStop|**ALT+BREAK**|

### <a name="report-designer"></a>Конструктор отчетов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.BreakLine|**ВВОД**|
|Edit.CharLeft|**СТРЕЛКА ВЛЕВО**|
|Edit.CharLeftExtend|**SHIFT+СТРЕЛКА ВЛЕВО**|
|Edit.CharRight|**СТРЕЛКА ВПРАВО**|
|Edit.CharRightExtend|**SHIFT+СТРЕЛКА ВПРАВО**|
|Edit.InsertTab|**TAB**|
|Edit.LineDown|**СТРЕЛКА ВНИЗ**|
|Edit.LineDownExtend|**SHIFT+СТРЕЛКА ВНИЗ**|
|Edit.LineUp|**СТРЕЛКА ВВЕРХ**|
|Edit.LineUpExtend|**SHIFT+СТРЕЛКА ВВЕРХ**|
|Edit.MoveControlDown|**CTRL+СТРЕЛКА ВНИЗ**|
|Edit.MoveControlLeft|**CTRL+СТРЕЛКА ВЛЕВО**|
|Edit.MoveControlRight|**CTRL+СТРЕЛКА ВПРАВО**|
|Edit.MoveControlUp|**CTRL+СТРЕЛКА ВВЕРХ**|
|Edit.SelectionCancel|**ESC**|
|Edit.SizeControlDown|**CTRL+SHIFT+СТРЕЛКА ВНИЗ**|
|Edit.SizeControlLeft|**CTRL+SHIFT+СТРЕЛКА ВЛЕВО**|
|Edit.SizeControlRight|**CTRL+SHIFT+СТРЕЛКА ВПРАВО**|
|Edit.SizeControlUp|**CTRL+SHIFT+СТРЕЛКА ВВЕРХ**|
|Edit.TabLeft|**SHIFT+TAB**|
|View.ReportData|**CTRL+ALT+D**|

### <a name="sequence-diagram"></a>Схема последовательностей

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|ArchitectureDesigner.Sequence.NavigateToCode|**F12**|
|Edit.Delete|**SHIFT+DEL**|

### <a name="settings-designer"></a>Конструктор параметров

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.EditCell|**F2**|
|Edit.RemoveRow|**CTRL+DELETE**|
|Edit.SelectionCancel|**ESC**|
|View.ViewCode|**F7**|

### <a name="solution-explorer"></a>обозреватель решений

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector|**CTRL+K, CTRL+G**|

### <a name="team-explorer"></a>Командный обозреватель

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|Edit.Delete|**Удалить**|
|File.Rename|**F2**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation|**ALT+HOME**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent|**ALT+СТРЕЛКА ВНИЗ**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent|**ALT+0** (ноль)|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent|**ALT+СТРЕЛКА ВВЕРХ**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content|**ALT+1**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content|**ALT+2**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content|**ALT+3**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content|**ALT+4**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content|**ALT+5**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content|**ALT+6**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content|**ALT+7**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content|**ALT+8**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content|**ALT+9**|
|TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward|**ALT+СТРЕЛКА ВЛЕВО**|
|TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward|**ALT+СТРЕЛКА ВПРАВО**|
|TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI|**SHIFT+ALT+C**|
|TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI|**SHIFT+ALT+L**|
|View.Refresh|**F5**|

### <a name="test-explorer"></a>Обозреватель тестов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|TestExplorer.OpenTest|**F12**|

### <a name="text-editor"></a>Текстовый редактор

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


| Команды | Сочетания клавиш |
| - | - |
| Edit.BreakLine | **ВВОД**<br /><br /> or<br /><br /> **SHIFT+ВВОД** |
| Edit.CharLeft | **СТРЕЛКА ВЛЕВО** |
| Edit.CharLeftExtend | **SHIFT+СТРЕЛКА ВЛЕВО** |
| Edit.CharLeftExtendColumn | **SHIFT+ALT+СТРЕЛКА ВЛЕВО** |
| Edit.CharRight | **СТРЕЛКА ВПРАВО** |
| Edit.CharRightExtend | **SHIFT+СТРЕЛКА ВПРАВО** |
| Edit.CharRightExtendColumn | **SHIFT+ALT+СТРЕЛКА ВПРАВО** |
| Edit.ClearBookmarks | **CTRL+K, CTRL+L** |
| Edit.CollapseAllOutlining | **CTRL+M, CTRL+A** |
| Edit.CollapseCurrentRegion | **CTRL+M, CTRL+S** |
| Edit.CollapseTag | **CTRL+M, CTRL+T** |
| Edit.CollapseToDefinitions | **CTRL+M, CTRL+O** (латинская буква O) |
| Edit.ContractSelection | **SHIFT+ALT+-** |
| Edit.CommentSelection | **CTRL+K, CTRL+C** |
| Edit.CompleteWord | **CTRL+ПРОБЕЛ**<br /><br /> or<br /><br /> **ALT+СТРЕЛКА ВПРАВО** |
| Edit.CopyParameterTip | **CTRL+SHIFT+ALT+C** |
| Edit.DecreaseFilterLevel | **ALT+,** |
| Edit.DeleteBackwards | **BACKSPACE**<br /><br /> or<br /><br /> **SHIFT+BKSPCE** |
| Edit.DeleteHorizontalWhiteSpace | **CTRL+K, CTRL+\\** |
| Edit.DocumentEnd | **CTRL+END** |
| Edit.DocumentEndExtend | **CTRL+SHIFT+END** |
| Edit.DocumentStart | **CTRL+HOME** |
| Edit.DocumentStartExtend | **CTRL+SHIFT+HOME** |
| Edit.ExpandAllOutlining | **CTRL+M, CTRL+X** |
| Edit.ExpandCurrentRegion | **CTRL+M, CTRL+E** |
| Edit.ExpandSelection | **SHIFT+ALT+=** |
| Edit.ExpandSelectiontoContainingBlock | **Shift+Alt+]** |
| Edit.FormatDocument | **CTRL+K, CTRL+D** |
| Edit.FormatSelection | **CTRL+K, CTRL+F** |
| Edit.GotoAll | **CTRL+T**<br /><br /> or<br /><br /> **CTRL+,** |
| Edit.GotoBrace | **CTRL+]** |
| Edit.GotoBraceExtend | **CTRL+SHIFT+]** |
| Edit.GotoRecent | **CTRL + T, R** |
| Edit.GotoNextIssueinFile | **ALT+PGDN** |
| Edit.GotoPreviousIssueinFile | **ALT+PGUP** |
| Edit.HideSelection | **CTRL+M, CTRL+H** |
| Edit.IncreaseFilterLevel | **ALT+.** |
| Edit.IncrementalSearch | **CTRL+I** |
| Edit.InsertCaretsatAllMatching | **SHIFT+ALT+;** |
| Edit.InsertNextMatchingCaret | **SHIFT+ALT+.** |
| Edit.InsertTab | **TAB** |
| Edit.LineCut | **CTRL+L** |
| Edit.LineDelete | **CTRL+SHIFT+L** |
| Edit.LineDown | **СТРЕЛКА ВНИЗ** |
| Edit.LineDownExtend | **SHIFT+СТРЕЛКА ВНИЗ** |
| Edit.LineDownExtendColumn | **SHIFT+ALT+СТРЕЛКА ВНИЗ** |
| Edit.LineEnd | **END** |
| Edit.LineEndExtend | **SHIFT+END** |
| Edit.LineEndExtendColumn | **SHIFT+ALT+END** |
| Edit.LineOpenAbove | **CTRL+ВВОД** |
| Edit.LineOpenBelow | **CTRL+SHIFT+ВВОД** |
| Edit.LineStart | **Корневая папка** |
| Edit.LineStartExtend | **SHIFT+HOME** |
| Edit.LineStartExtendColumn | **SHIFT+ALT+HOME** |
| Edit.LineTranspose | **SHIFT+ALT+T** |
| Edit.LineUp | **СТРЕЛКА ВВЕРХ** |
| Edit.LineUpExtend | **SHIFT+СТРЕЛКА ВВЕРХ** |
| Edit.LineUpExtendColumn | **SHIFT+ALT+СТРЕЛКА ВВЕРХ** |
| Edit.ListMembers | **CTRL+J** |
| Edit.MakeLowercase | **CTRL+U** |
| Edit.MakeUppercase | **CTRL+SHIFT+U** |
| Edit.MoveSelectedLinesDown | **ALT+СТРЕЛКА ВНИЗ** |
| Edit.MoveSelectedLinesUp | **ALT+СТРЕЛКА ВВЕРХ** |
| Edit.NextHighlightedReference | **CTRL+SHIFT+СТРЕЛКА ВНИЗ** |
| Edit.OvertypeMode | **Вставить** |
| Edit.PageDown | **PGDN** |
| Edit.PageDownExtend | **SHIFT+PGDN** |
| Edit.PageUp | **PGUP** |
| Edit.PageUpExtend | **SHIFT+PGUP** |
| Edit.ParameterInfo | **CTRL+SHIFT+ПРОБЕЛ** |
| Edit.PasteParameterTip | **CTRL+SHIFT+ALT+P** |
| Edit.PeekBackward | **CTRL+ALT+-** |
| Edit.PeekDefinition | **ALT+F12** |
| Edit.PeekForward | **CTRL+ALT+=** |
| Edit.PreviousHighlightedReference | **CTRL+SHIFT+СТРЕЛКА ВВЕРХ** |
| Edit.QuickInfo | **CTRL+K, CTRL+I** |
| Edit.ReverseIncrementalSearch | **CTRL+SHIFT+I** |
| Edit.ScrollLineDown | **CTRL+СТРЕЛКА ВНИЗ** |
| Edit.ScrollLineUp | **CTRL+СТРЕЛКА ВВЕРХ** |
| Edit.SelectCurrentWord | **CTRL+W** |
| Edit.SelectionCancel | **ESCAPE** |
| Edit.SelectToLastGoBack | **CTRL+=** |
| Edit.ShowCodeLensMenu | **CTRL+K, CTRL+\`** |
| Edit.ShowNavigateMenu | **ALT+\`** |
| Edit.StopHidingCurrent | **CTRL+M, CTRL+U** |
| Edit.StopOutlining | **CTRL+M, CTRL+P** |
| Edit.SwapAnchor | **CTRL+K, CTRL+A** |
| Edit.TabLeft | **SHIFT+TAB** |
| Edit.ToggleAllOutlining | **CTRL+M, CTRL+L** |
| Edit.ToggleBookmark | **CTRL+K, CTRL+K** |
| Edit.ToggleCompletionMode | **CTRL+ALT+ПРОБЕЛ** |
| Edit.ToggleOutliningExpansion | **CTRL+M, CTRL+M** |
| Edit.ToggleTaskListShortcut | **CTRL+K, CTRL+H** |
| Edit.ToggleWordWrap | **CTRL+E, CTRL+W** |
| Edit.UncommentSelection | **CTRL+K, CTRL+U** |
| Edit.ViewBottom | **CTRL+PGDN** |
| Edit.ViewBottomExtend | **CTRL+SHIFT+PGDN** |
| Edit.ViewTop | **CTRL+PGUP** |
| Edit.ViewTopExtend | **CTRL+SHIFT+PGUP** |
| Edit.ViewWhiteSpace | **CTRL+R, CTRL+W** |
| Edit.WordDeleteToEnd | **CTRL+DELETE** |
| Edit.WordDeleteToStart | **CTRL+BACKSPACE** |
| Edit.WordNext | **CTRL+СТРЕЛКА ВПРАВО** |
| Edit.WordNextExtend | **CTRL+SHIFT+СТРЕЛКА ВПРАВО** |
| Edit.WordNextExtendColumn | **CTRL+SHIFT+ALT+СТРЕЛКА ВПРАВО** |
| Edit.WordPrevious | **CTRL+СТРЕЛКА ВЛЕВО** |
| Edit.WordPreviousExtend | **CTRL+SHIFT+СТРЕЛКА ВЛЕВО** |
| Edit.WordPreviousExtendColumn | **CTRL+SHIFT+ALT+СТРЕЛКА ВЛЕВО** |
| Edit.WordTranspose | **CTRL+SHIFT+T** |
| EditorContextMenus.CodeWindow.ExecuteInInteractive | **ALT+ВВОД** |
| EditorContextMenus.CodeWindow.ExecuteLineInInteractive | **ALT+'** |
| OtherContextMenus.HTMLContext.ViewinPageInspector | **CTRL+K, CTRL+G** |
| TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion | **ALT+PGDN** |
| TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion | **ALT+PGUP** |

### <a name="uml-activity-diagram"></a>Схема активности UML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|Edit.Delete|**SHIFT+DEL**|

### <a name="uml-class-diagram"></a>UML-схема классов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|Edit.DeleteFromModel|**SHIFT+DEL**|

### <a name="uml-component-diagram"></a>Схема компонентов UML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|Edit.DeleteFromModel|**SHIFT+DEL**|

### <a name="uml-use-case-diagram"></a>Схема вариантов использования UML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|Edit.DeleteFromModel|**SHIFT+DEL**|

### <a name="vc-accelerator-editor"></a>Редактор сочетаний клавиш VC

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.NewAccelerator|**Вставить**|
|Edit.NextKeyTyped|**CTRL+W**|

### <a name="vc-dialog-editor"></a>Редактор диалоговых окон VC

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.MoveControlDown|**СТРЕЛКА ВНИЗ**|
|Edit.MoveControlLeft|**СТРЕЛКА ВЛЕВО**|
|Edit.MoveControlRight|**СТРЕЛКА ВПРАВО**|
|Edit.MoveControlUp|**СТРЕЛКА ВВЕРХ**|
|Edit.ScrollColumnLeft|**CTRL+СТРЕЛКА ВЛЕВО**|
|Edit.ScrollColumnRight|**CTRL+СТРЕЛКА ВПРАВО**|
|Edit.ScrollLineDown|**CTRL+СТРЕЛКА ВНИЗ**|
|Edit.ScrollLineUp|**CTRL+СТРЕЛКА ВВЕРХ**|
|Edit.SizeControlDown|**SHIFT+СТРЕЛКА ВНИЗ**|
|Edit.SizeControlLeft|**SHIFT+СТРЕЛКА ВЛЕВО**|
|Edit.SizeControlRight|**SHIFT+СТРЕЛКА ВПРАВО**|
|Edit.SizeControlUp|**SHIFT+СТРЕЛКА ВВЕРХ**|
|Format.AlignBottoms|**CTRL+SHIFT+СТРЕЛКА ВНИЗ**|
|Format.AlignCenters|**SHIFT+F9**|
|Format.AlignLefts|**CTRL+SHIFT+СТРЕЛКА ВЛЕВО**|
|Format.AlignMiddles|**F9**|
|Format.AlignRights|**CTRL+SHIFT+СТРЕЛКА ВПРАВО**|
|Format.AlignTops|**CTRL+SHIFT+СТРЕЛКА ВВЕРХ**|
|Format.ButtonBottom|**CTRL+B**|
|Format.ButtonRight|**CTRL+R**|
|Format.CenterHorizontal|**CTRL+SHIFT+F9**|
|Format.CenterVertical|**CTRL+F9**|
|Format.CheckMnemonics|**CTRL+M**|
|Format.SizetoContent|**SHIFT+F7**|
|Format.SpaceAcross|**ALT+СТРЕЛКА ВПРАВО**<br /><br /> or<br /><br /> **ALT+СТРЕЛКА ВЛЕВО**|
|Format.SpaceDown|**ALT+СТРЕЛКА ВВЕРХ**<br /><br /> or<br /><br /> **ALT+СТРЕЛКА ВНИЗ**|
|Format.TabOrder|**CTRL+D**|
|Format.TestDialog|**CTRL+T**|
|Format.ToggleGuides|**CTRL+G**|

### <a name="vc-image-editor"></a>Редактор изображений VC

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Image.AirbrushTool|**CTRL+A**|
|Image.BrushTool|**CTRL+B**|
|Image.CopyandOutlineSelection|**CTRL+SHIFT+U**|
|Image.DrawOpaque|**CTRL+J**|
|Image.EllipseTool|**ALT+P**|
|Image.EraseTool|**CTRL+SHIFT+I**|
|Image.FilledEllipseTool|**CTRL+SHIFT+ALT+P**|
|Image.FilledRectangleTool|**CTRL+SHIFT+ALT+R**|
|Image.FilledRoundedRectangleTool|**CTRL+SHIFT+ALT+W**|
|Image.FillTool|**CTRL+F**|
|Image.FlipHorizontal|**CTRL+H**|
|Image.FlipVertical|**SHIFT+ALT+H**|
|Image.LargerBrush|**CTRL+=**|
|Image.LineTool|**CTRL+L**|
|Image.MagnificationTool|**CTRL+M**|
|Image.Magnify|**CTRL+SHIFT+M**|
|Image.NewImageType|**Вставить**|
|Image.NextColor|**CTRL+]**<br /><br /> or<br /><br /> **CTRL+СТРЕЛКА ВПРАВО**|
|Image.NextRightColor|**CTRL+SHIFT+]**<br /><br /> or<br /><br /> **CTRL+SHIFT+СТРЕЛКА ВПРАВО**|
|Image.OutlinedEllipseTool|**SHIFT+ALT+P**|
|Image.OutlinedRectangleTool|**SHIFT+ALT+R**|
|Image.OutlinedRoundedRectangleTool|**SHIFT+ALT+W**|
|Image.PencilTool|**CTRL+I**|
|Image.PreviousColor|**CTRL+[**<br /><br /> or<br /><br /> **CTRL+СТРЕЛКА ВЛЕВО**|
|Image.PreviousRightColor|**CTRL+SHIFT+[**<br /><br /> or<br /><br /> **CTRL+SHIFT+СТРЕЛКА ВЛЕВО**|
|Image.RectangleSelectionTool|**SHIFT+ALT+S**|
|Image.RectangleTool|**ALT+R**|
|Image.Rotate90Degrees|**CTRL+SHIFT+H**|
|Image.RoundedRectangleTool|**ALT+W**|
|Image.ShowGrid|**CTRL+ALT+S**|
|Image.ShowTileGrid|**CTRL+SHIFT+ALT+S**|
|Image.SmallBrush|**CTRL+.**|
|Image.SmallerBrush|**CTRL+-**|
|Image.TextTool|**CTRL+T**|
|Image.UseSelectionasBrush|**CTRL+U**|
|Image.ZoomIn|**CTRL+SHIFT+.**<br /><br /> or<br /><br /> **CTRL+СТРЕЛКА ВВЕРХ**|
|Image.ZoomOut|**CTRL+SHIFT+,**<br /><br /> or<br /><br /> **CTRL+СТРЕЛКА ВНИЗ**|

### <a name="vc-string-editor"></a>Редактор строк VC

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|Edit.NewString|**Вставить**|

### <a name="view-designer"></a>Конструктор представлений

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|QueryDesigner.CancelRetrievingData|**CTRL+T**|
|QueryDesigner.Criteria|**CTRL+2**|
|QueryDesigner.Diagram|**CTRL+1**|
|QueryDesigner.ExecuteSQL|**CTRL+R**|
|QueryDesigner.GotoRow|**CTRL+G**|
|QueryDesigner.JoinMode|**CTRL+SHIFT+J**|
|QueryDesigner.Results|**CTRL+4**|
|QueryDesigner.SQL|**CTRL+3**|

### <a name="visual-studio"></a>Visual Studio

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команда|Сочетание клавиш|
|-------------| - |
|OtherContextMenus.ORDesignerContext.HideMethodsPane|**CTRL+1**|

### <a name="windows-forms-designer"></a>Конструктор Windows Forms

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.BreakLine|**ВВОД**|
|Edit.CharLeft|**СТРЕЛКА ВЛЕВО**|
|Edit.CharLeftExtend|**SHIFT+СТРЕЛКА ВЛЕВО**|
|Edit.CharRight|**СТРЕЛКА ВПРАВО**|
|Edit.CharRightExtend|**SHIFT+СТРЕЛКА ВПРАВО**|
|Edit.DocumentEnd|**END**|
|Edit.DocumentEndExtend|**SHIFT+END**|
|Edit.DocumentStart|**Корневая папка**|
|Edit.DocumentStartExtend|**SHIFT+HOME**|
|Edit.InsertTab|**TAB**|
|Edit.LineDown|**СТРЕЛКА ВНИЗ**|
|Edit.LineDownExtend|**SHIFT+СТРЕЛКА ВВЕРХ**|
|Edit.LineUp|**СТРЕЛКА ВВЕРХ**|
|Edit.LineUpExtend|**SHIFT+СТРЕЛКА ВНИЗ**|
|Edit.MoveControlDown|**CTRL+СТРЕЛКА ВНИЗ**|
|Edit.MoveControlLeft|**CTRL+СТРЕЛКА ВЛЕВО**|
|Edit.MoveControlRight|**CTRL+СТРЕЛКА ВПРАВО**|
|Edit.MoveControlUp|**CTRL+СТРЕЛКА ВВЕРХ**|
|Edit.SelectionCancel|**ESCAPE**|
|Edit.SizeControlDown|**CTRL+SHIFT+СТРЕЛКА ВНИЗ**|
|Edit.SizeControlLeft|**CTRL+SHIFT+СТРЕЛКА ВЛЕВО**|
|Edit.SizeControlRight|**CTRL+SHIFT+СТРЕЛКА ВПРАВО**|
|Edit.SizeControlUp|**CTRL+SHIFT+СТРЕЛКА ВВЕРХ**|
|Edit.TabLeft|**SHIFT+TAB**|

### <a name="work-item-editor"></a>Редактор рабочих элементов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.CreateCopyofWorkItem|**SHIFT+ALT+C**|
|Edit.RefreshWorkItem|**F5**|
|Team.NewLinkedWorkItem|**SHIFT+ALT+L**|

### <a name="work-item-query-view"></a>Представление запросов рабочих элементов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.CreateCopyofWorkItem|**SHIFT+ALT+C**|
|Edit.Indent|**SHIFT+ALT+СТРЕЛКА ВПРАВО**|
|Edit.Outdent|**SHIFT+ALT+СТРЕЛКА ВЛЕВО**|
|Team.NewLinkedWorkItem|**SHIFT+ALT+L**|
|Team.Refresh|**F5**|
|Window.Toggle|**SHIFT+ALT+V**|

### <a name="work-item-results-view"></a>Представление результатов рабочих элементов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.CreateCopyofWorkItem|**SHIFT+ALT+C**|
|Edit.Indent|**SHIFT+ALT+СТРЕЛКА ВПРАВО**|
|Edit.Outdent|**SHIFT+ALT+СТРЕЛКА ВЛЕВО**|
|Team.GotoNextWorkItem|**SHIFT+ALT+N**|
|Team.GotoPreviousWorkItem|**SHIFT+ALT+P**|
|Team.NewLinkedWorkItem|**SHIFT+ALT+L**|
|Team.Refresh|**F5**|
|Window.Toggle|**SHIFT+ALT+V**|

### <a name="workflow-designer"></a>Конструктор рабочих процессов

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Edit.CompleteWord|**CTRL+K, W**<br /><br /> or<br /><br /> **CTRL+K, CTRL+W**<br /><br /> or<br /><br /> **CTRL+ПРОБЕЛ**<br /><br /> or<br /><br /> **ALT+СТРЕЛКА ВПРАВО**|
|Edit.DecreaseFilterLevel|**ALT+,**|
|Edit.IncreaseFilterLevel|**ALT+.**|
|Edit.ListMembers|**CTRL+K, L**<br /><br /> or<br /><br /> **CTRL+K, CTRL+L**<br /><br /> or<br /><br /> **CTRL+J**|
|Edit.ParameterInfo|**CTRL+K, P**<br /><br /> or<br /><br /> **CTRL+K, CTRL+P**<br /><br /> or<br /><br /> **CTRL+SHIFT+ПРОБЕЛ**|
|Edit.QuickInfo|**CTRL+K, I**<br /><br /> or<br /><br /> **CTRL+K, CTRL+I**|
|WorkflowDesigner.Collapse|**CTRL+E, CTRL+C**<br /><br /> or<br /><br /> **CTRL+E, C**|
|WorkflowDesigner.CollapseAll|or|
|WorkflowDesigner.ConnectNodes|**CTRL+E, CTRL+F**<br /><br /> or<br /><br /> **CTRL+E, F**|
|WorkflowDesigner.CreateVariable|**CTRL+E, CTRL+N**<br /><br /> or<br /><br /> **CTRL+E, N**|
|WorkflowDesigner.ExpandAll|**CTRL+E, CTRL+X**<br /><br /> or<br /><br /> **CTRL+E, X**|
|WorkflowDesigner.ExpandInPlace|**CTRL+E, CTRL+E**<br /><br /> or<br /><br /> **CTRL+E, E**|
|WorkflowDesigner.GoToParent|**CTRL+E, CTRL+P**<br /><br /> or<br /><br /> **CTRL+E, P**|
|WorkflowDesigner.MoveFocus|**CTRL+E, CTRL+M**<br /><br /> or<br /><br /> **CTRL+E, M**|
|WorkflowDesigner.NavigateThroughDesigner|**CTRL+ALT+F6**|
|WorkflowDesigner.Restore|**CTRL+E, CTRL+R**<br /><br /> or<br /><br /> **CTRL+E, R**|
|WorkflowDesigner.ShowHideArgumentDesigner|**CTRL+E, CTRL+A**<br /><br /> or<br /><br /> **CTRL+E, A**|
|WorkflowDesigner.ShowHideImportsDesigner|**CTRL+E, CTRL+I**<br /><br /> or<br /><br /> **CTRL+E, I**|
|WorkflowDesigner.ShowHideOverviewMap|**CTRL+E, CTRL+O** (латинская буква O)<br /><br /> or<br /><br /> **CTRL+E, O**|
|WorkflowDesigner.ShowHideVariableDesigner|**CTRL+E, CTRL+V**<br /><br /> or<br /><br /> **CTRL+E, V**|
|WorkflowDesigner.ToggleSelection|**CTRL+E, CTRL+S**<br /><br /> or<br /><br /> **CTRL+E, S**|
|WorkflowDesigner.ZoomIn|**CTRL+NUM +**|
|WorkflowDesigner.ZoomOut|**CTRL+NUM -**|

### <a name="xaml-ui-designer"></a>Конструктор XAML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|Design.FitAll|**CTRL+0** (ноль)|
|Design.ShowHandles|**F9**|
|Design.ZoomIn|**CTRL+ALT+=**|
|Design.ZoomOut|**CTRL+ALT+-**|
|Параметры конструктора|**CTRL+SHIFT+;**|
|Format.EditText|**F2**|
|Format.ResetLayout.All|**CTRL+SHIFT+R**|
|Выполнить код проекта|**CTRL+F9**|
|Timeline.Hide (только в режиме смешения)|**CTRL+H**|
|Timeline.Lock (только в режиме смешения)|**CTRL+L**|
|Timeline.Show (только в режиме смешения)|**CTRL+SHIFT+H**|
|Timeline.Unlock (только в режиме смешения)|**CTRL+SHIFT+L**|
|View.EdgeLeftMoveLeft|**CTRL+SHIFT+,**|
|View.EdgeLeftMoveRight|**CTRL+SHIFT+.**|
|View.EdgeRightMoveLeft|**CTRL+SHIFT+ALT+,**|
|View.EdgeRightMoveRight|**CTRL+SHIFT+ALT+.**|
|View.ShowPropertyMarkerMenu|**CTRL+ПРОБЕЛ**|

### <a name="xml-text-editor"></a>XML-редактор (текстовый)

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|XML.StartXSLTDebugging|**ALT+F5**|
|XML.StartXSLTWithoutDebugging|**CTRL+ALT+F5**|

### <a name="xml-schema-designer"></a>Конструктор схемы XML

Ниже приведены сочетания клавиш, относящиеся к этому контексту.


|Команды|Сочетания клавиш|
|--------------| - |
|GraphView.BottomtoTop|**ALT+СТРЕЛКА ВВЕРХ**|
|GraphView.LefttoRight|**ALT+СТРЕЛКА ВПРАВО**|
|GraphView.RighttoLeft|**ALT+СТРЕЛКА ВЛЕВО**|
|GraphView.ToptoBottom|**ALT+СТРЕЛКА ВНИЗ**|
|OtherContextMenus.GraphView.RemovefromWorkspace|**Удалить**|
|XsdDesigner.ShowContentModelView|**CTRL+2**|
|XsdDesigner.ShowGraphView|**CTRL+3**|
|XsdDesigner.ShowStartView|**CTRL+1**|

## <a name="see-also"></a>См. также

- [Команды Visual Studio](reference/visual-studio-commands.md)
