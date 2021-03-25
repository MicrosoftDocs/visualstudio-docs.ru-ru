---
title: Регистрация типа проекта | Документация Майкрософт
description: Сведения о создании записей реестра, позволяющих Visual Studio распознать и работать с новым типом проекта.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e54f62a90ece61fc2dd8f3cc2b242957f249ed33
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062776"
---
# <a name="registering-a-project-type"></a>Регистрация типа проекта
При создании нового типа проекта необходимо создать записи реестра, которые позволяют [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] распознать тип проекта и работать с ним. Обычно эти записи реестра создаются с помощью файла скрипта реестра (RGS).

 В приведенном ниже примере инструкции из реестра предоставляют пути и данные по умолчанию, а затем таблицу, содержащую записи из скрипта реестра для каждой инструкции. Таблицы содержат записи скрипта и дополнительные сведения об инструкциях.

> [!NOTE]
> Следующие сведения о реестре предназначены для примера типа и целей записей в сценариях реестра, которые будут записываться для регистрации типа проекта. Фактические записи и их использование могут различаться в зависимости от конкретных требований типа проекта. Ознакомьтесь с доступными примерами, чтобы найти тот, который похож на тип разрабатываемого проекта, а затем просмотрите сценарий реестра для этого примера.

 Следующие примеры взяты из HKEY_CLASSES_ROOT.

## <a name="example-1"></a>Пример 1

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|Имя|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|Имя и описание файлов типа проекта с расширением фигп.|
|`Content Type`|REG_SZ|`Text/plain`|Тип содержимого для файлов проекта.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Значок по умолчанию, используемый для проекта этого типа. Инструкция% MODULE% завершена в реестре до расположения библиотеки типа проекта по умолчанию.|
|`@`|REG_SZ|`&Open in Visual Studio`|Приложение по умолчанию, в котором будет открыт этот тип проекта.|
|`@`|REG_SZ|`devenv.exe "%1"`|Команда по умолчанию, которая будет запускаться при открытии проекта этого типа.|

 Следующие примеры взяты из HKEY_LOCAL_MACHINE и находятся в реестре раздела [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].

## <a name="example-2"></a>Пример 2

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|Имя|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@` (по умолчанию)|REG_SZ|`FigPrj Project VSPackage`|Локализуемое имя этого зарегистрированного пакета VSPackage (тип проекта).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Путь к DLL типа проекта. Интегрированная среда разработки загружает эту библиотеку DLL и передает идентификатор CLSID пакета VSPackage для `DllGetClassObject` <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> создания <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> объекта.|
|`CompanyName`|REG_SZ|`Microsoft`|Название компании, которая разработала тип проекта.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Имя типа проекта.|
|`ProductVersion`|REG_SZ|`9.0`|Номер версии типа проекта выпуск.|
|`MinEdition`|REG_SZ|`professional`|Выпуск регистрируемого пакета VSPackage.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Ключ загрузки пакета для проекта VSPackage. Ключ проверяется, когда проект загружается после запуска среды.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Имя файла вспомогательной библиотеки DLL, содержащей локализованные ресурсы для типа проекта.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Путь к вспомогательной библиотеке DLL.|
|`FigProjectsEvents`|REG_SZ|См. инструкцию для value.|Определяет текстовую строку, возвращаемую для этого события автоматизации.|
|`FigProjectItemsEvents`|REG_SZ|См. инструкцию для value.|Определяет текстовую строку, возвращаемую для этого события автоматизации.|

 Все приведенные ниже примеры находятся в реестре раздела [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-3"></a>Пример 3

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Имя|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Имена проектов этого типа по умолчанию.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Идентификатор ресурса имени, которое должно быть получено из вспомогательной библиотеки DLL, зарегистрированной в пакетах.|
|`Package`|REG_SZ|`%CLSID_Package%`|Идентификатор класса VSPackage, зарегистрированного в пакетах.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь по умолчанию к файлам шаблонов проектов. Это файлы, отображаемые в новом шаблоне проекта.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Путь по умолчанию для файлов шаблонов элементов проекта. Это файлы, отображаемые шаблоном Добавление нового элемента.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Позволяет интегрированной среде разработки реализовать диалоговое окно " **Открыть** ".|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Используется интегрированной средой разработки для определения того, обрабатывается ли открываемый проект этим типом проекта (фабрикой проекта). В качестве формата для нескольких записей используется список, разделенный точкой с запятой. Например, "vdproj; ВДП".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Используется интегрированной средой разработки в качестве расширения имени файла по умолчанию для операции "Сохранить как".|
|`Filter Settings`|REG_DWORD|Различные, см. инструкции и комментарии, приведенные в таблице ниже.|Эти параметры используются для задания различных фильтров для отображения файлов в диалоговых окнах пользовательского интерфейса.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Идентификатор ресурса для добавления шаблонов элементов.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Путь к элементам проекта, отображаемым в диалоговом окне для шаблона " **Добавить новый элемент** ".|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Определяет порядок сортировки в узле дерева файлов, отображаемых в диалоговом окне " **Добавление нового элемента** ".|

 В следующей таблице показаны параметры фильтров, доступные в предыдущем сегменте кода.

|Параметр фильтра|Описание|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Указывает, что фильтр является одним из общих фильтров в диалоговом окне **найти в файлах** . Общие фильтры перечислены в списке фильтров до тех пор, пока фильтры не помечаются как общие.|
|`CommonOpenFilesFilter`|Указывает, что фильтр является одним из общих фильтров в диалоговом окне **Открытие файла** . Общие фильтры перечислены в списке фильтров до тех пор, пока фильтры не помечаются как общие.|
|`FindInFilesFilter`|Указывает, что фильтр будет одним из фильтров в диалоговом окне **найти в файлах** и будет указан после общих фильтров.|
|`NotOpenFileFilter`|Указывает, что фильтр не будет использоваться в диалоговом окне **Открытие файла** .|
|`NotAddExistingItemFilter`|Указывает, что фильтр не будет использоваться в диалоговом окне "Добавление **существующего элемента** ".|

 По умолчанию, если в фильтре не задан один или несколько флагов, фильтр используется в диалоговом окне **Добавление существующего элемента** и в диалоговом окне **Открытие файла** после перечисления общих фильтров. Фильтр не используется в диалоговом окне **найти в файлах** .

 Все приведенные ниже примеры находятся в реестре раздела [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-4"></a>Пример 4

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Имя|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Идентификатор ресурса для новых шаблонов проектов.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь по умолчанию для проектов зарегистрированного типа проекта.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Задает порядок сортировки проектов, отображаемых в диалоговом окне Мастер создания проектов.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|значение 0 указывает, что проекты этого типа отображаются только в диалоговом окне Новый проект.|

 Все приведенные ниже примеры находятся в реестре раздела [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example-5"></a>Пример 5

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Имя|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Отсутствуют|Значение по умолчанию, которое указывает, что для записей проектов прочих файлов используются следующие записи.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Значение идентификатора ресурса для файлов шаблонов добавления новых элементов.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Путь по умолчанию к элементам, которые будут отображаться в диалоговом окне " **Добавление нового элемента** ".|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Устанавливает порядок сортировки для элементов, отображаемых в узле дерево диалогового окна **Добавление нового элемента** .|

 Следующий пример находится в реестре раздела [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].

## <a name="example-6"></a>Пример 6

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Запись меню указывает IDE на ресурс, используемый для получения сведений о меню. Если эти данные были объединены в базу данных меню, то тот же ключ будет добавлен в раздел Менусмержед реестра. Пакет VSPackage не должен изменять ничего в разделе Менусмержед напрямую. В поле данных в следующей таблице есть три поля, разделенные запятыми. Первое поле определяет полный путь к файлу ресурсов меню:

- Если первое поле пропущено, ресурс меню загружается из вспомогательной библиотеки DLL, определяемой идентификатором GUID VSPackage.

  Второе поле определяет идентификатор ресурса меню для типа CTMENU:

- Если указан идентификатор ресурса и путь к файлу предоставляется первым параметром, ресурс меню загружается из полного пути к файлу.

- Если указан идентификатор ресурса, но путь к файлу не указан, ресурс меню загружается из вспомогательной библиотеки DLL.

- Если указан полный путь к файлу и идентификатор ресурса отсутствует, то загружаемый файл должен быть файлом CTO.

  Последнее поле определяет номер версии для ресурса CTMENU. Вы можете снова выполнить слияние меню, изменив номер версии.

|Имя|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|% CLSID_Package%|REG_SZ|`,1000,1`|Ресурс для получения сведений о меню.|

 Все приведенные ниже примеры находятся в реестре раздела [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Имя|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Значение идентификатора ресурса для проекта рисунков новые шаблоны проектов.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Путь по умолчанию к каталогу новых проектов. Элементы в этом каталоге будут отображаться в диалоговом окне **Мастер создания проекта** .|
|`SortPriority`|REG_DWORD|`41 (x29)`|Устанавливает порядок, в котором проекты будут отображаться в узле дерево диалогового окна " **Новый проект** ".|
|`NewProjectDialogOnly`|REG_DWORD|`0`|значение 0 указывает, что проекты этого типа отображаются только в диалоговом окне **Новый проект** .|

 Следующий пример находится в реестре раздела [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Имя|Type|Данные|Описание|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|Идентификатор класса зарегистрированного пакета VSPackage.|
|`UseInterface`|REG_DWORD|`1`|значение 1 указывает, что пользовательский интерфейс будет использоваться для взаимодействия с этим проектом. значение 0 указывает, что интерфейс пользовательского интерфейса отсутствует.|

 VSZ-файлы, управляющие новыми типами проектов, часто содержат запись RELATIVE_PATH. Этот путь указывается относительно пути, указанного в разделе \Продуктдир записи типа проекта в следующем ключе установки:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Например, шаблоны проектов Enterprise Framework добавляют следующие записи реестра:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Студио\ентерприсефрамеворкс\

 Это означает, что если включить в VSZ-файл запись PROJECT_TYPE = EF, среда находит VSZ-файлы в каталоге Продуктдир, указанном ранее.

## <a name="see-also"></a>См. также
- [Контрольный список. Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)
- [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
