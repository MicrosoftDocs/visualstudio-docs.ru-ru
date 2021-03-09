---
title: Идентификаторы рабочих нагрузок и компонентов для Visual Studio Enterprise 2019
titleSuffix: ''
description: Идентификаторы рабочих нагрузок и компонентов позволяют устанавливать Visual Studio с помощью командной строки. Также их можно указать в качестве зависимости в манифесте VSIX.
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 3/2/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 6a23833160c3b1c6173a605e493b979e894c1c93
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683333"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Основной редактор Visual Studio (включен в Visual Studio Enterprise 2019)

**Идентификатор:** Microsoft.VisualStudio.Workload.CoreEditor

**Описание.** Основные возможности оболочки Visual Studio, включая редактирование кода с учетом синтаксиса, управление исходным кодом и рабочими элементами.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Основной редактор Visual Studio | 16.1.28811.260 | Обязательное значение
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Начальная страница Visual Studio для пользователей C++ | 16.0.28315.86 | Необязательный

## <a name="azure-development"></a>Разработка для Azure

**Идентификатор:** Microsoft.VisualStudio.Workload.Azure

**Описание.** Пакеты SDK Azure, средства и проекты для разработки облачных приложений и создания ресурсов с помощью .NET Core и .NET Framework. Также включает в себя средства для упаковки приложения в контейнер, включая поддержку Docker.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.9.31004.209 | Обязательное значение
Component.Microsoft.VisualStudio.Web.AzureFunctions | Средства веб-заданий Azure | 16.9.31004.209 | Обязательное значение
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.9.31004.209 | Обязательно
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Динамический просмотр веб-содержимого | 0.4.12.14637 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Обязательное значение
Microsoft.ComponentGroup.ClickOnce.Publish | Публикация ClickOnce для .NET Core  | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Обязательное значение
Microsoft.NetCore.Component.DevelopmentTools | Средства разработки .NET Core | 16.9.31004.209 | Обязательное значение
Microsoft.NetCore.Component.Runtime.3.1 | Среда выполнения .NET Core 3.1 (LTS) | 16.9.31024.58 | Обязательно
Microsoft.NetCore.Component.Runtime.5.0 | Среда выполнения .NET 5.0 | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.SDK | Пакет SDK для .NET | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.Web | Средства разработки .NET Core | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.4.29313.120 | Обязательное значение
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Поддержка языка F# для веб-проектов | 16.3.29207.166 | Обязательное значение
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.4.29318.151 | Обязательное значение
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Необходимые компоненты для разработки на базе Azure | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Средства веб-заданий Azure | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Обязательное значение
Microsoft.Component.Azure.DataLake.Tools | Средства Azure Data Lake и Stream Analytics | 16.9.31004.209 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.1 | Среда выполнения .NET Core 2.1 (LTS) | 16.9.31024.58 | Рекомендованное
Microsoft.VisualStudio.Component.AspNet45 | Дополнительные возможности ASP.NET | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Средства Visual Studio для Kubernetes | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Powershell | Azure PowerShell | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Основные инструменты Azure Resource Manager | 16.4.29409.204 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Средства Service Fabric | 16.4.29313.120 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.Snapshot | Отладчик моментальных снимков | 16.5.29813.82 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Отладчик перехода по времени | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Инструменты облачных служб Azure | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Средства Azure Resource Manager | 16.0.28528.71 | Рекомендованное
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 Targeting Pack | 16.4.29313.120 | Необязательный
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Средства разработки .NET Framework 4.6.1 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Средства разработки для .NET Framework 4.8 | 16.4.29318.151 | Необязательный
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy службы хранилища Azure | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Необязательный

## <a name="data-storage-and-processing"></a>Хранение и обработка данных

**Идентификатор:** Microsoft.VisualStudio.Workload.Data

**Описание.** Связывание, разработка и тестирование решений по обработке данных с помощью SQL Server, Azure Data Lake и Hadoop.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.9.31004.209 | Рекомендованное
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.9.31004.209 | Рекомендуемая
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Динамический просмотр веб-содержимого | 0.4.12.14637 | Рекомендованное
Microsoft.Component.Azure.DataLake.Tools | Средства Azure Data Lake и Stream Analytics | 16.9.31004.209 | Рекомендованное
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Рекомендованное
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Рекомендованное
Microsoft.NetCore.Component.Runtime.3.1 | Среда выполнения .NET Core 3.1 (LTS) | 16.9.31024.58 | Рекомендуется
Microsoft.NetCore.Component.Runtime.5.0 | Среда выполнения .NET 5.0 | 16.9.31024.58 | Рекомендованное
Microsoft.NetCore.Component.SDK | Пакет SDK для .NET | 16.9.31024.58 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.4.29313.120 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.4.29409.204 | Рекомендованное
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.4.29409.204 | Рекомендованное
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.4.29318.151 | Рекомендованное
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Рекомендованное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Рекомендованное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.FSharp.Desktop | Поддержка языка F# для классических приложений | 16.0.28315.86 | Необязательный

## <a name="data-science-and-analytical-applications"></a>Приложения для обработки и анализа данных и аналитические приложения

**Идентификатор:** Microsoft.VisualStudio.Workload.DataScience

**Описание.** Языки и средства для создания приложений для обработки и анализа данных, включая Python и F#.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.PythonTools | Поддержка языка Python | 16.5.29515.121 | Рекомендованное
Microsoft.Component.PythonTools.Minicondax64 | Python Miniconda | 16.2.29003.222 | Рекомендованное
Microsoft.Component.PythonTools.Web | Поддержка веб-приложений Python | 16.9.31004.209 | Рекомендованное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.4.29409.204 | Рекомендованное
Microsoft.VisualStudio.Component.FSharp.Desktop | Поддержка языка F# для классических приложений | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Рекомендуемая
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Рекомендованное
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Встроенные средства разработки Python | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 16.5.29515.121 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64/x86 (последняя версия) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 16.4.29409.204 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Пакет SDK для Windows 10 (10.0.19041.0) | 16.9.31004.209 | Необязательный

## <a name="net-desktop-development"></a>Разработка классических приложений .NET

**Идентификатор:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Описание.** Сборка приложений WPF, Windows Forms и консольных приложений на C#, Visual Basic и F# с помощью .NET Core и .NET Framework.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Обязательное значение
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Обязательное значение
Microsoft.NetCore.Component.Runtime.3.1 | Среда выполнения .NET Core 3.1 (LTS) | 16.9.31024.58 | Обязательно
Microsoft.NetCore.Component.Runtime.5.0 | Среда выполнения .NET 5.0 | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.SDK | Пакет SDK для .NET | 16.9.31024.58 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.4.29318.151 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Средства разработки классических приложений .NET | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательное значение
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | Рекомендованное
Microsoft.ComponentGroup.Blend | Blend для Visual Studio | 16.0.28315.86 | Рекомендованное
Microsoft.ComponentGroup.ClickOnce.Publish | Публикация ClickOnce для .NET Core  | 16.9.31004.209 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.1 | Среда выполнения .NET Core 2.1 (LTS) | 16.9.31024.58 | Рекомендованное
Microsoft.NetCore.Component.DevelopmentTools | Средства разработки .NET Core | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.4.29409.204 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.DotNetModelBuilder | Построитель моделей ML.NET (предварительная версия) | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.EntityFramework | Инструменты для Entity Framework 6 | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Рекомендованное
Component.Dotfuscator | PreEmptive Protection — Dotfuscator | 16.0.28528.71 | Необязательный
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.9.31004.209 | Необязательный
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.9.31004.209 | Необязательно
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Динамический просмотр веб-содержимого | 0.4.12.14637 | Необязательный
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 Targeting Pack | 16.4.29313.120 | Необязательный
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Средства разработки .NET Framework 4.6.1 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Средства разработки для .NET Framework 4.8 | 16.4.29318.151 | Необязательный
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | 16.0.28528.71 | Необязательный
Microsoft.VisualStudio.Component.CodeClone | Клон кода | 16.4.29409.204 | Необязательный
Microsoft.VisualStudio.Component.CodeMap | Представление кода | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Динамическая проверка зависимостей | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.4.29409.204 | Необязательный
Microsoft.VisualStudio.Component.FSharp.Desktop | Поддержка языка F# для классических приложений | 16.0.28315.86 | Необязательный
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Необязательный
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Необязательный
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Необязательный
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Необязательный
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Инструменты архитектуры и анализа | 16.5.29514.35 | Необязательный
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Средство упаковки MSIX | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.9.31004.209 | Необязательный

## <a name="game-development-with-unity"></a>Разработка игр с помощью Unity

**Идентификатор:** Microsoft.VisualStudio.Workload.ManagedGame

**Описание.** Создание двухмерных и трехмерных игр с помощью Unity, мощной кроссплатформенной среды разработки.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Средства разработки для .NET Framework 3.5 | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Unity | Набор средств Visual Studio для Unity | 16.0.28315.86 | Обязательное значение
Component.UnityEngine.x64 | Unity Hub | 16.9.31004.209 | Рекомендованное
Component.UnityEngine.x86 | Редактор Unity 5.6 (32-разрядный) | 16.1.28811.260 | Рекомендованное

## <a name="linux-development-with-c"></a>Разработка приложений для Linux на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Описание.** Создание и отладка приложений, запускаемых в среде Linux.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.MDD.Linux | Разработка на C++ для Linux | 16.5.29515.121 | Обязательное значение
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.9.31004.209 | Обязательное значение
Component.Linux.CMake | Средства CMake C++ для Linux | 16.2.29003.222 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Рекомендованное
Component.MDD.Linux.GCC.arm | Средства разработки для встроенных платформ и Интернета вещей | 16.5.29515.121 | Необязательный

## <a name="desktop-development-with-c"></a>Разработка классических приложений на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeDesktop

**Описание.** Создание современных приложений для Windows на C++ с помощью выбранных вами средств, включая MSVC, Clang, CMake и MSBuild.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Обязательное значение
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | 16.0.28528.71 | Обязательное значение
Microsoft.VisualStudio.Component.CodeMap | Представление кода | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Обновление для распространяемого компонента C++ 2019 | 16.5.29515.121 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Инструменты разработки архитектуры для C++ | 16.0.28621.142 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Основные возможности C++ для классических приложений | 16.2.29012.281 | Обязательное значение
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Рекомендуемая
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.VC.ATL | ATL C++ для средств сборки последней версии 142 (x86 и x64) | 16.4.29313.120 | Рекомендованное
Microsoft.VisualStudio.Component.VC.CMake.Project | Средства CMake C++ для Windows | 16.3.29103.31 | Рекомендованное
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Адаптер теста для Boost.Test | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Адаптер тестов для Google Test | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64/x86 (последняя версия) | 16.9.31004.209 | Рекомендуемая
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Пакет SDK для Windows 10 (10.0.19041.0) | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.CMake | Редактор JSON | 16.9.31004.209 | Рекомендованное
Component.Incredibuild | IncrediBuild — ускорение сборки | 16.5.29721.120 | Необязательный
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Необязательный
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 16.0.28625.61 | Необязательный
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Необязательный
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.VC.140 | MSVC версии 140 — средства сборки C++ VS 2015 (версия 14.00) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC C++ для средств сборки последней версии 142 (x86 и x64) | 16.4.29313.120 | Необязательный
Microsoft.VisualStudio.Component.VC.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (последняя версия) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Компилятор Clang C++ для Windows (11.0.0) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | C++ Clang-cl для средств сборки версии 142 (x64/x86) | 16.3.29207.166 | Необязательный
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Модули C++ для средств сборки версии 142 (x64 или x86 — экспериментальная) | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC версии 141 — средства сборки C++ для VS 2017 для 64- или 32-разрядных систем (версия 14.16) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Пакет SDK для Windows 10 (10.0.18362.0) | 16.1.28829.92 | Необязательный
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | Средства Clang C++ для Windows (11.0.0 — x64/x86) | 16.9.31004.209 | Необязательный

## <a name="game-development-with-c"></a>Разработка игр на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeGame

**Описание.** Используйте все возможности C++ для создания профессиональных игр на базе DirectX, Unreal или Cocos2D.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Обновление для распространяемого компонента C++ 2019 | 16.5.29515.121 | Обязательное значение
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64/x86 (последняя версия) | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Пакет SDK для Windows 10 (10.0.19041.0) | 16.9.31004.209 | Рекомендованное
Component.Android.NDK.R16B | NDK для Android (R16B) | 16.9.31023.347 | Необязательный
Component.Android.SDK25.Private | Установка пакета SDK для Android (уровень API 25) (локальная установка для разработки мобильных приложений на C++) | 16.0.28625.61 | Необязательный
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Необязательный
Component.Cocos | Cocos | 16.0.28315.86 | Необязательный
Component.Incredibuild | IncrediBuild — ускорение сборки | 16.5.29721.120 | Необязательный
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Необязательный
Component.MDD.Android | Средства разработки на C++ для Android | 16.0.28517.75 | Необязательный
Component.OpenJDK | OpenJDK (дистрибутив от Майкрософт) | 16.1.28811.260 | Необязательный
Component.Unreal | Установщик Unreal Engine | 16.1.28810.153 | Необязательный
Component.Unreal.Android | Поддержка IDE Android для Unreal Engine | 16.1.28810.153 | Необязательный
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Необязательный
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Необязательный
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 16.1.28829.92 | Необязательный
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Необязательный
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Пакет SDK для Windows 10 (10.0.18362.0) | 16.1.28829.92 | Необязательный

## <a name="mobile-development-with-c"></a>Разработка мобильных приложений на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeMobile

**Описание.** Создание межплатформенных приложений для iOS, Android или Windows на С++.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Android.SDK25.Private | Установка пакета SDK для Android (уровень API 25) (локальная установка для разработки мобильных приложений на C++) | 16.0.28625.61 | Обязательное значение
Component.OpenJDK | OpenJDK (дистрибутив от Майкрософт) | 16.1.28811.260 | Обязательное значение
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.9.31004.209 | Обязательное значение
Component.Android.NDK.R16B | NDK для Android (R16B) | 16.9.31023.347 | Рекомендованное
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Рекомендованное
Component.MDD.Android | Средства разработки на C++ для Android | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Component.Android.NDK.R16B_3264 | NDK для Android (R16B) (32-разрядный) | 16.9.31023.347 | Необязательный
Component.Google.Android.Emulator.API25.Private | Google Android Emulator (уровень API 25), локальная установка | 16.1.28810.153 | Необязательный
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM), локальная установка | 16.0.28528.71 | Необязательный
Component.Incredibuild | IncrediBuild — ускорение сборки | 16.5.29721.120 | Необязательный
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Необязательный
Component.MDD.IOS | Средства разработки C++ для iOS | 16.0.28517.75 | Необязательный

## <a name="net-core-cross-platform-development"></a>Кроссплатформенная разработка .NET Core

**Идентификатор:** Microsoft.VisualStudio.Workload.NetCoreTools

**Описание.** Создание кроссплатформенных приложений с помощью .NET Core, ASP.NET Core, HTML, JavaScript и контейнеров, включая поддержку Docker.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.9.31004.209 | Обязательное значение
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.9.31004.209 | Обязательно
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Динамический просмотр веб-содержимого | 0.4.12.14637 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Обязательное значение
Microsoft.ComponentGroup.ClickOnce.Publish | Публикация ClickOnce для .NET Core  | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Обязательное значение
Microsoft.NetCore.Component.DevelopmentTools | Средства разработки .NET Core | 16.9.31004.209 | Обязательное значение
Microsoft.NetCore.Component.Runtime.3.1 | Среда выполнения .NET Core 3.1 (LTS) | 16.9.31024.58 | Обязательно
Microsoft.NetCore.Component.Runtime.5.0 | Среда выполнения .NET 5.0 | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.SDK | Пакет SDK для .NET | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.Web | Средства разработки .NET Core | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Поддержка языка F# для веб-проектов | 16.3.29207.166 | Обязательное значение
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.4.29318.151 | Обязательное значение
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Обязательное значение
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | Рекомендованное
Component.Microsoft.VisualStudio.Web.AzureFunctions | Средства веб-заданий Azure | 16.9.31004.209 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.1 | Среда выполнения .NET Core 2.1 (LTS) | 16.9.31024.58 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.4.29313.120 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.Snapshot | Отладчик моментальных снимков | 16.5.29813.82 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Отладчик перехода по времени | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.DotNetModelBuilder | Построитель моделей ML.NET (предварительная версия) | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.WslDebugging | Отладка .NET Core с использованием WSL 2. | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Средства веб-заданий Azure | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Облачные средства для веб-разработки | 16.9.31004.209 | Рекомендуемая
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Поддержка времени разработки в IIS | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Средство упаковки MSIX | 16.9.31004.209 | Необязательный

## <a name="mobile-development-with-net"></a>Разработка мобильных приложений на платформе .NET

**Идентификатор:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Описание.** Создание кроссплатформенных приложений для iOS, Android или Windows с помощью Xamarin.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (дистрибутив от Майкрософт) | 16.1.28811.260 | Обязательное значение
Component.Xamarin | Xamarin | 16.9.31004.209 | Обязательное значение
Component.Xamarin.RemotedSimulator | Симулятор удаленной работы для Xamarin | 16.9.31004.209 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Обязательное значение
Microsoft.ComponentGroup.ClickOnce.Publish | Публикация ClickOnce для .NET Core  | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Обязательное значение
Microsoft.NetCore.Component.DevelopmentTools | Средства разработки .NET Core | 16.9.31004.209 | Обязательное значение
Microsoft.NetCore.Component.Runtime.3.1 | Среда выполнения .NET Core 3.1 (LTS) | 16.9.31024.58 | Обязательно
Microsoft.NetCore.Component.Runtime.5.0 | Среда выполнения .NET 5.0 | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.SDK | Пакет SDK для .NET | 16.9.31024.58 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.Merq | Внутренние средства Common Xamarin | 16.2.29012.281 | Обязательное значение
Microsoft.VisualStudio.Component.MonoDebugger | Отладчик Mono | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Модуль создания шаблонов ASP.NET | 16.9.31004.209 | Обязательно
Component.Android.SDK30 | Установка пакета SDK для Android (уровень API 30) | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное

## <a name="aspnet-and-web-development"></a>ASP.NET и веб-разработка

**Идентификатор:** Microsoft.VisualStudio.Workload.NetWeb

**Описание.** Создание веб-приложений с помощью ASP.NET Core, ASP.NET, HTML, JavaScript и контейнеров, включая поддержку Docker.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.9.31004.209 | Обязательное значение
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.9.31004.209 | Обязательно
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Динамический просмотр веб-содержимого | 0.4.12.14637 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Обязательное значение
Microsoft.ComponentGroup.ClickOnce.Publish | Публикация ClickOnce для .NET Core  | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Обязательное значение
Microsoft.NetCore.Component.DevelopmentTools | Средства разработки .NET Core | 16.9.31004.209 | Обязательное значение
Microsoft.NetCore.Component.Runtime.3.1 | Среда выполнения .NET Core 3.1 (LTS) | 16.9.31024.58 | Обязательно
Microsoft.NetCore.Component.Runtime.5.0 | Среда выполнения .NET 5.0 | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.SDK | Пакет SDK для .NET | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.Web | Средства разработки .NET Core | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Поддержка языка F# для веб-проектов | 16.3.29207.166 | Обязательное значение
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.4.29318.151 | Обязательное значение
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Web.Client | ASP.NET и средства веб-разработки | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Обязательное значение
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | Рекомендованное
Component.Microsoft.VisualStudio.Web.AzureFunctions | Средства веб-заданий Azure | 16.9.31004.209 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.1 | Среда выполнения .NET Core 2.1 (LTS) | 16.9.31024.58 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.AspNet45 | Дополнительные возможности ASP.NET | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.4.29313.120 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.Snapshot | Отладчик моментальных снимков | 16.5.29813.82 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Отладчик перехода по времени | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.EntityFramework | Инструменты для Entity Framework 6 | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.WslDebugging | Отладка .NET Core с использованием WSL 2. | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Средства веб-заданий Azure | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Облачные средства для веб-разработки | 16.9.31004.209 | Рекомендованное
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 Targeting Pack | 16.4.29313.120 | Необязательный
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Средства разработки .NET Framework 4.6.1 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Средства разработки для .NET Framework 4.8 | 16.4.29318.151 | Необязательный
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | 16.0.28528.71 | Необязательный
Microsoft.VisualStudio.Component.CodeClone | Клон кода | 16.4.29409.204 | Необязательный
Microsoft.VisualStudio.Component.CodeMap | Представление кода | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Динамическая проверка зависимостей | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Инструменты веб-тестирования производительности и нагрузочного тестирования | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Дополнительные шаблоны проектов (предыдущие версии) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Инструменты архитектуры и анализа | 16.5.29514.35 | Необязательный
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Поддержка времени разработки в IIS | 16.9.31004.209 | Необязательный

## <a name="nodejs-development"></a>Разработка Node.js

**Идентификатор:** Microsoft.VisualStudio.Workload.Node

**Описание.** Создание масштабируемых сетевых приложений при помощи Node.js, асинхронной среды выполнения JavaScript с управлением на основе событий. 

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Node.Tools | Средства разработки для Node.js | 16.5.29515.121 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Обязательное значение
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.5.29515.121 | Необязательный
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.4.29409.204 | Необязательный
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64/x86 (последняя версия) | 16.9.31004.209 | Необязательный

## <a name="officesharepoint-development"></a>Разработка для Office и SharePoint

**Идентификатор:** Microsoft.VisualStudio.Workload.Office

**Описание.** Создание надстроек для Office 365 и SharePoint, решений SharePoint и надстроек VSTO на C#, VB и JavaScript.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.9.31004.209 | Обязательное значение
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.9.31004.209 | Обязательно
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Динамический просмотр веб-содержимого | 0.4.12.14637 | Обязательное значение
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Обязательное значение
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Обязательное значение
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Обязательное значение
Microsoft.NetCore.Component.Runtime.3.1 | Среда выполнения .NET Core 3.1 (LTS) | 16.9.31024.58 | Обязательно
Microsoft.NetCore.Component.Runtime.5.0 | Среда выполнения .NET 5.0 | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.SDK | Пакет SDK для .NET | 16.9.31024.58 | Обязательное значение
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.5.29515.121 | Обязательное значение
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.4.29318.151 | Обязательное значение
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Средства разработки классических приложений .NET | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Sharepoint.Tools | Инструменты разработчика Office для Visual Studio | 16.4.29409.204 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Обязательное значение
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Обязательное значение
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендуемая
Microsoft.VisualStudio.Component.TeamOffice | Набор средств Visual Studio для Office (VSTO) | 16.4.29409.204 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 Targeting Pack | 16.4.29313.120 | Необязательный
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Средства разработки .NET Framework 4.6.1 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 16.3.29207.166 | Необязательный
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Средства разработки для .NET Framework 4.8 | 16.4.29318.151 | Необязательный
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Необязательный

## <a name="python-development"></a>Разработка на Python

**Идентификатор:** Microsoft.VisualStudio.Workload.Python

**Описание.** Редактирование, отладка, интерактивная разработка и система управления версиями для Python.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.PythonTools | Поддержка языка Python | 16.5.29515.121 | Обязательное значение
Component.CPython3.x64 | 64-разрядная версия Python 3 (3.7.8) | 3.7.8 | Рекомендованное
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | Рекомендованное
Microsoft.Component.PythonTools.Minicondax64 | Python Miniconda | 16.2.29003.222 | Рекомендованное
Microsoft.Component.PythonTools.Web | Поддержка веб-приложений Python | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.4.29409.204 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Рекомендуемая
Microsoft.VisualStudio.Component.TypeScript.4.1 | Пакет SDK для TypeScript 4.1 | 16.0.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.9.31004.209 | Рекомендованное
Component.CPython2.x64 | 64-разрядная версия Python 2 (2.7.18) | 2.7.18.1 | Необязательный
Component.CPython2.x86 | 32-разрядная версия Python 2 (2.7.18) | 2.7.18.1 | Необязательный
Component.CPython3.x86 | 32-разрядная версия Python 3 (3.7.8) | 3.7.8 | Необязательный
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.9.31004.209 | Необязательный
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.9.31004.209 | Необязательно
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Динамический просмотр веб-содержимого | 0.4.12.14637 | Необязательный
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Необязательный
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Встроенные средства разработки Python | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Необязательный
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Необязательный
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Необязательный
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Необязательный
Microsoft.NetCore.Component.Runtime.3.1 | Среда выполнения .NET Core 3.1 (LTS) | 16.9.31024.58 | Необязательно
Microsoft.NetCore.Component.Runtime.5.0 | Среда выполнения .NET 5.0 | 16.9.31024.58 | Необязательный
Microsoft.NetCore.Component.SDK | Пакет SDK для .NET | 16.9.31024.58 | Необязательный
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Необязательный
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.4.29313.120 | Необязательный
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | 16.9.31019.194 | Необязательный
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 16.9.31019.194 | Необязательный
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.4.29409.204 | Необязательный
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Необязательный
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.4.29318.151 | Необязательный
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Необязательный
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Необязательный
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Необязательный
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Необязательный
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Необязательный
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 16.5.29515.121 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64/x86 (последняя версия) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 16.4.29409.204 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Пакет SDK для Windows 10 (10.0.19041.0) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.9.31004.209 | Необязательный

## <a name="universal-windows-platform-development"></a>Разработка с помощью универсальной платформы Windows

**Идентификатор:** Microsoft.VisualStudio.Workload.Universal

**Описание.** Вы сможете создавать приложения для универсальной платформы Windows на C#, VB или, при необходимости, на C++.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.5.29515.121 | Обязательное значение
Microsoft.ComponentGroup.Blend | Blend для Visual Studio | 16.0.28315.86 | Обязательное значение
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.NetCore.Component.Runtime.3.1 | Среда выполнения .NET Core 3.1 (LTS) | 16.9.31024.58 | Обязательно
Microsoft.NetCore.Component.Runtime.5.0 | Среда выполнения .NET 5.0 | 16.9.31024.58 | Обязательное значение
Microsoft.NetCore.Component.SDK | Пакет SDK для .NET | 16.9.31024.58 | Обязательное значение
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.5.29515.121 | Обязательное значение
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.Graphics | Редакторы изображений и трехмерных моделей | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Пакет SDK для Windows 10 (10.0.19041.0) | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Средство упаковки MSIX | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native и .NET Standard | 16.3.29102.218 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Средства универсальной платформы Windows | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Средства универсальной платформы Windows для Xamarin | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Рекомендованное
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Необязательный
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | 16.0.28528.71 | Необязательный
Microsoft.VisualStudio.Component.CodeClone | Клон кода | 16.4.29409.204 | Необязательный
Microsoft.VisualStudio.Component.CodeMap | Представление кода | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Динамическая проверка зависимостей | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Необязательный
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Поддержка универсальной платформы Windows C++ для средств сборки версии 142 (ARM64) | 16.3.29207.166 | Необязательный
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (последняя версия) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (последняя версия) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64/x86 (последняя версия) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC версии 141 — средства сборки C++ для VS 2017 для ARM (версия 14.16) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC версии 141 — средства сборки C++ для VS 2017 для ARM64 (версия 14.16) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC версии 141 — средства сборки C++ для VS 2017 для 64- или 32-разрядных систем (версия 14.16) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 16.0.28517.75 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Пакет SDK для Windows 10 (10.0.18362.0) | 16.1.28829.92 | Необязательный
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Подключение USB-устройств | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Инструменты архитектуры и анализа | 16.5.29514.35 | Необязательный
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Средства универсальной платформы Windows на C++ (версия 142) | 16.9.31004.209 | Необязательный
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Средства универсальной платформы Windows для C++ (v141) | 16.1.28810.153 | Необязательный

## <a name="visual-studio-extension-development"></a>Разработка расширений Visual Studio

**Идентификатор:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Описание.** Создавайте надстройки и расширения для Visual Studio, включая новые команды, анализаторы кода и окна инструментов.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Version | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Обязательное значение
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Обязательное значение
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.9.31004.209 | Обязательное значение
Microsoft.Net.Component.4.8.SDK | Пакет SDK для .NET Framework 4.8 | 16.4.29313.120 | Обязательное значение
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.3.29207.166 | Обязательное значение
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.1.28829.92 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательное значение
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.VSSDK | SDK для Visual Studio | 16.0.28315.86 | Обязательное значение
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Необходимые компоненты для разработки расширений Visual Studio | 16.9.31004.209 | Обязательное значение
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.9.31004.209 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Рекомендованное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Рекомендованное
Microsoft.Component.CodeAnalysis.SDK | Пакет SDK для .NET Compiler Platform | 16.2.29003.222 | Необязательный
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.5.29515.121 | Необязательный
Microsoft.VisualStudio.Component.DslTools | Пакет SDK для моделирования | 16.0.28315.86 | Необязательный

## <a name="unaffiliated-components"></a>Самостоятельные компоненты

Здесь перечислены компоненты, которые не используются рабочими нагрузками, но могут быть выбраны в качестве отдельного компонента.

Идентификатор компонента | name | Version
--- | --- | ---
Component.GitHub.VisualStudio | Расширение GitHub для Visual Studio | 2.5.9.5485
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 16.4.29409.204
Microsoft.Component.HelpViewer | Help Viewer | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | Среда выполнения .NET Core 2.2 (не поддерживается) | 16.9.31024.58
Microsoft.Net.Core.Component.SDK.3.0 | Среда выполнения .NET Core 3.0 (не поддерживается) | 16.9.31024.58
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки с .NET Core 2.1 | 16.9.31004.209
Microsoft.NetCore.ComponentGroup.Web.2.1 | Средства разработки веб-приложений с .NET Core 2.1 | 16.9.31004.209
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Установщик интеграции Azure DevOps с Office | 16.0.28625.61
Microsoft.VisualStudio.Component.Debugger.VSOnline | Отладчик для GitHub Codespaces | 16.9.31004.209
Microsoft.VisualStudio.Component.Git | Git для Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Инструменты LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Закодированный тест ИП | 16.0.28327.66
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версия 14.20) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версия 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версия 14.20) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версия 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | ATL C++ версии 14.20 для средств сборки версии 142 (для 32- и 64-разрядных систем) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | ATL C++ версии 14.20 для средств сборки версии 142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | ATL C++ версии 14.20 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | ATL C++ версии 14.20 для средств сборки версии 142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | ATL C++ версии 14.20 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | ATL C++ версии 14.20 для средств сборки версии 142 с устранением рисков Spectre (для 32- и 64-разрядных систем) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (14.20) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.20.MFC | MFC C++ версии 14.20 для средств сборки версии 142 (для 32- и 64-разрядных систем) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | MFC C++ версии 14.20 для средств сборки версии 142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | MFC C++ версии 14.20 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | MFC C++ версии 14.20 для средств сборки версии 142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | MFC C++ версии 14.20 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | MFC C++ версии 14.20 для средств сборки версии 142 с устранением рисков Spectre (для 32- и 64-разрядных систем) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для 32- и 64-разрядных систем (версия 14.20) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для 32- и 64-разрядных систем с устранением рисков Spectre (версия 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версия 14.21) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версия 14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версия 14.21) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версия 14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | ATL C++ версии 14.21 для средств сборки версии 142 (x86 и x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | ATL C++ версии 14.21 для средств сборки версии 142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | ATL C++ версии 14.21 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | ATL C++ версии 14.21 для средств сборки версии 142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | ATL C++ версии 14.21 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | ATL C++ версии 14.21 для средств сборки версии 142 с устранением рисков Spectre (x86 и x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | MFC C++ версии 14.21 для средств сборки версии 142 (x86 и x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | MFC C++ версии 14.21 для средств сборки версии 142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | MFC C++ версии 14.21 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | MFC C++ версии 14.21 для средств сборки версии 142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | MFC C++ версии 14.21 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | MFC C++ версии 14.21 для средств сборки версии 142 с устранением рисков Spectre (x86 и x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для 64- или 32-разрядных систем (версия 14.21) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для x64 или x86 с устранением рисков Spectre (версия 14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версия 14.22) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версия 14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версия 14.22) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версия 14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | ATL C++ версии 14.22 для средств сборки версии 142 (x86 и x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | ATL C++ версии 14.22 для средств сборки версии 142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | ATL C++ версии 14.22 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | ATL C++ версии 14.22 для средств сборки версии 142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | ATL C++ версии 14.22 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | ATL C++ версии 14.22 для средств сборки версии 142 с устранением рисков Spectre (x86 и x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (14.22) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.22.MFC | MFC C++ версии 14.22 для средств сборки версии 142 (x86 и x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | MFC C++ версии 14.22 для средств сборки версии 142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | MFC C++ версии 14.22 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | MFC C++ версии 14.22 для средств сборки версии 142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | MFC C++ версии 14.22 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | MFC C++ версии 14.22 для средств сборки версии 142 с устранением рисков Spectre (x86 и x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64/x86 (версия 14.22) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для x64 или x86 с устранением рисков Spectre (версия 14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версия 14.23) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версия 14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версия 14.23) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версия 14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | Библиотека ATL C++ версии 14.23 для средств сборки версии 142 (86- и 64-разрядная система) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | ATL C++ версии 14.23 для средств сборки версии 142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | ATL C++ версии 14.23 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | ATL C++ версии 14.23 для средств сборки версии 142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | ATL C++ версии 14.23 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | ATL C++ версии 14.23 для средств сборки версии 142 с устранением рисков Spectre (86- и 64-разрядная система) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (14.23) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.23.MFC | MFC C++ версии 14.23 для средств сборки версии 142 (86- и 64-разрядная система) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | MFC C++ версии 14.23 для средств сборки версии 142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | MFC C++ версии 14.23 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | MFC C++ версии 14.23 для средств сборки версии 142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | MFC C++ версии 14.23 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | MFC C++ версии 14.23 для средств сборки версии 142 с устранением рисков Spectre (86- и 64-разрядная система) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64/x86 (версия 14.23) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для x64 или x86 с устранением рисков Spectre (версия 14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версия 14.24) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версия 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версия 14.24) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версия 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | Библиотека ATL C++ версии 14.24 для средств сборки версии 142 (32- и 64-разрядная система) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | Библиотека ATL C++ версии 14.24 для средств сборки версии 142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | Библиотека ATL C++ версии 14.24 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | Библиотека ATL C++ версии 14.24 для средств сборки версии 142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | Библиотека ATL C++ версии 14.24 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | Библиотека ATL C++ версии 14.24 для средств сборки версии 142 с устранением рисков Spectre (32- и 64-разрядная система) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (14.24) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.24.MFC | MFC C++ версии 14.24 для средств сборки версии 142 (32- и 64-разрядная система) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM | MFC C++ версии 14.24 для средств сборки версии 142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM.Spectre | MFC C++ версии 14.24 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64 | MFC C++ версии 14.24 для средств сборки версии 142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64.Spectre | MFC C++ версии 14.24 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.24.MFC.Spectre | MFC C++ версии 14.24 для средств сборки версии 142 с устранением рисков Spectre (32- и 64-разрядная система) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для 64- или 86-разрядных систем (версия 14.24) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для x64 или x86 с устранением рисков Spectre (версия 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.25.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версия 14.25) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версия 14.25) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версия 14.25) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версия 14.25) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.ATL | Библиотека ATL C++ версии 14.25 для средств сборки версии 142 (системы с архитектурой x86 и x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM | Библиотека ATL C++ версии 14.25 для средств сборки версии 142 (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM.Spectre | Библиотека ATL C++ версии 14.25 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM64 | Библиотека ATL C++ версии 14.25 для средств сборки версии 142 (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM64.Spectre | Библиотека ATL C++ версии 14.25 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.ATL.Spectre | Библиотека ATL C++ версии 14.25 для средств сборки версии 142 с устранением рисков Spectre (системы с архитектурой x86 и x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (14.25) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.MFC | MFC C++ версии 14.25 для средств сборки версии 142 (системы с архитектурой x86 и x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM | MFC C++ версии 14.25 для средств сборки версии 142 (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM.Spectre | MFC C++ версии 14.25 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64 | MFC C++ версии 14.25 для средств сборки версии 142 (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64.Spectre | MFC C++ версии 14.25 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.MFC.Spectre | MFC C++ версии 14.25 для средств сборки версии 142 с устранением рисков Spectre (системы с архитектурой x86 и x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для 64- или 32-разрядных систем (версия 14.25) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.25.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для x64 или x86 с устранением рисков Spectre (версия 14.25) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версия 14.26) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версия 14.26) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версия 14.26) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версия 14.26) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ATL | Библиотека ATL C++ версии 14.26 для средств сборки версии 142 (32-разрядные и 64-разрядные системы) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM | Библиотека ATL C++ версии 14.26 для средств сборки версии 142 (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM.Spectre | Библиотека ATL C++ версии 14.26 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64 | Библиотека ATL C++ версии 14.26 для средств сборки версии 142 (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64.Spectre | Библиотека ATL C++ версии 14.26 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.ATL.Spectre | Библиотека ATL C++ версии 14.26 для средств сборки версии 142 с устранением рисков Spectre (32-разрядные и 64-разрядные системы) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (14.26) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.MFC | Библиотека MFC C++ версии 14.26 для средств сборки версии 142 (32-разрядные и 64-разрядные системы) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM | Библиотека MFC C++ версии 14.26 для средств сборки версии 142 (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM.Spectre | Библиотека MFC C++ версии 14.26 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64 | Библиотека MFC C++ версии 14.26 для средств сборки версии 142 (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64.Spectre | Библиотека MFC C++ версии 14.26 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.MFC.Spectre | Библиотека MFC C++ версии 14.26 для средств сборки версии 142 с устранением рисков Spectre (32-разрядные и 64-разрядные системы) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для систем с архитектурой x64 и x86 (версия 14.26) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.26.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для систем с архитектурой x64 и x86 с устранением рисков Spectre (версия 14.26) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версия 14.27) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версия 14.27) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версия 14.27) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версия 14.27) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ATL | Библиотека ATL C++ версии 14.27 для средств сборки версии 142 (x86 или x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM | Библиотека ATL C++ версии 14.27 для средств сборки версии 142 (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM.Spectre | Библиотека ATL C++ версии 14.27 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM64 | Библиотека ATL C++ версии 14.27 для средств сборки версии 142 (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM64.Spectre | Библиотека ATL C++ версии 14.27 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.ATL.Spectre | Библиотека ATL C++ версии 14.27 для средств сборки версии 142 с устранением рисков Spectre (x86 или x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (14.27) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.MFC | MFC C++ версии 14.27 для средств сборки версии 142 (x86 или x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM | MFC C++ версии 14.27 для средств сборки версии 142 (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM.Spectre | MFC C++ версии 14.27 для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64 | MFC C++ версии 14.27 для средств сборки версии 142 (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64.Spectre | MFC C++ версии 14.27 для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.MFC.Spectre | MFC C++ версии 14.27 для средств сборки версии 142 с устранением рисков Spectre (x86 или x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для 32-разрядных и 64-разрядных систем (версия 14.27) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.27.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для 32-разрядных и 64-разрядных системы с устранением рисков Spectre (версия 14.27) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версии 14.28–16.8) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версии 14.28–16.8) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версии 14.28–16.8) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версии 14.28–16.8) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ATL | Библиотека ATL C++ версии 14.28 (16.8) для средств сборки версии 142 (x86 или x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM | Библиотека ATL C++ версии 14.28 (16.8) для средств сборки версии 142 (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM.Spectre | Библиотека ATL C++ версии 14.28 (16.8) для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM64 | Библиотека ATL C++ версии 14.28 (16.8) для средств сборки версии 142 (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM64.Spectre | Библиотека ATL C++ версии 14.28 (16.8) для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.ATL.Spectre | Библиотека ATL C++ версии 14.28 (16.8) для средств сборки версии 142 с устранением рисков Spectre (x86 или x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 (14.28–16.8) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.MFC | MFC C++ версии 14.28 (16.8) для средств сборки версии 142 (x86 или x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM | MFC C++ версии 14.28 (16.8) для средств сборки версии 142 (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM.Spectre | MFC C++ версии 14.28 (16.8) для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM64 | MFC C++ версии 14.28 (16.8) для средств сборки версии 142 (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM64.Spectre | MFC C++ версии 14.28 (16.8) для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.MFC.Spectre | MFC C++ версии 14.28 (16.8) для средств сборки версии 142 с устранением рисков Spectre (x86/x64) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64/x86 (версии 14.28–16.8) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.28.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для x64/x86 с устранением рисков Spectre (версии 14.28–16.8) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.ATL.ARM | ATL C++ для средств сборки последней версии 142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | ATL C++ для средств сборки последней версии 142 с устранением рисков Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | ATL C++ для средств сборки последней версии 142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | ATL C++ для средств сборки последней версии 142 с устранением рисков Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.ARM64EC | Библиотека ATL C++ для средств сборки последней версии 142 (ARM64EC — экспериментальная версия) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.ATL.ARM64EC.Spectre | Библиотека ATL C++ для средств сборки последней версии 142 с устранением рисков Spectre (ARM64EC — экспериментальная версия) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.ATL.Spectre | ATL C++ для средств сборки последней версии 142 с устранением рисков Spectre (x86 и x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | MFC C++ для средств сборки последней версии 142 с устранением рисков Spectre (x86 и x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | MFC C++ для средств сборки последней версии 142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | MFC C++ для средств сборки последней версии 142 с устранением рисков Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | MFC C++ для средств сборки последней версии 142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | MFC C++ для средств сборки последней версии 142 с устранением рисков Spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64EC | MFC C++ для средств сборки последней версии 142 (ARM64EC — экспериментальная версия) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.MFC.ARM64EC.Spectre | MFC C++ для средств сборки последней версии 142 с устранением рисков Spectre (ARM64EC — экспериментальная версия) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.Redist.MSM | Распространяемые пакеты MSM C++ 2019 | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (последняя версия) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (последняя версия) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64EC.Spectre | MSVC версии 142 — библиотеки С++ для VS 2019 для ARM64EC с устранением рисков Spectre (последняя экспериментальная версия) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для x64/x86 с устранением рисков Spectre (последняя версия)  | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.Tools.ARM64EC | MSVC версии 142 — средства сборки С++ для VS 2019 для ARM64EC (последняя экспериментальная версия) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC версии 141 — библиотеки C++ для VS 2017 для ARM с устранением рисков Spectre (версия 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC версии 141 — библиотеки C++ для VS 2017 для ARM64 с устранением рисков Spectre (версия 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | ATL C++ для средств сборки версии 141 (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | ATL C++ для средств сборки версии 141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | ATL C++ для средств сборки версии 141 с устранением рисков Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | ATL C++ для средств сборки версии 141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | ATL C++ для средств сборки версии 141 с устранением рисков Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | ATL C++ для средств сборки версии 141 с устранением рисков Spectre (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | Поддержка C++/CLI для средств сборки версии 141 (14.16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | MFC C++ для средств сборки версии 141 (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | MFC C++ для средств сборки версии 141 (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | MFC C++ для средств сборки версии 141 с устранением рисков Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | MFC C++ для средств сборки версии 141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | MFC C++ для средств сборки версии 141 с устранением рисков Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | MFC C++ для средств сборки версии 141 с устранением рисков Spectre (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC версии 141 — библиотеки C++ для VS 2017 для x64 или x86 с устранением рисков Spectre (версия 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Поддержка Windows XP на C++ для инструментов VS 2017 (версия 141) [не рекомендуется] | 16.9.31004.209
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.9.31004.209
