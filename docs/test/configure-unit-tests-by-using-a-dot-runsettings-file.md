---
title: Настройка модульных тестов с помощью RUNSETTINGS-файла
description: Сведения о том, как использовать файл .runsettings в Visual Studio для настройки модульных тестов, выполняющихся из командной строки, из интегрированной среды разработки или в рабочем процессе сборки.
ms.custom: SEO-VS-2020
ms.date: 07/15/2020
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 65785384746fa3f16dd25f0405e5ead45c553c21
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221162"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Настройка модульных тестов с помощью файла *.runsettings*

Модульные тесты в Visual Studio можно настроить с помощью файла *.runsettings*. Например, можно изменить версию платформы .NET, на которой выполняются тесты, каталог для результатов теста и данные, собранные во время тестового запуска. Чаще всего файл *.runsettings* используют для настройки [анализа объема протестированного кода](../test/customizing-code-coverage-analysis.md).

Файлы параметров запуска можно использовать для настройки тестов, которые запускаются из [командной строки](vstest-console-options.md), в интегрированной среде разработки или в [рабочем процессе сборки](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true) с помощью Azure Test Plans или Team Foundation Server (TFS).

Файлы параметров запуска являются необязательными. Если вам не требуется специальная конфигурация, файл *.runsettings* не нужен.

## <a name="create-a-run-settings-file-and-customize-it"></a>Создание и настройка файла параметров запуска

1. Добавьте файл параметров запуска в решение. В **обозревателе решений** в контекстном меню выберите **Добавить** > **Новый элемент** и **XML-файл**. Сохраните файл с именем, похожим на *test.runsettings*.

   > [!TIP]
   > Имя файла не имеет значения, если вы используете расширение *.runsettings*.

2. Добавьте содержимое из [примера файла *.runsettings](#example-runsettings-file), а затем настройте его в соответствии с собственными требованиями, как описано в следующих разделах.

3. Указать нужный файл *.runsettings можно с помощью одного из следующих методов:

   - [Интегрированная среда разработки Visual Studio](#specify-a-run-settings-file-in-the-ide)
   - [командная строка;](#specify-a-run-settings-file-from-the-command-line)
   - [рабочий процесс сборки](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true) с использованием Azure Test Plans или Team Foundation Server (TFS).

4. Выполните модульные тесты с применением пользовательских параметров запуска.

::: moniker range="vs-2017"

Чтобы включить или отключить пользовательские параметры в интегрированной среде разработки, выберите файл или отмените его выбор в меню **Тест** > **Параметры тестирования**.

![Меню параметров тестирования с пользовательским файлом параметров в Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Чтобы включить или отключить пользовательские параметры в интегрированной среде разработки, выберите файл или отмените его выбор в меню **Тест**.

::: moniker-end

> [!TIP]
> Можно создать в решении несколько файлов *.runsettings* файлов и при необходимости выбирать один из них в качестве действующего файла параметров тестирования.

## <a name="specify-a-run-settings-file-in-the-ide"></a>Указание файла параметров запуска в интегрированной среде разработки

Доступные методы зависят от используемой версии среды Visual Studio.

::: moniker range="vs-2017"
Чтобы указать файл параметров запуска в интегрированной среде разработки, выберите **Тест** > **Параметры тестирования** > **Выбрать файл параметров теста**, а затем выберите файл *RUNSETTINGS*.

![Выбор файла параметров тестирования в Visual Studio 2017](media/select-test-settings-file.png)

В меню "Параметры тестирования" появится файл, который можно выбрать или отменить выбор. Если файл параметров запуска выбран, он применяется при каждом выборе функции **Анализ объема протестированного кода**.
::: moniker-end

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 версии 16.4 и более поздней

Файл параметров запуска можно указать в Visual Studio 2019 версии 16.4 или более поздней тремя способами:

- [автоматическое определение параметров запуска](#autodetect-the-run-settings-file);
- [настройка параметров запуска вручную](#manually-select-the-run-settings-file);
- [задание свойства сборки](#set-a-build-property).

#### <a name="autodetect-the-run-settings-file"></a>Автоматическое определение параметров запуска

> [!NOTE]
> Оно будет работать только для файла с именем `.runsettings`.

Чтобы файл параметров запуска определялся автоматически, поместите его в корень решения.

Если включено автоматическое определение файлов параметров запуска, параметры в этом файле применяются ко всем тестовым запускам. Вы можете включить автоматическое обнаружение RUNSETTINGS-файлов двумя способами.

- Выберите **Сервис** > **Параметры** > **Тест** > **Автоматическое обнаружение файлов параметров выполнения**.

   ![Параметр "Автоматическое обнаружение файлов параметров выполнения" в Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)

- Выберите **Тест** > **Настройка параметров выполнения** > **Автоматическое обнаружение файлов параметров выполнения**.

   ![Меню "Автоматическое обнаружение файлов параметров выполнения" в Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

#### <a name="manually-select-the-run-settings-file"></a>Выбор файла параметров запуска вручную

В интегрированной среде разработки выберите **Тест** > **Настройка параметров выполнения** > **Выберите файл параметров выполнения на уровне решения**, а затем выберите файл *RUNSETTINGS*.

   - Этот файл переопределяет *RUNSETTINGS*-файл в корневом каталоге решения, если он существует, и применяется ко всем тестовым запускам.
   - Этот выбор файла сохраняется только локально.

![Пункт меню "Выберите файл параметров выполнения на уровне решения" для теста в Visual Studio 2019](media/vs-2019/select-solution-settings-file.png)

#### <a name="set-a-build-property"></a>Задание свойства сборки

Добавить свойство сборки в проект с помощью файла проекта или файла Directory.Build.props. Файл параметров запуска для проекта задается свойством **RunSettingsFilePath**.

- В настоящее время параметры запуска на уровне проекта поддерживаются в проектах C#, VB, C++ и F#.
- Файл, указанный для проекта, переопределяет любой другой файл параметров запуска, указанный в решении.
- [Эти свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md) можно использовать для указания пути к файлу параметров запуска.

Пример указания файла с расширением *RUNSETTINGS* для проекта:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
  </PropertyGroup>
  ...
</Project>
```

### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 версии 16.3 и более ранней

Чтобы указать файл параметров запуска в интегрированной среде разработки, выберите **Тестирование** > **Выбрать файл параметров**. Найдите и выберите файл *.runsettings*.

![Выбор файла параметров тестирования в Visual Studio 2019](media/vs-2019/select-settings-file.png)

В меню "Тестирование" появится файл, который можно выбрать или отменить выбор. Если файл параметров запуска выбран, он применяется при каждом выборе функции **Анализ объема протестированного кода**.
::: moniker-end

## <a name="specify-a-run-settings-file-from-the-command-line"></a>Указание файла параметров тестирования в командной строке

Для запуска тестов из командной строки используйте *vstest.console.exe* и укажите файл параметров с помощью параметра **/Settings**.

1. Откройте [командную строку разработчика для Visual Studio](../ide/reference/command-prompt-powershell.md).

2. Введите команду, подобную следующей:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   or

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Дополнительные сведения см. в статье [Параметры командной строки для VSTest.Console.exe](vstest-console-options.md).

## <a name="the-runsettings-file"></a>RUNSETTINGS-файл

Файл RUNSETTINGS — это XML-файл, который содержит различные элементы конфигурации в элементе **RunSettings**. В последующих разделах подробно описаны эти элементы. Полный пример см. в [образце файла *.runsettings](#example-runsettings-file).

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- configuration elements -->
</RunSettings>
```

Каждый элемент конфигурации необязателен, так как имеет значение по умолчанию.

## <a name="runconfiguration-element"></a>Элемент RunConfiguration

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
</RunConfiguration>
```

Элемент **RunConfiguration** может содержать следующие элементы:

|Узел|По умолчанию|Значения|
|-|-|-|
|**MaxCpuCount**|1|Этот параметр управляет степенью параллелизма при выполнении тестов при запуске модульных тестов, используя доступные ядра на компьютере. Модуль выполнения тестов запускается как отдельный процесс на каждом доступном ядре и дает каждому ядру контейнер с запускаемыми тестами. Контейнером может быть сборка, библиотека DLL или соответствующий артефакт. Тестовый контейнер — это модуль, работающий по расписанию. В каждом контейнере тесты запускаются в соответствии с платформой тестов. Если контейнеров много, то после того как процессы завершают выполнение тестов в контейнере, им предоставляются следующие доступные контейнеры.<br /><br />MaxCpuCount может быть:<br /><br />n, где 1 < n < числа ядер: будет запущено до n процессов;<br /><br />n, где n равно любому другому значению: число запускаемых процессов может достигать числа доступных ядер на компьютере. Например, установите n=0, чтобы позволить платформе автоматически определить оптимальное количество процессов для запуска в зависимости от среды.|
|**ResultsDirectory**||Каталог для сохранения результатов тестов. Путь задается относительно каталога, содержащего файл RUNSETTINGS.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` для источников .NET Core, `FrameworkUap10` для источников на основе UWP, `Framework45` для .NET Framework 4.5 и более поздней версии, `Framework40` для .NET Framework 4.0 и `Framework35` для .NET Framework 3.5.<br /><br />Этот параметр указывает, какая версия платформы модульных тестов используется для поиска и выполнения тестов. Эта версия может отличаться от версии платформы .NET, указанной в свойствах сборки проекта модульного теста.<br /><br />Если опустить элемент `TargetFrameworkVersion` в файле *.runsettings*, платформа автоматически определит версию .NET на основе двоичных файлов сборки.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||Один или несколько путей к каталогу, где находятся адаптеры TestAdapters|
|**TestSessionTimeout**||Дает пользователям возможность завершить сеанс тестирования, если его длительность превышает заданный промежуток времени. Задав время ожидания, вы обеспечите надлежащее использование ресурсов и ограничите выполнение сеансов тестирования определенным периодом. Этот параметр доступен в **Visual Studio 2017 версии 15.5** и более поздних версий.|
|**DotnetHostPath**||Укажите пользовательский путь к узлу dotnet, который используется для запуска testhost. Это полезно при создании собственного узла dotnet, например при создании репозитория dotnet/runtime. При указании этого параметра поиск testhost.exe выполняться не будет, и всегда будет использоваться testhost.dll.|
|**TreatNoTestsAsError**|false| true или false <br>Укажите логическое значение, определяющее код выхода, если тесты не обнаружены. Если значение равно `true` и тесты не обнаружены, возвращается ненулевой код выхода. Иначе возвращается нуль.|

## <a name="datacollectors-element-diagnostic-data-adapters"></a>Элемент DataCollectors (адаптеры диагностических данных)

Элемент **DataCollectors** задает параметры адаптеров диагностических данных. Адаптеры диагностических данных собирают дополнительные сведения о среде и тестируемом приложении. Для каждого адаптера заданы параметры по умолчанию; указывать параметры следует, только если вы не хотите использовать параметры по умолчанию.

```xml
<DataCollectionRunSettings>
  <DataCollectors>
    <!-- data collectors -->
  </DataCollectors>
</DataCollectionRunSettings>
```

### <a name="codecoverage-data-collector"></a>Сборщик данных CodeCoverage

Сборщик данных о покрытии кода создает журнал с указанием того, какие части кода приложения были включены в тест. Подробные сведения о настройке параметров объема протестированного кода см. в разделе [Настройка анализа объема протестированного кода](../test/customizing-code-coverage-analysis.md).

```xml
<DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
  <Configuration>
    <CodeCoverage>
      <ModulePaths>
        <Exclude>
          <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
      </ModulePaths>

      <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
      <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
      <CollectFromChildProcesses>True</CollectFromChildProcesses>
      <CollectAspDotNet>False</CollectAspDotNet>
    </CodeCoverage>
  </Configuration>
</DataCollector>
```

### <a name="videorecorder-data-collector"></a>Сборщик данных VideoRecorder

Сборщик видеоданных захватывает запись экрана при выполнении тестов. Эта запись полезна для устранения неполадок тестов пользовательского интерфейса. Сборщик видеоданных предусмотрен в **Visual Studio 2017 версии 15.5** и более поздних версий. Пример настройки этого сборщика данных см. в [образце файла *.runsettings](#example-runsettings-file).

Для настройки любого другого типа адаптеров диагностических данных используйте [файл параметров тестирования](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="blame-data-collector"></a>Запуск cборщика данных в режиме обвинения

Этот параметр помогает изолировать проблемный тест, из-за которого в узле тестов возникает сбой. При запуске сборщика создается выходной файл (*Sequence.xml*) в *TestResults*, в который записывается порядок выполнения теста перед сбоем.

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

## <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Параметры тестового запуска предоставляют способ определения переменных и значений, доступных для тестов во время выполнения. Обращайтесь к параметрам с помощью свойства MSTest <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> (или NUnit [TestContext](https://docs.nunit.org/articles/nunit/writing-tests/TestContext.html)):

```csharp
private string _appUrl;
public TestContext TestContext { get; set; }

[TestMethod] // [Test] for NUnit
public void HomePageTest()
{
    string _appURL = TestContext.Properties["webAppUrl"];
}
```

Чтобы использовать параметры тестового запуска, добавьте в тестовый класс общедоступное свойство <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext>.

## <a name="loggerrunsettings-element"></a>Элемент LoggerRunSettings

Раздел `LoggerRunSettings` определяет средства ведения журнала, которые будут использоваться при тестовом запуске. Самые распространенные средства ведения журнала — это консоль, файл с результатами теста Visual Studio (TRX) и html.

```xml
<LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
    </Loggers>
  </LoggerRunSettings>
```

## <a name="mstest-element"></a>Элемент MSTest

Эти параметры относятся к адаптеру тестов, выполняющему методы теста, которые имеют атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>.

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

|Параметр Configuration|Значение по умолчанию|Значения|
|-|-|-|
|**ForcedLegacyMode**|false|В Visual Studio 2012 адаптер MSTest был оптимизирован для повышения скорости и масштабируемости. Некоторое поведение, в частности порядок, в котором выполняются тесты, может немного отличаться от поведения в предыдущих выпусках Visual Studio. Чтобы использовать старый адаптер теста, установите для этого параметра значение **true**.<br /><br />Например, этот параметр можно использовать при наличии файла *app.config*, указанного для модульного теста.<br /><br />Рекомендуется рассмотреть возможность рефакторинга тестов для включения возможности использования более нового адаптера.|
|**IgnoreTestImpact**|false|Функция влияния на тесты приоритизирует тесты, затронутые последними изменениями, при запуске в MSTest или из Microsoft Test Manager (не рекомендуется в Visual Studio 2017). Этот параметр деактивирует функцию. Дополнительные сведения см. в разделе [Какие тесты следует выполнить с момента предыдущей сборки](/previous-versions/dd286589(v=vs.140)).|
|**SettingsFile**||Здесь можно задать файл параметров тестирования для использования с адаптером MSTest. Этот файл можно также указать [из меню параметров](#specify-a-run-settings-file-in-the-ide).<br /><br />Если задано это значение, необходимо также задать для параметра **ForcedlegacyMode** значение **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|После завершения тестового запуска MSTest завершает работу. Будет также завершен любой процесс, запущенный в рамках теста. Чтобы сохранить исполнитель тестов в активном состоянии, задайте для этого параметра значение **true**. Например, этот параметр можно использовать, чтобы браузер продолжал работать в перерывах между закодированными тестами пользовательского интерфейса.|
|**DeploymentEnabled**|true|Если установить для этого параметра значение **false**, то элементы развертывания, заданные в методе теста, не будут копироваться в каталог развертывания.|
|**CaptureTraceOutput**|true|Чтобы выполнять запись в трассировку отладки из метода теста, используйте <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Чтобы сохранить каталог развертывания после завершения тестового запуска, установите для этого параметра значение **false**.|
|**MapInconclusiveToFailed**|false|Если тест завершается с неопределенным состоянием, оно обычно сопоставляется с состоянием "Пропущено" в **обозревателе тестов**. Если требуется, чтобы тесты с неопределенным результатом отображались как завершившиеся неудачно, установите для этого параметра значение **true**.|
|**InProcMode**|false|Если требуется, чтобы тесты выполнялись в одном процессе с адаптером MSTest, установите этот параметр в значение **true**. Этот параметр обеспечивает небольшое повышение производительности. Но если тест прекращается с выдачей исключения, остальные тесты выполняться не будут.|
|**AssemblyResolution**|false|При поиске и выполнении модульных тестов можно указать пути для дополнительных сборок. Например, эти пути можно использовать для сборок зависимостей, которые не находятся в том же каталоге, что и тестовая сборка. Чтобы указать путь, используйте элемент **путь к каталогу**. Пути могут содержать переменные среды.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="example-runsettings-file"></a>Пример файла *.runsettings*

Следующий XML-код представляет содержимое обычного файла *.runsettings*. Скопируйте этот код и измените его в соответствии с требованиями.

Каждый элемент этого файла необязателен, так как все они имеют значения по умолчанию.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>

    <!-- true or false -->
    <!-- Value that specifies the exit code when no tests are discovered -->
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>

      <!-- Configuration for blame data collector -->
      <DataCollector friendlyName="blame" enabled="True">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Configuration for loggers -->
  <LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="blame" enabled="True" />
    </Loggers>
  </LoggerRunSettings>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="specify-environment-variables-in-the-runsettings-file"></a>Указание переменных среды в файле *.runsettings*

Вы можете задавать переменные среды в файле *.runsettings*, способный напрямую взаимодействовать с узлом тестов. Указание переменных среды в файле *.runsettings* необходимо для поддержки особых проектов, требующих установки таких переменных среды, как *DOTNET_ROOT*. Эти переменные задаются при порождении процесса узла тестов и доступны на этом узле.

### <a name="example"></a>Пример

Следующий код является примером файла *.runsettings*, который передает переменные среды:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <RunConfiguration>
    <EnvironmentVariables>
      <!-- List of environment variables we want to set-->
      <DOTNET_ROOT>C:\ProgramFiles\dotnet</DOTNET_ROOT>
      <SDK_PATH>C:\Codebase\Sdk</SDK_PATH>
    </EnvironmentVariables>
  </RunConfiguration>
</RunSettings>
```

Узел **RunConfiguration** должен содержать узел **EnvironmentVariables**. Переменная среды может быть указана как имя и значение элемента.

> [!NOTE]
> Поскольку эти переменные среды должны всегда быть заданы при запуске узла тестов, тесты всегда должны выполняться в отдельном процессе. Для этого при наличии переменных среды будет устанавливаться флаг */InIsolation*, позволяющий всегда вызывать узел тестов.

## <a name="see-also"></a>См. также

- [Настройка тестового запуска](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Настройка анализа объема протестированного кода](../test/customizing-code-coverage-analysis.md)
- [Задача теста Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts&preserve-view=true)
