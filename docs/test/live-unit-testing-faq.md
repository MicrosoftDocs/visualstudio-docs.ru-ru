---
title: 'Функция Live Unit Testing: вопросы и ответы'
description: Ознакомьтесь с этими вопросами и ответами по Live Unit Testing, включая поддерживаемые платформы, конфигурацию и настройку.
ms.custom: SEO-VS-2020
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: bb2c9a4cae25b388d5817b04ff54f6e6443b2f44
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800553"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Часто задаваемые вопросы о функции Live Unit Testing

## <a name="supported-frameworks"></a>Поддерживаемые платформы

**Какие платформы тестирования и минимальные версии поддерживает функция Live Unit Testing?**

Функция Live Unit Testing работает на трех известных платформах модульного тестирования, приведенных в таблице ниже. В этой таблице также приведены сведения о минимальной поддерживаемой версии адаптеров и платформ. Платформы модульного тестирования доступны на сайте NuGet.org.

|Тестовая платформа  |Минимальная версия адаптера Visual Studio  |Минимальная версия платформы  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio версии 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter версии 3.7.0 |NUnit версии 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Если у вас есть старые тестовые проекты на основе MSTest, которые ссылаются на `Microsoft.VisualStudio.QualityTools.UnitTestFramework`, и вы не хотите переходить на более новые пакеты NuGet MSTest, выполните обновление до Visual Studio 2019 или Visual Studio 2017.

В некоторых случаях, чтобы обеспечить работу Live Unit Testing, вам потребуется явным образом восстановить пакеты NuGet, на которые ссылается проект в решении. Вы можете восстановить пакеты, выполнив сборку решения явным образом (в меню верхнего уровня Visual Studio выберите **Сборка** > **Пересобрать решение**) или щелкнув решение правой кнопкой мыши и выбрав пункт **Восстановить пакеты NuGet** перед включением Living Unit Testing.

## <a name="net-core-support"></a>Поддержка .NET Core

**Совместима ли функция Live Unit Testing с .NET Core?**

Да. Функция Live Unit Testing совместима с .NET Core и .NET Framework.

## <a name="configuration"></a>Параметр Configuration

**Почему функция Live Unit Testing не работает после включения?**

Сведения о том, почему функция Live Unit Testing не работает, можно посмотреть в окне вывода (после выбора раскрывающегося меню Live Unit Testing). Эта функция может не работать по одной из следующих причин:

- Пакеты NuGet, на которые имеются ссылки в проекте, не были восстановлены. Чтобы устранить эту проблему, перед включением Live Unit Testing выполните явную сборку решения или восстановите пакеты NuGet в решении.

- При использовании в проекте тестов на основе MSTest удалите ссылку на `Microsoft.VisualStudio.QualityTools.UnitTestFramework` и добавьте ссылки на последнюю версию пакетов NuGet для MSTest, `MSTest.TestAdapter` (минимальная версия — 1.1.11) и `MSTest.TestFramework` (минимальная версия — 1.1.11). Дополнительные сведения см. в разделе "Поддерживаемые тестовые платформы" статьи [Использование Live Unit Testing в Visual Studio](live-unit-testing.md#supported-test-frameworks).

- По крайней мере один проект в решении должен иметь ссылку на NuGet или прямую ссылку на платформу тестирования xUnit, NUnit или MSTest. Этот проект также должен иметь ссылку на соответствующий пакет NuGet для адаптера теста Visual Studio. Ссылку на адаптер теста Visual Studio можно также создать, используя файл *RUNSETTINGS*. Файл *RUNSETTINGS* должен иметь запись, аналогичную следующей:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Неправильный объем протестированного кода после обновления

**Почему Live Unit Testing показывает неправильный объем протестированного кода после обновления до поддерживаемой версии адаптера теста, на который ссылаются проекты Visual Studio?**

- Если несколько проектов в решении ссылаются на пакет адаптера теста NuGet, требуется обновить каждый из них до поддерживаемой версии.

- Убедитесь, что *PROPS*-файл MSBuild, импортированный из пакета адаптера теста, также обновлен должным образом. Проверьте версию и путь импорта для пакета NuGet, которые обычно указаны в начале файла проекта, например:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Настройка сборок

**Можно ли настроить сборки для Live Unit Testing?**

Если для реализации инструментирования (Live Unit Testing) в решении требуется настроить дополнительные шаги, необязательные для обычной неинструментированной сборки, вы можете добавить код в проект или файлы *TARGETS*. Этот код проверяет свойство `BuildingForLiveUnitTesting` и выполняет настраиваемые шаги перед сборкой или после нее. Вы также можете удалить определенные шаги сборки (например, публикация или создание пакетов) или добавить шаги (например, шаги для копирования) в сборку Live Unit Testing на основе этого свойства проекта. Настройка сборки на основе этого свойства никак не изменит обычную сборку, а только повлияет на сборки Live Unit Testing.

Например, у вас может быть целевой объект, который создает пакеты NuGet во время обычной сборки. Вы, вероятно, не хотите, чтобы пакеты NuGet создавались после каждого внесенного изменения. Таким образом, вы можете отключить этот целевой объект в сборке Live Unit Testing, выполнив следующую команду:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Сообщения об ошибках с \<OutputPath>, \<OutDir> или \<IntermediateOutputPath>

**При попытке выполнить сборку решения с помощью Live Unit Testing отображается сообщение об ошибке, указывающее, что свойство `<OutputPath>` или `<OutDir>` задано безусловно и Live Unit Testing не будет выполнять тесты из выходной сборки. С чем это связано?**

Эта ошибка может возникать, если в процессе сборки для решения определена пользовательская логика, которая указывает на место создания двоичных файлов. По умолчанию расположение двоичных файлов зависит от `<OutputPath>`, `<OutDir>` или `<IntermediateOutputPath>`, а также от `<BaseOutputPath>` или `<BaseIntermediateOutputPath>`.

Live Unit Testing переопределяет эти переменные, чтобы гарантировать перенос артефактов сборки в папку артефактов Live Unit Testing. Если же процесс сборки также переопределит эти переменные, произойдет сбой.

Существует два основных подхода к выполнению успешной сборки Live Unit Testing. Для более простых конфигураций сборки пути к выходным файлам могут быть основаны на `<BaseIntermediateOutputPath>`. Для более сложных конфигураций пути к выходным файлам могут быть основаны на `<LiveUnitTestingBuildRootPath>`.

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Условное переопределение `<OutputPath>`/`<IntermediateOutputPath>` на основе `<BaseOutputPath>`/`<BaseIntermediateOutputPath>`.

> [!NOTE]
> Чтобы использовать этот подход, для каждого проекта необходимо обеспечить возможность независимой друг от друга сборки. Ссылка в одном проекте на артефакт из другого проекта во время сборки запрещена. Не используйте один проект для динамической загрузки сборок из другого проекта во время выполнения (например, вызвав `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")`).

Во время сборки Live Unit Testing автоматически переопределяет переменные `<BaseOutputPath>`/`<BaseIntermediateOutputPath>`, чтобы указать целевую папку артефактов Live Unit Testing.

Например, сборка может переопределить <OutputPath>, как показано ниже.

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

В этом случае ее можно заменить следующим кодом XML:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Это гарантирует, что `<OutputPath>` находится в папке `<BaseOutputPath>`.

Не переопределяйте `<OutDir>` непосредственно в процессе сборки. Переопределите `<OutputPath>` вместо того, чтобы отправлять артефакты сборки в определенное расположение.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Переопределение свойств на основе свойства `<LiveUnitTestingBuildRootPath>`.

> [!NOTE]
> Такой подход требует осторожного использования файлов, добавленных в папку артефактов, которые не создаются во время сборки. В приведенном ниже примере показано, что делать при помещении папки пакетов в артефакты. Так как содержимое этой папки не создается во время сборки, свойство MSBuild **должно оставаться неизменным**.

Во время сборки Live Unit Testing свойство `<LiveUnitTestingBuildRootPath>` задается в расположении папки артефактов Live Unit Testing.

Например, предположим, что ваш проект имеет структуру, приведенную в этой статье.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Во время сборки Live Unit Testing для свойства `<LiveUnitTestingBuildRootPath>` задается полный путь `.vs\...\lut\0\b`. Если проект определяет свойство `<ArtifactsRoot>`, отображаемое в каталоге решения, вы можете обновить проект MSBuild следующим образом:

```xml
<Project>
    <PropertyGroup Condition="'$(LiveUnitTestingBuildRootPath)' == ''">
        <SolutionDir>$([MSBuild]::GetDirectoryNameOfFileAbove(`$(MSBuildProjectDirectory)`, `YOUR_SOLUTION_NAME.sln`))\</SolutionDir>

        <ArtifactsRoot>Artifacts\</ArtifactsRoot>
        <ArtifactsRoot Condition="'$(LiveUnitTestingBuildRootPath)' != ''">$(LiveUnitTestingBuildRootPath)</ArtifactsRoot>
    </PropertyGroup>

    <PropertyGroup>
        <BinLogPath>$(ArtifactsRoot)\BinLog</BinLogPath>
        <ObjPath>$(ArtifactsRoot)\Obj</ObjPath>
        <BinPath>$(ArtifactsRoot)\Bin</BinPath>
        <NupkgPath>$(ArtifactsRoot)\Nupkg</NupkgPath>
        <TestResultsPath>$(ArtifactsRoot)\TestResults</TestResultsPath>

        <!-- Note: Given that a build doesn't generate packages, the path should be relative to the solution dir, rather than artifacts root, which will change during a Live Unit Testing build. -->
        <PackagesPath>$(SolutionDir)\artifacts\packages</PackagesPath>
    </PropertyGroup>
</Project>
```

## <a name="build-artifact-location"></a>Расположение артефакта сборки

**Я хочу, чтобы артефакты сборки Live Unit Testing отправлялись в определенное расположение, а не в расположение по умолчанию в папке *.vs*. Как это можно сделать?**

Задайте путь, где вы хотите хранить артефакты сборки Live Unit Testing, в качестве значения переменной среды уровня пользователя `LiveUnitTesting_BuildRoot`. 

## <a name="test-explorer-versus-live-unit-testing"></a>Обозреватель тестов и Live Unit Testing

**Чем отличается выполнение тестов в окне обозревателя тестов от их выполнения с помощью функции Live Unit Testing?**

Существует несколько различий:

- Во время выполнения и отладки тестов из окна **обозревателя тестов** используются обычные двоичные файлы, а при использовании функции Live Unit Testing — инструментированные двоичные файлы. Если вы хотите выполнить отладку инструментированных двоичных файлов, добавьте вызов метода [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) в метод теста. После этого отладчик будет запускаться во время каждого выполнения метода (в том числе когда этот метод выполняется с помощью функции Live Unit Testing), и тогда вы сможете прикрепить инструментированные двоичные файлы, а также выполнить их отладку. Тем не менее мы надеемся, что инструментирование происходит прозрачно в большинстве пользовательских сценариев, и вам не потребуется выполнять отладку инструментированных двоичных файлов.

- Функция Live Unit Testing не создает домен приложения для выполнения тестов, но при выполнении тестов в окне **обозревателя тестов** этот домен создается.

- Функция Live Unit Testing выполняет тесты из разных сборок последовательно. В окне **обозревателя тестов** можно выбрать режим параллельного выполнения нескольких тестов.

- **Обозреватель тестов** по умолчанию выполняет тесты в однопотоковом подразделении (STA), а Live Unit Testing — в многопотоковом (MTA). Чтобы выполнить тесты MSTest в однопотоковом подразделении с помощью функции Live Unit Testing, декорируйте метод теста или содержащий класс атрибутом `<STATestMethod>` или `<STATestClass>`, который находится в пакете `MSTest.STAExtensions 1.0.3-beta` NuGet. Для NUnit декорируйте метод теста атрибутом `<RequiresThread(ApartmentState.STA)>`, а для xUnit — атрибутом `<STAFact>`.

## <a name="exclude-tests"></a>Исключение тестов

**Как исключить тесты из выполнения с помощью Live Unit Testing?**

Пользовательские параметры см. в разделе "Добавление и исключение тестовых проектов и методов теста" статьи [Использование Live Unit Testing в Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods). Добавление или исключение тестов полезно, когда необходимо выполнить конкретный набор тестов для определенного сеанса редактирования или сохранить личные настройки.

Для параметров, относящихся к конкретному решению, вы можете программно применить атрибут <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName>, чтобы исключить методы, свойства, классы или структуры из инструментирования с помощью функции Live Unit Testing. Кроме того, чтобы исключить весь проект из инструментирования, в файле проекта для свойства `<ExcludeFromCodeCoverage>` можно задать значение `true`. Функция Live Unit Testing будет по-прежнему выполнять неинструментированные тесты, но их покрытие визуализироваться не будет.

Вы также можете проверить, отправлен ли атрибут `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` в текущий домен приложения, и на основе этого отключить тесты. Например, на тестовой платформе xUnit это можно сделать следующим образом:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>Заголовки Win32 PE

**Почему отличаются заголовки Win32 PE в инструментированных сборках, созданных с помощью функции Live Unit Testing?**

Эта проблема исправлена и отсутствует в Visual Studio 2017 версии 15.3 и более поздних.

Это известная ошибка прежних версий Visual Studio 2017, которая в сборках Live Unit Testing может повлиять на внедрение следующих данных заголовка Win32 PE:

- версия файла (заданная в коде параметром @System.Reflection.AssemblyFileVersionAttribute );

- значок Win32 (заданный в командной строке параметром `/win32icon:`);

- манифест Win32 (заданный в командной строке параметром `/win32manifest:`).

При выполнении тестов на основе этих значений с помощью функции Live Unit Testing может произойти сбой.

::: moniker-end

## <a name="continuous-builds"></a>Непрерывные сборки

**Почему функция Live Unit Testing выполняет сборку решения, даже если я не вношу изменения?**

Сборка решения при отсутствии изменений может произойти, если в процессе сборки создается исходный код, который является частью самого решения, а в целевых файлах сборки не указаны соответствующие входные и выходные данные. В целевых файлах необходимо определить список входных и выходных данных. За счет этого MSBuild сможет выполнять соответствующие проверки наличия обновлений и определять, требуются ли они для новой сборки.

Функция Live Unit Testing запускает сборку после обнаружения изменений в исходных файлах. Так как в процессе сборки решения создаются исходные файлы, функция Live Unit Testing переходит в бесконечный цикл сборки. Тем не менее, если проверка входных и выходных данных целевого файла выполняется, когда функция Live Unit Testing запускает вторую сборку (после обнаружения вновь созданных исходных файлов из предыдущей сборки), цикл сборки прерывается, так как при проверке входных и выходных данных будет установлено, что обновление не требуется.

## <a name="editor-icons"></a>Редактор значков

**Почему не отображаются какие-либо значки, даже если функция Live Unit Testing выполняет тесты (в окне вывода появляются сообщения)?**

Значки могут не отображаться в редакторе, если сборки, обрабатываемые функцией Live Unit Testing, по какой-либо причине не инструментированы. Например, эта функция несовместима с проектами со значением `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. В этом случае, чтобы обеспечить работоспособность функции Live Unit Testing, сборку необходимо обновить. Для этого либо удалите этот параметр, либо измените его на `true`. 

## <a name="capture-logs"></a>Сохранение журналов

**Как собрать более подробные журналы для создания отчетов об ошибках?**

Чтобы собрать более подробные журналы, выполните следующее:

- Выберите **Инструменты** > **Параметры** > **Live Unit Testing** и задайте для параметра ведения журнала значение **Подробный**. В этом случае в окне **вывода** будут отображаться более подробные журналы.

- В качестве значения переменной среды пользователя `LiveUnitTesting_BuildLog` задайте файл, который вы хотите использовать для сбора данных журнала MSBuild. Затем в этом файле можно просмотреть более подробные сообщения журнала MSBuild из сборок Live Unit Testing.

- Задайте для пользовательской переменной среды `LiveUnitTesting_TestPlatformLog` значение `1`, чтобы собирать журнал тестовой платформы. Теперь в файле `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` можно просмотреть подробные сообщения журнала тестовой платформы о запусках динамического модульного тестирования.

- Создайте переменную среды уровня пользователя `VS_UTE_DIAGNOSTICS` и присвойте ей значение 1 (или другое значение), а затем перезапустите Visual Studio. После этого на вкладке **Выходные данные — Тесты** в Visual Studio должно отображаться большое количество регистрируемых данных.

## <a name="see-also"></a>См. также

- [Динамическое модульное тестирование](live-unit-testing.md)
