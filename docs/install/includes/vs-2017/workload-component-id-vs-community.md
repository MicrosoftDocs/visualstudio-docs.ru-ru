---
title: Идентификаторы рабочих нагрузок и компонентов для Visual Studio Community 2017
titleSuffix: ''
description: Идентификаторы рабочих нагрузок и компонентов позволяют устанавливать Visual Studio с помощью командной строки. Также их можно указать в качестве зависимости в манифесте VSIX.
keywords: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.date: 2/12/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: ec1a9fe14a5bf78395b76f0dc85f4ad061ed3329
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "110449757"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2017"></a>Основной редактор Visual Studio (входит в состав Visual Studio Community 2017)

**Идентификатор:** Microsoft.VisualStudio.Workload.CoreEditor

**Описание.** Основные возможности оболочки Visual Studio, включая редактирование кода с учетом синтаксиса, управление исходным кодом и рабочими элементами.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Основной редактор Visual Studio | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Начальная страница Visual Studio для пользователей C++ | 15.0.27128.1 | Необязательный

## <a name="azure-development"></a>Разработка для Azure

**Идентификатор:** Microsoft.VisualStudio.Workload.Azure

**Описание.** Пакеты Azure SDK, инструменты и проекты для разработки облачных приложений, создания ресурсов и контейнеров, включая поддержку Docker.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 15.0.26720.2 | Обязательное значение
Component.Microsoft.VisualStudio.Web.AzureFunctions | Средства веб-заданий Microsoft Azure | 15.7.27617.1 | Обязательное значение
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 15.8.27705.0 | Обязательно
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Обязательное значение
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательное значение
Microsoft.Component.NetFX.Core.Runtime | Среда выполнения .NET Core | 15.0.26208.0 | Обязательное значение
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательное значение
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.NetCore.ComponentGroup.Web.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 15.9.28307.421 | Обязательное значение
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 15.9.28307.421 | Обязательное значение
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 15.9.28125.51 | Обязательное значение
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Обязательное значение
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 15.8.27906.1 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Средства разработки для контейнеров — средства сборки | 15.7.27617.1 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Поддержка языка F# для веб-проектов | 15.9.28307.421 | Обязательное значение
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательное значение
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 15.0.26621.2 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 15.7.27617.1 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.NCLI | собственный клиент SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Обязательное значение
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательное значение
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Необходимые компоненты для разработки на базе Azure | 15.9.28107.0 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Средства веб-заданий Microsoft Azure | 15.7.27617.1 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 15.9.28219.51 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Обязательное значение
Microsoft.Component.Azure.DataLake.Tools | Средства Azure Data Lake и Stream Analytics | 15.9.28107.0 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.AspNet45 | Дополнительные возможности ASP.NET | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Пакет SDK для мобильных приложений Azure | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Основные инструменты Azure Resource Manager | 15.9.28107.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Средства Service Fabric | 15.8.27825.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | 15.9.28107.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 15.7.27617.1 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Инструменты облачных служб Azure | 15.0.26504.0 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Средства Azure Resource Manager | 15.0.27005.2 | Рекомендованное
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 15.8.27825.0 | Необязательный
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 15.8.27825.0 | Необязательный
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Средства разработки для .NET Framework 4.7.2 | 15.8.27825.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 15.6.27406.0 | Необязательный
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 2.0 | 15.6.27406.0 | Необязательный
Microsoft.Net.Core.Component.SDK.1x | Средства разработки .NET Core 1.0–1.1 | 15.6.27406.0 | Необязательный
Microsoft.NetCore.1x.ComponentGroup.Web | Средства разработки .NET Core 1.0–1.1 для веб-приложений | 15.6.27406.0 | Необязательный
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Средства разработки .NET Core 2.0 | 15.8.27729.1 | Необязательный
Microsoft.NetCore.ComponentGroup.Web | Средства разработки .NET Core 2.0 | 15.7.27625.0 | Необязательный
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy службы хранилища Azure | 15.0.26906.1 | Необязательный
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Необязательный

## <a name="data-storage-and-processing"></a>Хранение и обработка данных

**Идентификатор:** Microsoft.VisualStudio.Workload.Data

**Описание.** Связывание, разработка и тестирование решений по обработке данных с помощью SQL Server, Azure Data Lake и Hadoop.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 15.0.26720.2 | Рекомендованное
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 15.8.27705.0 | Рекомендуется
Component.Redgate.SQLSearch.VSExtension | Поиск Redgate SQL | 3.1.7.2062 | Рекомендуется
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Рекомендованное
Microsoft.Component.Azure.DataLake.Tools | Средства Azure Data Lake и Stream Analytics | 15.9.28107.0 | Рекомендованное
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Рекомендованное
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 15.9.28307.421 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 15.9.28307.421 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 15.9.28125.51 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | 15.9.28107.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 15.7.27617.1 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Рекомендованное
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 15.8.27906.1 | Рекомендованное
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Средства разработки для контейнеров — средства сборки | 15.7.27617.1 | Рекомендованное
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Рекомендованное
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Рекомендуется
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 15.0.26621.2 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 15.7.27617.1 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.NCLI | собственный клиент SQL Server | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Рекомендуется
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 15.8.27825.0 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 15.9.28219.51 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Рекомендованное
Microsoft.VisualStudio.Component.FSharp.Desktop | Поддержка языка F# для классических приложений | 15.8.27825.0 | Необязательный

## <a name="data-science-and-analytical-applications"></a>Приложения для обработки и анализа данных и аналитические приложения

**Идентификатор:** Microsoft.VisualStudio.Workload.DataScience

**Описание.** Языки и инструменты для создания приложений для обработки и анализа данных, включая Python, R и F#.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Anaconda3.x64 | 64-разрядная версия Anaconda3 (5.2.0) | 5.2.0 | Рекомендуется
Microsoft.Component.CookiecutterTools | Поддержка шаблонов Cookiecutter | 15.0.26621.2 | Рекомендованное
Microsoft.Component.PythonTools | Поддержка языка Python | 15.0.26823.1 | Рекомендованное
Microsoft.Component.PythonTools.Web | Поддержка веб-приложений Python | 15.9.28107.0 | Рекомендованное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Рекомендованное
Microsoft.VisualStudio.Component.FSharp.Desktop | Поддержка языка F# для классических приложений | 15.8.27825.0 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Рекомендуется
Microsoft.VisualStudio.Component.R.Open | Microsoft R Client (3.3.2) | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.RHost | Поддержка средств разработки R в среде выполнения | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.RTools | Поддержка языка R | 15.0.26919.1 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Рекомендуется
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Рекомендованное
Component.Anaconda2.x64 | 64-разрядная версия Anaconda2 (5.2.0) | 5.2.0 | Необязательный
Component.Anaconda2.x86 | 32-разрядная версия Anaconda2 (5.2.0) | 5.2.0 | Необязательный
Component.Anaconda3.x86 | 32-разрядная версия Anaconda3 (5.2.0) | 5.2.0 | Необязательный
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 15.6.27309.0 | Необязательный
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Встроенные средства разработки Python | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Graphics.Win81 | Пакет SDK графических инструментов для Windows 8.1 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.VC.140 | Набор инструментов VC++ 2015.3 v14.00 (v140) для ПК | 15.7.27617.1 | Необязательный
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 15.0.26823.1 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.Component.Windows81SDK | Пакет SDK для Windows 8.1 | 15.6.27406.0 | Необязательный

## <a name="net-desktop-development"></a>Разработка классических приложений .NET

**Идентификатор:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Описание.** Разработка приложений WPF, Windows Forms и консольных приложений с использованием .C#, Visual Basic и F#.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Средства разработки классических приложений .NET | 15.7.27625.0 | Обязательное значение
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Обязательное значение
Microsoft.ComponentGroup.Blend | Blend для Visual Studio | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 15.0.27005.2 | Рекомендованное
Microsoft.VisualStudio.Component.EntityFramework | Инструменты для Entity Framework 6 | 15.6.27406.0 | Рекомендованное
Component.Dotfuscator | PreEmptive Protection — Dotfuscator | 15.0.26208.0 | Необязательный
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 15.0.26720.2 | Необязательный
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 15.8.27705.0 | Необязательный
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Необязательный
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 15.8.27825.0 | Необязательный
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 15.8.27825.0 | Необязательный
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Средства разработки для .NET Framework 4.7.2 | 15.8.27825.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 15.6.27406.0 | Необязательный
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 2.0 | 15.6.27406.0 | Необязательный
Microsoft.Net.Core.Component.SDK.1x | Средства разработки .NET Core 1.0–1.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Необязательный
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Средства разработки .NET Core 2.0 | 15.8.27729.1 | Необязательный
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Необязательный
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Необязательный
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 15.8.27906.1 | Необязательный
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Средства разработки для контейнеров — средства сборки | 15.7.27617.1 | Необязательный
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.FSharp.Desktop | Поддержка языка F# для классических приложений | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Необязательный
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Необязательный
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Необязательный
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 15.0.26621.2 | Необязательный
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 15.7.27617.1 | Необязательный
Microsoft.VisualStudio.Component.SQL.NCLI | собственный клиент SQL Server | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Необязательный
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Необязательный
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Необязательный
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 15.9.28219.51 | Необязательный
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Необязательный

## <a name="game-development-with-unity"></a>Разработка игр с помощью Unity

**Идентификатор:** Microsoft.VisualStudio.Workload.ManagedGame

**Описание.** Создание двухмерных и трехмерных игр с помощью Unity, мощной кроссплатформенной среды разработки.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Средства разработки для .NET Framework 3.5 | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.Unity | Набор средств Visual Studio для Unity | 15.7.27617.1 | Обязательное значение
Component.UnityEngine.x64 | Редактор Unity 2018.3 (64-разрядный) | 15.9.28307.271 | Рекомендованное
Component.UnityEngine.x86 | Редактор Unity 5.6 (32-разрядный) | 15.6.27406.0 | Рекомендованное

## <a name="linux-development-with-c"></a>Разработка приложений для Linux на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Описание.** Создание и отладка приложений, запускаемых в среде Linux.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.MDD.Linux | Visual C++ для разработки в среде Linux | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 15.6.27406.0 | Обязательное значение
Component.Linux.CMake | Инструменты Visual C++ для CMake и Linux | 15.9.28307.102 | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 15.9.28307.102 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Рекомендованное
Component.MDD.Linux.GCC.arm | Разработка для встроенных платформ и Интернета вещей | 15.6.27309.0 | Необязательный

## <a name="desktop-development-with-c"></a>Разработка классических приложений на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeDesktop

**Описание.** Создание классических приложений Windows с помощью набора инструментов Microsoft C++, ATL или MFC.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Распространяемый компонент Visual C++ 2017 с обновлением | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Основные возможности Visual C++ для классических приложений | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 15.0.27005.2 | Рекомендованное
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.Graphics.Win81 | Пакет SDK графических инструментов для Windows 8.1 | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL для x86 и x64 | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Component.VC.CMake.Project | Инструменты Visual C++ для CMake | 15.9.28307.102 | Рекомендованное
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 15.0.26823.1 | Рекомендованное
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Адаптер теста для Boost.Test | 15.8.27906.1 | Рекомендованное
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Адаптер тестов для Google Test | 15.8.27906.1 | Рекомендованное
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 15.9.28307.102 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Рекомендованное
Component.Incredibuild | IncrediBuild — ускорение сборки | 15.7.27617.1 | Необязательный
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Необязательный
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 15.6.27309.0 | Необязательный
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.VC.140 | Набор инструментов VC++ 2015.3 v14.00 (v140) для ПК | 15.7.27617.1 | Необязательный
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC для x86 и x64 | 15.7.27625.0 | Необязательный
Microsoft.VisualStudio.Component.VC.CLI.Support | Поддержка C++/CLI | 15.6.27309.0 | Необязательный
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Модули для стандартной библиотеки (экспериментальная версия) | 15.6.27309.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Пакет SDK для Windows 10 (10.0.15063.0) для Desktop C++ x86 и x64 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C#, VB, JS | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) для Desktop C++ [x86 и x64] | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Пакет SDK для Windows 10 (10.0.16299.0) для Desktop C++ [ARM и ARM64] | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C#, VB, JS | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.Component.Windows81SDK | Пакет SDK для Windows 8.1 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.WinXP | Поддержка Windows XP для C++ | 15.8.27924.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Пакеты SDK для Windows 8.1 и UCRT | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Поддержка Windows XP для C++ | 15.8.27705.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Пакет SDK для Windows 10 (10.0.15063.0) | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 15.8.27825.0 | Необязательный

## <a name="game-development-with-c"></a>Разработка игр на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeGame

**Описание.** Используйте все возможности C++ для создания профессиональных игр на базе DirectX, Unreal или Cocos2D.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Распространяемый компонент Visual C++ 2017 с обновлением | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Обязательное значение
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.Graphics.Win81 | Пакет SDK графических инструментов для Windows 8.1 | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 15.0.26823.1 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 15.9.28307.102 | Рекомендованное
Component.Android.NDK.R12B | Пакет NDK для Android (R12B) | 12.1.10 | Необязательный
Component.Android.SDK23.Private | Установка пакета SDK для Android (уровень API 23) (локальная установка для разработки мобильных приложений на JavaScript или C++) | 15.9.28016.0 | Необязательный
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Необязательный
Component.Cocos | Cocos | 15.0.26906.1 | Необязательный
Component.Incredibuild | IncrediBuild — ускорение сборки | 15.7.27617.1 | Необязательный
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Необязательный
Component.MDD.Android | Средства разработки на C++ для Android | 15.0.26606.0 | Необязательный
Component.OpenJDK | Дистрибутив OpenJDK от Майкрософт | 15.9.28125.51 | Необязательный
Component.Unreal | Установщик Unreal Engine | 15.8.27729.1 | Необязательный
Component.Unreal.Android | Поддержка Visual Studio Android для Unreal Engine | 15.9.28307.341 | Необязательный
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 15.6.27309.0 | Необязательный
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Необязательный
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.9.28016.0 | Необязательный
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Необязательный
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Пакет SDK для Windows 10 (10.0.15063.0) для Desktop C++ x86 и x64 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C#, VB, JS | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) для Desktop C++ [x86 и x64] | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Пакет SDK для Windows 10 (10.0.16299.0) для Desktop C++ [ARM и ARM64] | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C#, VB, JS | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.Component.Windows81SDK | Пакет SDK для Windows 8.1 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Пакеты SDK для Windows 8.1 и UCRT | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Пакет SDK для Windows 10 (10.0.15063.0) | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 15.8.27825.0 | Необязательный

## <a name="mobile-development-with-c"></a>Разработка мобильных приложений на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeMobile

**Описание.** Создание межплатформенных приложений для iOS, Android или Windows на С++.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Android.SDK19.Private | Установка пакета SDK для Android (уровень API 19) (локальная установка для разработки мобильных приложений на JavaScript или C++) | 15.9.28107.0 | Обязательное значение
Component.Android.SDK21.Private | Установка пакета SDK для Android (уровень API 21) (локальная установка для разработки мобильных приложений на JavaScript или C++) | 15.9.28016.0 | Обязательное значение
Component.Android.SDK22.Private | Установка пакета SDK для Android (уровень API 22) (локальная установка для разработки мобильных приложений на JavaScript или C++) | 15.9.28016.0 | Обязательное значение
Component.Android.SDK23.Private | Установка пакета SDK для Android (уровень API 23) (локальная установка для разработки мобильных приложений на JavaScript или C++) | 15.9.28016.0 | Обязательное значение
Component.Android.SDK25.Private | Установка пакета SDK для Android (уровень API 25) (локальная установка для разработки мобильных приложений на JavaScript или C++) | 15.9.28016.0 | Обязательное значение
Component.OpenJDK | Дистрибутив OpenJDK от Майкрософт | 15.9.28125.51 | Обязательное значение
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | 15.6.27406.0 | Обязательное значение
Component.Android.NDK.R15C | Пакет NDK для Android (R15C) | 15.2.1 | Рекомендованное
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Рекомендованное
Component.MDD.Android | Средства разработки на C++ для Android | 15.0.26606.0 | Рекомендованное
Component.Android.NDK.R12B | Пакет NDK для Android (R12B) | 12.1.10 | Необязательный
Component.Android.NDK.R12B_3264 | Пакет NDK для Android (R12B) (32-разрядная версия) | 12.1.11 | Необязательный
Component.Android.NDK.R13B | Пакет NDK для Android (R13B) | 13.1.7 | Необязательный
Component.Android.NDK.R13B_3264 | Пакет NDK для Android (R13B) (32-разрядная версия) | 13.1.8 | Необязательный
Component.Android.NDK.R15C_3264 | Пакет NDK для Android (R15C) (32-разрядная версия) | 15.2.1 | Необязательный
Component.Google.Android.Emulator.API23.Private | Google Android Emulator (уровень API 23), локальная установка | 15.6.27413.0 | Необязательный
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM), локальная установка | 15.9.28307.421 | Необязательный
Component.Incredibuild | IncrediBuild — ускорение сборки | 15.7.27617.1 | Необязательный
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Необязательный
Component.MDD.IOS | Средства разработки C++ для iOS | 15.0.26621.2 | Необязательный

## <a name="net-core-cross-platform-development"></a>Кроссплатформенная разработка .NET Core

**Идентификатор:** Microsoft.VisualStudio.Workload.NetCoreTools

**Описание.** Создание кроссплатформенных приложений с помощью .NET Core, ASP.NET Core, HTML, JavaScript и контейнеров, включая поддержку Docker.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 15.0.26720.2 | Обязательное значение
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 15.8.27705.0 | Обязательно
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Обязательное значение
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательное значение
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательное значение
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.NetCore.ComponentGroup.Web.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 15.8.27906.1 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Средства разработки для контейнеров — средства сборки | 15.7.27617.1 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Поддержка языка F# для веб-проектов | 15.9.28307.421 | Обязательное значение
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательное значение
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 15.0.26621.2 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 15.7.27617.1 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.NCLI | собственный клиент SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Обязательное значение
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательное значение
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 15.9.28219.51 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Обязательное значение
Component.Microsoft.VisualStudio.Web.AzureFunctions | Средства веб-заданий Microsoft Azure | 15.7.27617.1 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 15.8.27825.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 15.9.28307.421 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 15.9.28307.421 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 15.9.28125.51 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 15.8.27825.0 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Средства веб-заданий Microsoft Azure | 15.7.27617.1 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Облачные средства для веб-разработки | 15.8.27729.1 | Рекомендованное
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 2.0 | 15.6.27406.0 | Необязательный
Microsoft.Net.Core.Component.SDK.1x | Средства разработки .NET Core 1.0–1.1 | 15.6.27406.0 | Необязательный
Microsoft.NetCore.1x.ComponentGroup.Web | Средства разработки .NET Core 1.0–1.1 для веб-приложений | 15.6.27406.0 | Необязательный
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Средства разработки .NET Core 2.0 | 15.8.27729.1 | Необязательный
Microsoft.NetCore.ComponentGroup.Web | Средства разработки .NET Core 2.0 | 15.7.27625.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Поддержка времени разработки в IIS | 15.9.28219.51 | Необязательный

## <a name="mobile-development-with-net"></a>Разработка мобильных приложений на платформе .NET

**Идентификатор:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Описание.** Создание кроссплатформенных приложений для iOS, Android или Windows с помощью Xamarin.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Xamarin | Xamarin | 15.8.27906.1 | Обязательное значение
Component.Xamarin.RemotedSimulator | Симулятор удаленной работы для Xamarin | 15.6.27323.2 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательное значение
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 2.0 | 15.6.27406.0 | Обязательное значение
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Средства разработки .NET Core 2.0 | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.Merq | Внутренние средства Common Xamarin | 15.8.27924.0 | Обязательное значение
Microsoft.VisualStudio.Component.MonoDebugger | Отладчик Mono | 15.0.26720.2 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательное значение
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Модуль создания шаблонов ASP.NET | 15.8.27729.1 | Обязательное значение
Component.Android.SDK27 | Программа установки пакета SDK для Android (уровень API 27) | 15.9.28016.0 | Рекомендуется
Component.Google.Android.Emulator.API27 | Google Android Emulator (уровень API 27) | 15.9.28307.421 | Рекомендованное
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM), глобальная установка | 15.9.28307.421 | Рекомендованное
Component.OpenJDK | Дистрибутив OpenJDK от Майкрософт | 15.9.28125.51 | Рекомендованное
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26606.0 | Необязательный
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Необязательный
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 15.8.27729.1 | Необязательный
Microsoft.VisualStudio.Component.Graphics | Редакторы изображений и трехмерных моделей | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Средства универсальной платформы Windows для Xamarin | 15.9.28307.102 | Необязательный

## <a name="aspnet-and-web-development"></a>ASP.NET и веб-разработка

**Идентификатор:** Microsoft.VisualStudio.Workload.NetWeb

**Описание.** Создание веб-приложений с помощью ASP.NET, ASP.NET Core, HTML/JavaScript и контейнеров, включая поддержку Docker.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 15.0.26720.2 | Обязательное значение
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 15.8.27705.0 | Обязательно
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Обязательное значение
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательное значение
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательное значение
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.NetCore.ComponentGroup.Web.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 15.8.27906.1 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Средства разработки для контейнеров — средства сборки | 15.7.27617.1 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Поддержка языка F# для веб-проектов | 15.9.28307.421 | Обязательное значение
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательное значение
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 15.0.26621.2 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 15.7.27617.1 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.NCLI | собственный клиент SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Обязательное значение
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательное значение
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 15.9.28219.51 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Обязательное значение
Component.Microsoft.VisualStudio.Web.AzureFunctions | Средства веб-заданий Microsoft Azure | 15.7.27617.1 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 15.8.27825.0 | Рекомендованное
Microsoft.VisualStudio.Component.AspNet45 | Дополнительные возможности ASP.NET | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 15.9.28307.421 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 15.9.28307.421 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 15.9.28125.51 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.EntityFramework | Инструменты для Entity Framework 6 | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Средства веб-заданий Microsoft Azure | 15.7.27617.1 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Облачные средства для веб-разработки | 15.8.27729.1 | Рекомендованное
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 15.8.27825.0 | Необязательный
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 15.8.27825.0 | Необязательный
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Средства разработки для .NET Framework 4.7.2 | 15.8.27825.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 15.6.27406.0 | Необязательный
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 2.0 | 15.6.27406.0 | Необязательный
Microsoft.Net.Core.Component.SDK.1x | Средства разработки .NET Core 1.0–1.1 | 15.6.27406.0 | Необязательный
Microsoft.NetCore.1x.ComponentGroup.Web | Средства разработки .NET Core 1.0–1.1 для веб-приложений | 15.6.27406.0 | Необязательный
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Средства разработки .NET Core 2.0 | 15.8.27729.1 | Необязательный
Microsoft.NetCore.ComponentGroup.Web | Средства разработки .NET Core 2.0 | 15.7.27625.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Поддержка времени разработки в IIS | 15.9.28219.51 | Необязательный
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | Необязательный

## <a name="nodejs-development"></a>Разработка Node.js

**Идентификатор:** Microsoft.VisualStudio.Workload.Node

**Описание.** Создание масштабируемых сетевых приложений при помощи Node.js, асинхронной среды выполнения JavaScript с управлением на основе событий. 

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Обязательное значение
Microsoft.VisualStudio.Component.Node.Build | Поддержка MSBuild в Node.js | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.Node.Tools | Поддержка разработки Node.js | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательное значение
Microsoft.VisualStudio.Component.TestTools.Core | Основные компоненты средств тестирования | 15.7.27520.0 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Необязательный
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Необязательный

## <a name="officesharepoint-development"></a>Разработка для Office и SharePoint

**Идентификатор:** Microsoft.VisualStudio.Workload.Office

**Описание.** Создание надстроек для Office 365 и SharePoint, решений SharePoint и надстроек VSTO на C#, VB и JavaScript.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 15.0.26720.2 | Обязательное значение
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 15.8.27705.0 | Обязательно
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Обязательное значение
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательное значение
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательное значение
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 15.8.27906.1 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Средства разработки для контейнеров — средства сборки | 15.7.27617.1 | Обязательное значение
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Средства разработки классических приложений .NET | 15.7.27625.0 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательное значение
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.Sharepoint.Tools | Инструменты разработчика Office для Visual Studio | 15.8.27924.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 15.0.26621.2 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 15.7.27617.1 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.NCLI | собственный клиент SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Обязательное значение
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательное значение
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Обязательное значение
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 15.9.28219.51 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.TeamOffice | Набор средств Visual Studio для Office (VSTO) | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 15.8.27825.0 | Необязательный
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 15.8.27825.0 | Необязательный
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Средства разработки для .NET Framework 4.7.2 | 15.8.27825.0 | Необязательный
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 15.6.27406.0 | Необязательный

## <a name="python-development"></a>Разработка на Python

**Идентификатор:** Microsoft.VisualStudio.Workload.Python

**Описание.** Редактирование, отладка, интерактивная разработка и система управления версиями для Python.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.PythonTools | Поддержка языка Python | 15.0.26823.1 | Обязательное значение
Component.CPython3.x64 | 64-разрядная версия Python 3 (3.6.6) | 3.6.6 | Рекомендуется
Microsoft.Component.CookiecutterTools | Поддержка шаблонов Cookiecutter | 15.0.26621.2 | Рекомендованное
Microsoft.Component.PythonTools.Web | Поддержка веб-приложений Python | 15.9.28107.0 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Рекомендуется
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Рекомендованное
Component.Anaconda2.x64 | 64-разрядная версия Anaconda2 (5.2.0) | 5.2.0 | Необязательный
Component.Anaconda2.x86 | 32-разрядная версия Anaconda2 (5.2.0) | 5.2.0 | Необязательный
Component.Anaconda3.x64 | 64-разрядная версия Anaconda3 (5.2.0) | 5.2.0 | Необязательный
Component.Anaconda3.x86 | 32-разрядная версия Anaconda3 (5.2.0) | 5.2.0 | Необязательный
Component.CPython2.x64 | 64-разрядная версия Python 2 (2.7.14) | 2.7.14 | Необязательный
Component.CPython2.x86 | 32-разрядная версия Python 2 (2.7.14) | 2.7.14 | Необязательный
Component.CPython3.x86 | 32-разрядная версия Python 3 (3.6.6) | 3.6.6 | Необязательный
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 15.0.26720.2 | Необязательный
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 15.8.27705.0 | Необязательный
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Необязательный
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Необязательный
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Необязательный
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Необязательный
Microsoft.Component.PythonTools.UWP | Поддержка Интернета вещей для Python | 15.0.26606.0 | Необязательный
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 15.6.27309.0 | Необязательный
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Встроенные средства разработки Python | 15.9.28307.102 | Необязательный
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Необязательный
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Необязательный
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Необязательный
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 15.9.28307.421 | Необязательный
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 15.9.28307.421 | Необязательный
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 15.9.28125.51 | Необязательный
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | 15.9.28107.0 | Необязательный
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 15.7.27617.1 | Необязательный
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 15.8.27729.1 | Необязательный
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 15.8.27906.1 | Необязательный
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Средства разработки для контейнеров — средства сборки | 15.7.27617.1 | Необязательный
Microsoft.VisualStudio.Component.Graphics | Редакторы изображений и трехмерных моделей | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Graphics.Win81 | Пакет SDK графических инструментов для Windows 8.1 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Необязательный
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 15.8.27729.1 | Необязательный
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Необязательный
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Необязательный
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Необязательный
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Необязательный
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 15.0.26621.2 | Необязательный
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 15.7.27617.1 | Необязательный
Microsoft.VisualStudio.Component.SQL.NCLI | собственный клиент SQL Server | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Необязательный
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.VC.140 | Набор инструментов VC++ 2015.3 v14.00 (v140) для ПК | 15.7.27617.1 | Необязательный
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 15.0.26823.1 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Необязательный
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.Component.Windows81SDK | Пакет SDK для Windows 8.1 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 15.9.28219.51 | Необязательный

## <a name="universal-windows-platform-development"></a>Разработка с помощью универсальной платформы Windows

**Идентификатор:** Microsoft.VisualStudio.Workload.Universal

**Описание.** Создание приложений для универсальной платформы Windows с помощью C#, VB, JavaScript или C++.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Обязательное значение
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Обязательное значение
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Обязательное значение
Microsoft.ComponentGroup.Blend | Blend для Visual Studio | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательное значение
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.Graphics | Редакторы изображений и трехмерных моделей | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательное значение
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательное значение
Microsoft.VisualStudio.Component.UWP.Support | Средства универсальной платформы Windows | 15.9.28119.51 | Обязательно
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Обязательное значение
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 15.9.28307.102 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Средства универсальной платформы Windows для Cordova | 15.9.28307.102 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native и .NET Standard | 15.8.27906.1 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Средства универсальной платформы Windows для Xamarin | 15.9.28307.102 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Обязательное значение
Microsoft.Component.VC.Runtime.OSSupport | Среда выполнения Visual C++ для UWP | 15.6.27406.0 | Необязательный
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Graphics.Win81 | Пакет SDK графических инструментов для Windows 8.1 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Эмулятор мобильных устройств с ОС Windows 10 (Fall Creators Update) | 15.0.27406.0 | Необязательный
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Средства универсальной платформы Windows C++ для ARM64 | 15.0.28125.51 | Необязательный
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.ARM | Компиляторы и библиотеки Visual C++ для ARM | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Компиляторы и библиотеки Visual C++ для ARM64 | 15.9.28230.55 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Пакет SDK для Windows 10 (10.0.15063.0) для Desktop C++ x86 и x64 | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C#, VB, JS | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) для Desktop C++ [x86 и x64] | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Пакет SDK для Windows 10 (10.0.16299.0) для Desktop C++ [ARM и ARM64] | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C#, VB, JS | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Подключение USB-устройств | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Средства универсальной платформы Windows для C++ | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Пакет SDK для Windows 10 (10.0.15063.0) | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 15.8.27825.0 | Необязательный

## <a name="visual-studio-extension-development"></a>Разработка расширений Visual Studio

**Идентификатор:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Описание.** Создавайте надстройки и расширения для Visual Studio, включая новые команды, анализаторы кода и окна инструментов.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательное значение
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательное значение
Microsoft.VisualStudio.Component.VSSDK | SDK для Visual Studio | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Необходимые компоненты для разработки расширений Visual Studio | 15.7.27625.0 | Обязательное значение
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Рекомендованное
Component.Dotfuscator | PreEmptive Protection — Dotfuscator | 15.0.26208.0 | Необязательный
Microsoft.Component.CodeAnalysis.SDK | Пакет SDK для .NET Compiler Platform | 15.0.27729.1 | Необязательный
Microsoft.Component.VC.Runtime.OSSupport | Среда выполнения Visual C++ для UWP | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.DslTools | Пакет SDK для моделирования | 15.0.27005.2 | Необязательный
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL для x86 и x64 | 15.7.27625.0 | Необязательный
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC для x86 и x64 | 15.7.27625.0 | Необязательный
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Необязательный

## <a name="mobile-development-with-javascript"></a>Разработка мобильных приложений на языке JavaScript

**Идентификатор.** Microsoft.VisualStudio.Workload.WebCrossPlat

**Описание.** Разработка приложений Android, iOS и UWP с помощью средств для Apache Cordova.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Набор инструментов Cordova 6.3.1 | 15.7.27625.0 | Обязательное значение
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Обязательное значение
Microsoft.VisualStudio.Component.Cordova | Основные компоненты для разработки мобильных приложений на JavaScript | 15.0.26606.0 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript ProjectSystem и общий инструментарий | 15.0.26606.0 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 15.9.28125.51 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.2.3 | Пакет SDK для TypeScript 2.3 | 15.8.27729.1 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.8.27825.0 | Обязательное значение
Component.Android.SDK23.Private | Установка пакета SDK для Android (уровень API 23) (локальная установка для разработки мобильных приложений на JavaScript или C++) | 15.9.28016.0 | Необязательный
Component.Google.Android.Emulator.API23.Private | Google Android Emulator (уровень API 23), локальная установка | 15.6.27413.0 | Необязательный
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM), локальная установка | 15.9.28307.421 | Необязательный
Component.OpenJDK | Дистрибутив OpenJDK от Майкрософт | 15.9.28125.51 | Необязательный
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Необязательный
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 15.8.27825.0 | Необязательный
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 15.8.27729.1 | Необязательный
Microsoft.VisualStudio.Component.Git | Git для Windows | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.Graphics | Редакторы изображений и трехмерных моделей | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Эмулятор мобильных устройств с ОС Windows 10 (Fall Creators Update) | 15.0.27406.0 | Необязательный
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Необязательный
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 15.9.28307.102 | Необязательный
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Средства универсальной платформы Windows для Cordova | 15.9.28307.102 | Необязательный

## <a name="unaffiliated-components"></a>Самостоятельные компоненты

Здесь перечислены компоненты, которые не используются рабочими нагрузками, но могут быть выбраны в качестве отдельного компонента.

Идентификатор компонента | name | Версия
--- | --- | ---
Component.Android.Emulator | Эмулятор Visual Studio для Android | 15.6.27413.0
Component.Android.NDK.R11C | Пакет NDK для Android (R11C) | 11.3.14
Component.Android.NDK.R11C_3264 | Пакет NDK для Android (R11C) (32-разрядная версия) | 11.3.16
Component.Android.SDK23 | Программа установки пакета SDK для Android (уровень API 23), глобальная установка | 15.9.28107.0
Component.Android.SDK25 | Программа установки пакета SDK для Android (уровень API 25) | 15.9.28107.0
Component.GitHub.VisualStudio | Расширение GitHub для Visual Studio | 2.5.2.2500
Component.Google.Android.Emulator.API23.V2 | Google Android Emulator (уровень API 23), глобальная установка | 15.6.27413.0
Component.Google.Android.Emulator.API25 | Google Android Emulator (уровень API 25) | 15.7.27604.0
Microsoft.Component.Blend.SDK.WPF | Blend для пакета SDK для Visual Studio для .NET | 15.6.27406.0
Microsoft.Component.HelpViewer | Help Viewer | 15.9.28307.421
Microsoft.VisualStudio.Component.DependencyValidation.Community | Проверка зависимостей | 15.0.26208.0
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | 15.0.27005.2
Microsoft.VisualStudio.Component.LinqToSql | Инструменты LINQ to SQL | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator | Эмулятор Windows 10 Mobile (Anniversary Edition) | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Эмулятор мобильных устройств с ОС Windows 10 (Creators Update) | 15.6.27406.0
Microsoft.VisualStudio.Component.Runtime.Node.x86.6.4.0 | Среда выполнения для компонентов на основе Node.js версии 6.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.Runtime.Node.x86.7.4.0 | Среда выполнения для компонентов на основе Node.js версии 7.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.TypeScript.2.0 | Пакет SDK для TypeScript 2.0 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | Пакет SDK для TypeScript 2.2 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | Пакет SDK для TypeScript 2.5 | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | Пакет SDK для TypeScript 2.6 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | Пакет SDK для TypeScript 2.7 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | Пакет SDK для TypeScript 2.8 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | Пакет SDK для TypeScript 2.9 | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | Пакет SDK для TypeScript 3.0 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | Visual C++ ATL для ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL для ARM с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL для ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL для ARM64 с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86 или x64) с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC для x86 или x64 с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (экспериментальная версия) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++ MFC для ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC для ARM с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++ MFC для ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Поддержка Visual C++ MFC для ARM64 с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | Библиотеки версии 14.16 для VC++ 2017 версии 15.9 для Spectre (ARM) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | Библиотеки версии 14.16 для VC++ 2017 версии 15.9 для Spectre (ARM64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | Библиотеки версии 14.16 для VC++ 2017 версии 15.9 для Spectre (x86 и x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Набор инструментов v14.11 для VC++ 2017 версии 15.4 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Набор инструментов версии 14.12 для VC++ 2017 версии 15.5 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | Набор инструментов версии 14.13 для VC++ 2017 версии 15.6 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | Набор инструментов версии 14.14 для VC++ 2017 версии 15.7 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | Набор инструментов версии 14.15 для VC++ 2017 версии 15.8 | 15.0.28230.55
