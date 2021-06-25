---
title: Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio | Документация Майкрософт
description: Просмотрите список идентификаторов GUID и ИДЕНТИФИКАТОРов для панелей инструментов и содержащихся в них групп, которые включены в интегрированную среду разработки (IDE) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d2ba6c92a2913ec63a59751a4181454aa67fa67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898114"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio
В этом разделе перечисляются идентификаторы GUID и ИДЕНТИФИКАТОРы панелей инструментов, которые включены в интегрированную среду разработки (IDE) Visual Studio, и группы, которые они содержат. Эти значения определены в файлах *. vsct* , которые устанавливаются в составе пакета SDK для Visual Studio. Дополнительные сведения см. в разделе [команды, меню и группы, определяемые интегрированной средой разработки](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
> Многие из панелей инструментов, доступных для Visual Studio, не определены в Visual Studio, а их идентификаторы GUID и ИДЕНТИФИКАТОРы не являются общедоступными. В этом разделе перечислены только панели инструментов, определенные в файлах Visual Studio SDK *. vsct* .

 Дополнительные сведения о работе с объектами IDE, которые определены в *vsct* -файлах, см. в разделе [Расширение меню и команд](../../extensibility/extending-menus-and-commands.md).

 Панели инструментов по умолчанию, предоставляемые интегрированной средой разработки Visual Studio, используют идентификатор GUID `guidSHLMainMenu` , если иное не указано с помощью `GUID:ID` синтаксиса.

## <a name="ide-toolbars"></a>Панели инструментов IDE
 Интегрированная среда разработки Visual Studio предоставляет следующие панели инструментов. Панели инструментов можно отобразить, выбрав их в подменю **панели инструментов** меню **Сервис** . Панели инструментов в окнах инструментов не включены в этот раздел.

 Только группы могут переходить непосредственно из панелей инструментов. Чтобы добавить группу, присвойте ее родительскому элементу GUID и идентификатор панели инструментов. Чтобы добавить кнопку на панель инструментов, установите ее родительский элемент в группу на панели инструментов.

|Панель инструментов|ID|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Сборка|IDM_VS_TOOL_BUILD|
|Текстовый редактор|IDM_VS_TOOL_TEXTEDITOR|
|Отладка|Гуидвсдебугграуп: IDM_DEBUG_TOOLBAR|
|Расположение отладки|Гуидвсдебугграуп: IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Специальные панели инструментов
 Эти панели инструментов определяются интегрированной средой разработки Visual Studio, но они служат специализированными функциями и не размещают группы команд.

|Панель инструментов|ID|
|-------------|--------|
|Команда Add|IDM_VS_TOOL_ADDCOMMAND|
|Не определено.|IDM_VS_TOOL_UNDEFINED|
|схема XML|IDM_VS_TOOL_SCHEMA|
|XML-данные|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Группы на панелях инструментов интегрированной среды разработки
 Чтобы добавить кнопку на стандартную панель инструментов, установите одну из следующих групп в качестве ее родителя. Группы сортируются по родительской панели инструментов.

### <a name="standard-toolbar-groups"></a>Стандартные группы панелей инструментов

|Имя|ID|
|----------|--------|
|Сохранить или открыть|IDG_VS_TOOLSB_SAVEOPEN|
|Вырезать или копировать|IDG_VS_TOOLSB_CUTCOPY|
|Отменить/Повторить|IDG_VS_TOOLSB_UNDOREDO|
|Запуск и сборка|IDG_VS_TOOLSB_RUNBUILD|
|Поиск|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Новые окна|IDG_VS_TOOLSB_NEWWINDOWS|
|Загрузка и сохранение|IDG_VS_WINDOWUI_LOADSAVE|
|Датчик|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Создание групп панелей инструментов

|Имя|ID|
|----------|--------|
|Панель построения|IDG_VS_BUILDBAR|
|Отменить|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Группы панелей инструментов текстового редактора

|Имя|ID|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|Отступ|IDG_VS_EDITTOOLBAR_INDENT|
|Комментировать|IDG_VS_EDITTOOLBAR_COMMENT|
|Закладки|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Отладка групп панелей инструментов

|Имя|ID|
|----------|--------|
|Выполнение|IDM_DEBUG_TOOLBAR|
|Отладка по шагам|IDG_DEBUG_TOOLBAR_STEPPING|
|Watch|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Группы панелей инструментов расположения отладки

|Имя|ID|
|----------|--------|
|Расположение отладки|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Панели инструментов окна инструментов
 Панели инструментов могут отображаться непосредственно в интегрированной среде разработки или в окнах инструментов, таких как **Обозреватель решений**. Так как окна инструментов не определены в *vsct* -файлах, панели инструментов окна инструментов не имеют определенных родителей. Вместо этого они помещаются в код. В следующей таблице показаны панели инструментов, отображаемые в окнах инструментов в интегрированной среде разработки, и группы команд, которые они содержат.

> [!NOTE]
> Панели инструментов и группы используют идентификатор GUID `guidSHLMainMenu` , за исключением случаев, когда иное указано с помощью синтаксиса GUID: ID. Если для панели инструментов указан идентификатор GUID, он также применяется к группам, начиная с этой панели инструментов.

|Окно инструментов|Панель инструментов|Группы|
|-----------------|-------------|------------|
|Обозреватель решений|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.. 5.0|
|Обозреватель серверов|guid_SE_MenuGroup: IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Свойства|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Представление классов|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Представление классов|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Обозреватель объектов|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Обозреватель объектов|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Выходные данные|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Найти и заменить|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Результаты поиска 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Результаты поиска 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Фрагмент кода|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Закладки|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Список задач|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Задачи пользователя|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Список ошибок|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Обозреватель вызовов|IDM_VS_TOOL_CALLBROWSER1.. глубин|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Точки останова|Гуидвсдебугграуп: IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Дизассемблированный код|Гуидвсдебугграуп: IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Память 1-4|Гуидвсдебугграуп: IDM_MEMORY_WINDOW_TOOLBAR1... четырех|IDG_MEMORY_EXPRESSION1.. четырех<br /><br /> IDG_MEMORY_COLUMNS1.. четырех|
|Процессы|Гуидвсдебугграуп: IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>См. также
- [Добавление контроллера меню на панель инструментов](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Добавление панели инструментов в окно инструментов](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
