---
title: Идентификаторы GUID и идентификаторы меню Visual Studio | Документация Майкрософт
description: Просмотрите список значений GUID и ИДЕНТИФИКАТОРов для меню и групп в строке меню Visual Studio, включенной в интегрированную среду разработки Visual Studio (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9f5066c5ae5c9fa57517406b8eca388747979c4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082092"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Идентификаторы GUID и идентификаторы меню Visual Studio
В этой статье перечисляются значения GUID и ID меню и групп в строке меню Visual Studio. Эти значения определены в файлах *. vsct* , которые устанавливаются в составе пакета SDK для Visual Studio. Дополнительные сведения см. в разделе [команды, меню и группы, определяемые интегрированной средой разработки](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Дополнительные сведения о работе с объектами интегрированной среды разработки (IDE), которые определены в *vsct* -файлах, см. в разделе [Расширение меню и команд](../../extensibility/extending-menus-and-commands.md).

 Меню и группы в строке меню Visual Studio используют идентификатор GUID `guidSHLMainMenu` . Сама строка меню имеет идентификатор `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Группы в строке меню Visual Studio
 Чтобы добавить меню в строку меню, установите одну из этих групп в качестве родительской.

|Группа|ID|
|-----------|--------|
|Файл/Правка/представление|IDG_VS_MM_FILEEDITVIEW|
|Рефакторинг|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Сборка|IDG_VS_MM_BUILDDEBUGRUN|
|Формат/средства|IDG_VS_MM_TOOLSADDINS|
|Окно/Справка/сообщество|IDG_VS_MM_WINDOWHELP|
|Надстройки|IDG_VS_MM_MACROS|
|фуллскринбар|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Меню в строке меню Visual Studio
 Чтобы добавить группу в существующее меню Visual Studio, установите одно из следующих меню в качестве родительского. Подменю не включаются в этот список.

|Меню|ID|
|----------|--------|
|Файл|IDM_VS_MENU_FILE|
|Изменить|IDM_VS_MENU_EDIT|
|Представление|IDM_VS_MENU_VIEW|
|Рефакторинг|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Сборка|IDM_VS_MENU_BUILD|
|Формат|IDM_VS_MENU_FORMAT|
|Инструменты|IDM_VS_MENU_TOOLS|
|Расширения|IDM_VS_MENU_EXTENSIONS|
|Окно|IDM_VS_MENU_WINDOW|
|Надстройки|IDM_VS_MENU_ADDINS|
|Сообщество|IDM_VS_MENU_COMMUNITY|
|Справка|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Группы в меню Visual Studio
 В следующих списках показаны группы, расположенные непосредственно из меню в строке меню Visual Studio. Самый быстрый способ добавить команду в меню Visual Studio — задать одну из этих групп в качестве родительской. Группы из подменю не отображаются в этом разделе.

### <a name="file-menu-groups"></a>Группы меню "файл"

|Группа|ID|
|-----------|--------|
|Создать или открыть|IDG_VS_FILE_FILE|
|Добавить|IDG_VS_FILE_ADD|
|Решение|IDG_VS_FILE_SOLUTION|
|Разное|IDG_VS_FILE_MISC|
|Сохранить|IDG_VS_FILE_SAVE|
|Переименовать|IDG_VS_FILE_RENAME|
|Браузер|IDG_VS_FILE_BROWSER|
|Печать|IDG_VS_FILE_PRINT|
|Последние использованные|IDG_VS_FILE_MRU|
|Переместить|IDG_VS_FILE_MOVE|
|Выход|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Изменить группы меню

|Группа|ID|
|-----------|--------|
|Отменить/Повторить|IDG_VS_EDIT_UNDOREDO|
|Вырезать, копировать и вставить|IDG_VS_EDIT_CUTCOPY|
|Выберите пункт|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Поиск|IDG_VS_EDIT_FIND|
|Объекты|IDG_VS_EDIT_OBJECTS|
|Команды OLE|IDG_VS_EDIT_OLEVERBS|
|Контейнер команды|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Группы меню Рефакторинг

|Группа|ID|
|-----------|--------|
|Распространенные|IDG_REFACTORING_COMMON|
|Продвинутый уровень|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Группы меню "вид"

|Группа|ID|
|-----------|--------|
|Код формы|IDG_VS_VIEW_FORMCODE|
|Браузер|IDG_VS_VIEW_BROWSER|
|Определение представлений|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Архитектурные окна|IDG_VS_VIEW_ARCH_WINDOWS|
|Окна Организации|IDG_VS_VIEW_ORG_WINDOWS|
|Браузер кода|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Окна разработки|IDG_VS_VIEW_DEV_WINDOWS|
|Панели инструментов|IDG_VS_VIEW_TOOLBARS|
|Символы|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Перейти.|IDG_VS_VIEW_NAVIGATE|
|Мелкий переход|IDG_VS_VIEW_SMALLNAVIGATE|
|Обозреватель объектов|IDG_VS_VIEW_OBJBRWSR|
|Контейнер команды|IDG_VS_VIEW_COMMANDWELL|
|Страницы свойств|IDG_VS_VIEW_PROPPAGES|
|Обновить|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Группы меню "проект"

|Группа|ID|
|-----------|--------|
|Прочие добавления|IDG_VS_PROJ_MISCADD|
|Добавить|IDG_VS_PROJ_ADD|
|Папка|IDG_VS_PROJ_FOLDER|
|Выгрузить/перезагрузить|IDG_VS_PROJ_UNLOADRELOAD|
|Справочник|IDG_VS_PROJ_REFERENCE|
|Варианты|IDG_VS_PROJ_OPTIONS|
|Параметры|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Группы меню "сборка"

|Группа|ID|
|-----------|--------|
|Решение|IDG_VS_BUILD_SOLUTION|
|Выбор|IDG_VS_BUILD_SELECTION|
|Оптимизация с использованием профиля|IDG_VS_PGO_SELECTION|
|Прочее|IDG_VS_BUILD_MISC|
|Отменить|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Группы меню "Сервис"

|Группа|ID|
|-----------|--------|
|Командная строка|IDG_VS_TOOLS_CMDLINE|
|Фрагменты кода|IDG_VS_TOOLS_SNIPPETS|
|Подмножество объектов|IDG_VS_TOOLS_OBJSUBSET|
|Варианты|IDG_VS_TOOLS_OPTIONS|
|Другие 2|IDG_VS_TOOLS_OTHER2|
|Внешние инструменты|IDG_VS_TOOLS_EXT_TOOLS|
|Внешние настройки|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Группы меню "окно"

|Группа|ID|
|-----------|--------|
|Оператор new|IDG_VS_WINDOW_NEW|
|Закрепить/закрыть|IDG_VS_DOCKCLOSE|
|Закрепить/скрыть|IDG_VS_DOCKHIDE|
|Упорядочить|IDG_VS_WINDOW_ARRANGE|
|Навигация|IDG_VS_WINDOW_NAVIGATION|
|Список|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Группы меню "Справка"

|Группа|ID|
|-----------|--------|
|Примеры|IDG_VS_HELP_SAMPLES|
|Поддержка|IDG_VS_HELP_SUPPORT|
|Сведения|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Подменю меню Visual Studio
 В следующей иерархии отображаются подменю, связанные с меню в строке меню Visual Studio. Так как только группа может иметь меню в качестве своего родителя, каждое подменю должно быть в группе в меню, а не непосредственно из меню. Дополнительные сведения о связях между меню, группами и подменю см. в разделе Добавление подменю [в меню](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Имена меню в строке меню Visual Studio не отображаются отдельно в этой иерархии, так как их можно вывести из соглашения об именовании для групп в интегрированной среде разработки следующим образом: *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

|Родительская группа|Служат|Дочерние группы|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1... 1-6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>См. также
- [Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Идентификаторы GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Файлы таблицы команд Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
