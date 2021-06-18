---
title: API, удаленные в предварительной версии Visual Studio 2022
description: Сведения об API-интерфейсах пакета SDK VS, удаленных в предварительной версии Visual Studio 2022, для авторов расширений, которые обновляют свои расширения для работы с предварительной версией Visual Studio 2022.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: bed8d0a261f70acb5e842ebeaf0059faae3fc478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308617"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Удаленные API-интерфейсы пакета SDK для Visual Studio 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

Приведенные ниже API были удалены из пакета SDK для Visual Studio и больше не могут использоваться. Дополнительные сведения об обновлении кода см. в каждом разделе.

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` перетаскивани `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [Асинхронная загрузка решения и загрузка упрощенного решения](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [Открыть из источника "защищено"](#open-from-source-safe)
* [Новые Конструктор XAML WPF для платформа .NET Framework](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>ивсимажесервице

`IVsImageService`Удаляется в Visual Studio 2022. `IVsImageService`Вместо этого все пользователи должны перейти `IVsImageService2` на.

### <a name="recommended-updates"></a>Рекомендуемые обновления

Если используется `IVsImageService` , замените вызовы к своим методам вызовами эквивалентных методов в `IVsImageService2` :

| **Метод Ивсимажесервице** | **Эквивалентный метод IVsImageService2** |
|----------------------------|----------------------------------------|
| Добавить                        | аддкустомимаже                         |
| Получить                        | GetImage                               |
| жетиконфорфиле             | жетимажемоникерфорфиле                 |
| жетиконфорфиликс           | жетимажемоникерфорфиле                 |

`IVsImageService`— Это методы добавления и получения, которые называются пользовательскими изображениями по имени (строке), а не моникеру.  Предпочтительнее переключать код на использование только моникеров для ссылки на пользовательские образы, но если это нецелесообразно, то в `IVsImageService2` некоторых методах можно связать имя с моникером:

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

Используя эти два метода, можно продолжать ссылаться на изображения по имени.

## <a name="iblockcontextprovider"></a>иблоккконтекстпровидер

`IBlockContextProvider`Связанные типы и удаляются в Visual Studio 2022. `IBlockContextProvider`Вместо этого все пользователи должны перейти `IStructureContextSourceProvider` на.

### <a name="recommended-updates"></a>Рекомендуемые обновления

Пользователям `IBlockContextProvider` следует использовать `IStructureContextSourceProvider` вместо этого ([Документация](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)).

## <a name="itooltipprovider"></a>итултиппровидер

`IToolTipProvider`Связанные типы и удаляются в Visual Studio 2022. `IToolTipProvider`Вместо этого все пользователи должны перейти `IToolTipService` на.

### <a name="recommended-updates"></a>Рекомендуемые обновления

Пользователям `IToolTipProvider` следует использовать `IToolTipService` вместо этого ([Документация](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)).

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>Ивстекстсканнер и Ивсфуллтекстсканнер

`IVsTextScanner`И `IVsFullTextScanner` удаляются в Visual Studio 2022. `IVsTextScanner`Вместо этого все пользователи или `IVsFullTextScanner` должны перейти на `IVsTextLines` .

### <a name="recommended-updates"></a>Рекомендуемые обновления

Пользователи `IVsTextScanner` или `IVsFullTextScanner` должны использовать `IVsTextLines` вместо него ([документацию](/dotnet/apimicrosoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)).

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>Асинхронная загрузка решения и загрузка упрощенного решения

Функции асинхронной загрузки решения (АСЛ) и облегченной загрузки решения (LSL) удаляются в Visual Studio 2022, так как удаляются следующие методы:

### <a name="interfaces"></a>Интерфейсы

* `IVsSolution4` — Методы: `IsBackgroundSolutionLoadEnabled` , `EnsureProjectsAreLoaded` , `EnsureProjectIsLoaded` , `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` — Методы: `OnBeforeBackgroundSolutionLoadBegins` , `OnQueryBackgroundLoadProjectBatch` , `OnBeforeLoadProjectBatch` , `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` — Весь интерфейс
* `IVsSolutionLoadManager` — Весь интерфейс
* `IVsSccManager3`  — Весь интерфейс
* `IVsAsynchronousProjectCreate` — Весь интерфейс
* `IVsAsynchronousProjectCreateUI` — Весь интерфейс

### <a name="enums-properties-and-ui-contexts"></a>Перечисления, свойства и контексты пользовательского интерфейса

* `VSHPROPID_ProjectUnloadStatus` Перечисления `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>Рекомендуемые обновления

Отсутствует.

## <a name="ivsdummy"></a>ивсдумми

`IVsDummy`Удаляется в Visual Studio 2022 и не заменяется. 

### <a name="recommended-updates"></a>Рекомендуемые обновления

Отсутствует. Но это не должно повлиять на то, что API ничего не делало.

## <a name="microsoftvisualstudioshelltask"></a>Microsoft. VisualStudio. Shell. Task

`Microsoft.VisualStudio.Shell.Task`Класс был переименован в, чтобы `Microsoft.VisualStudio.Shell.TaskListItem` не конфликтовать с очень популярным `System.Threading.Tasks.Task` классом.

## <a name="open-from-source-safe"></a>Открыть из источника "защищено"

Удаляется поддержка открытия решения из безопасного источника, так как удаляются следующие методы, события и константы.

## <a name="interfaces"></a>Интерфейсы

* `IVsSCCProvider3` — Весь интерфейс

### <a name="recommended-updates"></a>Рекомендуемые обновления

Отсутствует.

## <a name="new-wpf-xaml-designer-for-net-framework"></a>Новые Конструктор XAML WPF для платформа .NET Framework

Текущая Конструктор XAML WPF для платформа .NET Framework является устаревшей и будет заменена новой Конструктор XAML WPF для платформа .NET Framework на основе той же архитектуры, которая использовалась для Конструктор XAML WPF для .NET (.NET Core). Это также означает, что модель расширяемости элемента управления WPF платформа .NET Framework на основе .design.dll и Microsoft. Windows. Design. Extensibility больше не поддерживается. Новая Конструктор XAML WPF для платформа .NET Framework предоставит ту же модель расширяемости, что и Конструктор XAML WPF для .NET (.NET Core). Если вы уже создали расширение .designtools.dll для .NET (.NET Core), это расширение будет работать для новых Конструктор XAML WPF для платформа .NET Framework. Дополнительные сведения о переходе на новую модель расширяемости для платформ WPF (платформа .NET Framework и .NET Core) и на платформах UWP можно найти по ссылке перехода ниже. 

### <a name="recommended-updates"></a>Рекомендуемые обновления

См. раздел [Миграция расширяемости конструктора XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md).
