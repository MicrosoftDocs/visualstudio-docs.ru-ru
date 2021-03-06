---
description: Система проектов Visual C++ используется для VCXPROJ-файлов.
title: Расширяемость проекта Visual C++
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fc538402ae39753f14a3bccd8bcd17ddb0081078
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221240"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Расширяемость системы проектов Visual Studio C++ и интеграция набора инструментов

Система проектов Visual C++ используется для VCXPROJ-файлов. Он основан на [системе общих проектов Visual Studio (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) и предоставляет дополнительные специальные точки расширения C++ для простоты интеграции новых наборов инструментов, архитектуры сборки и целевых платформ.

## <a name="c-msbuild-targets-structure"></a>Структура целевых объектов C++ MSBuild

Все файлы VCXPROJ импортируют следующие файлы:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Эти файлы определяются по отдельности. Вместо этого они импортируют другие файлы на основе этих значений свойств:

- `$(ApplicationType)`

   Примеры: Магазин Windows, Android, Linux

- `$(ApplicationTypeRevision)`

   Это должна быть допустимая строка версии в виде основной. дополнительный номер [. сборка [. Редакция]].

   Примеры: 1,0, 10.0.0.0

- `$(Platform)`

   Архитектура сборки с именем "Platform" по историческим причинам.

   Примеры: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Примеры: V140, v141, v141_xp, LLVM

Эти значения свойств указывают имена папок в `$(VCTargetsPath)` корневой папке:

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*Тип приложения*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Платформ*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*платформтулсетс*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*Платформ*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*платформтулсетс*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

`$(VCTargetsPath)` \\ Папка *Platforms* \\ используется, если `$(ApplicationType)` пустой, для проектов Windows для настольных компьютеров.

### <a name="add-a-new-platform-toolset"></a>Добавить новый набор инструментов платформы

Чтобы добавить новый набор инструментов, например "митулсет" для существующей платформы Win32, создайте папку *митулсет* в разделе `$(VCTargetsPath)` *\\ Platforms \\ Win32 \\ платформтулсетс \\*, а также создайте в ней файлы *набора инструментов. props* и *Toolset. targets* .

Каждое имя папки в разделе *платформтулсетс* отображается в диалоговом окне **Свойства проекта** как доступный **набор инструментов платформы** для указанной платформы, как показано ниже:

![Свойство набора инструментов платформы в диалоговом окне страниц свойств проекта](media/vc-project-extensibility-platform-toolset-property.png "Свойство набора инструментов платформы в диалоговом окне страниц свойств проекта")

Создавайте похожие папки *митулсет* и *набор инструментов. props* и *Targets* в каждой существующей папке платформы, которую поддерживает этот набор инструментов.

### <a name="add-a-new-platform"></a>Добавление новой платформы

Чтобы добавить новую платформу, например "миплатформ", создайте папку *миплатформ* на `$(VCTargetsPath)` *\\ \\ платформах* и создайте в ней файлы *Platform. Default. props*, *Platform. props* и *Platform. targets* . Также `$(VCTargetsPath)` *\\ Создайте \\* папку <strong><em>миплатформ</em></strong>*\\ платформтулсетс \\* и создайте в ней хотя бы один набор инструментов.

Все имена папок в папке *Platforms* для каждой `$(ApplicationType)` `$(ApplicationTypeRevision)` среды и отображаются в интегрированной среде разработки в качестве доступных вариантов **платформы** для проекта.

![Новый вариант платформы в диалоговом окне создания платформы проекта](media/vc-project-extensibility-new-project-platform.png "Новый вариант платформы в диалоговом окне создания платформы проекта")

### <a name="add-a-new-application-type"></a>Добавление нового типа приложения

Чтобы добавить новый тип приложения, создайте папку *MyApplicationType* в разделе " `$(VCTargetsPath)` *\\ тип \\ приложения* " и создайте в ней файл *по умолчанию. props* . Для типа приложения требуется по крайней мере одна редакция, поэтому создайте `$(VCTargetsPath)` *\\ приложение типа \\ MyApplicationType \\ 1,0* и создайте в нем файл *по умолчанию. props* . Следует также создать `$(VCTargetsPath)` папку *\\ платформы ApplicationType \\ MyApplicationType \\ 1,0 \\* и создать по крайней мере одну платформу.

`$(ApplicationType)``$(ApplicationTypeRevision)`Свойства и не отображаются в пользовательском интерфейсе. Они определяются в шаблонах проектов и не могут быть изменены после создания проекта.

## <a name="the-vcxproj-import-tree"></a>Дерево импорта. vcxproj

Упрощенное дерево импортов для свойств PROPS и targets в Microsoft C++ выглядит следующим образом:

> `$(VCTargetsPath)`\\*Microsoft. cpp. Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Импортбефоре* \\ *По умолчанию* \\ \* . свойства *PROPS* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Тип* \\ `$(ApplicationType)` приложения \\ *По умолчанию. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Тип* \\ `$(ApplicationType)` приложения \\ `$(ApplicationTypeRevision)` \\ *По умолчанию. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Тип* \\ `$(ApplicationType)` приложения \\ `$(ApplicationTypeRevision)` \\  \\ `$(Platform)` Платформы \\ *Platform. Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Импортафтер* \\ *По умолчанию* \\ \* . свойства *PROPS*

Проекты Windows для настольных систем не определяются `$(ApplicationType)` , поэтому они только импортируют

> `$(VCTargetsPath)`\\*Microsoft. cpp. Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Импортбефоре* \\ *По умолчанию* \\ \* . свойства *PROPS* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ \\ `$(Platform)` Платформы \\ *Platform. Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Импортафтер* \\ *По умолчанию* \\ \* . свойства *PROPS*

Мы будем использовать `$(_PlatformFolder)` свойство для хранения `$(Platform)` расположения папок платформы. Это свойство имеет значение

> `$(VCTargetsPath)`\\*Платформ*\\`$(Platform)`

для классических приложений Windows и

> `$(VCTargetsPath)`\\*Тип* \\ `$(ApplicationType)` приложения \\ `$(ApplicationTypeRevision)` \\ *Платформы*\\`$(Platform)`

для всех остальных.

Файлы PROPS импортируются в следующем порядке:

> `$(VCTargetsPath)`\\*Microsoft. cpp. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Импортбефоре* \\ \* . свойства *PROPS* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` Платформтулсетс \\ *Набор инструментов. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Импортафтер* \\ \* . свойства *PROPS*

Целевые файлы импортируются в следующем порядке:

> `$(VCTargetsPath)`\\*Microsoft. cpp. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Current. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Импортбефоре* \\ \* . *целевые объекты* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` Платформтулсетс \\ *Набор инструментов. Target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Импортафтер* \\ \* . *целевые объекты*

Если необходимо определить некоторые свойства по умолчанию для набора инструментов, можно добавить файлы в соответствующие папки Импортбефоре и Импортафтер.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Файлы набора инструментов автора. props и Toolset. targets

Файлы *набора инструментов. props* и *набор инструментов. targets* имеют полный контроль над тем, что происходит во время сборки при использовании этого набора инструментов. Они также могут контролировать Доступные отладчики, некоторые пользовательские интерфейсы IDE, такие как содержимое диалогового окна **страницы свойств** , и некоторые другие аспекты поведения проекта.

Хотя набор инструментов может переопределять весь процесс сборки, обычно требуется, чтобы набор инструментов мог изменить или добавить некоторые шаги построения или использовать другие средства сборки в рамках существующего процесса сборки. Для этого существует ряд общих свойств и целевых файлов, которые можно импортировать в набор инструментов. В зависимости от того, что должен делать набор инструментов, эти файлы могут быть полезны для использования в качестве импорта или в качестве примеров.

- `$(VCTargetsPath)`\\*Microsoft. Кппкоммон. targets*

  Этот файл определяет основные части процесса сборки в машинном код, а также импортирует:

  - `$(VCTargetsPath)`\\*Microsoft. Кппбуилд. targets*

  - `$(VCTargetsPath)`\\*Microsoft. Буилдстепс. targets*

  - `$(MSBuildToolsPath)`\\*Microsoft. Common. targets*

- `$(VCTargetsPath)`\\*Microsoft. cpp. Common. props*

   Задает значения по умолчанию для наборов инструментов, использующих компиляторы и целевые окна Майкрософт.

- `$(VCTargetsPath)`\\*Microsoft. cpp. Виндовссдк. props*

   Этот файл определяет расположение Windows SDK и определяет некоторые важные свойства для приложений, предназначенных для Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Интеграция целевых объектов набора инструментов с процессом сборки C++ по умолчанию

Процесс сборки C++ по умолчанию определяется в *Microsoft. кппкоммон. targets*. Целевые объекты не вызывают никаких конкретных средств сборки. они указывают основные этапы построения, их порядок и зависимости.

Сборка C++ включает три основных шага, которые представлены следующими целевыми объектами:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Поскольку каждый шаг сборки может выполняться независимо, целевые объекты, выполняемые на одном шаге, не могут полагаться на группы элементов и свойства, определенные в целевых объектах, которые выполняются как часть другого этапа. Это деление позволяет выполнять определенные оптимизации производительности сборки. Хотя это и не используется по умолчанию, по-прежнему рекомендуется учитывать это разделение.

Целевые объекты, выполняемые внутри каждого этапа, контролируются следующими свойствами:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Каждый шаг также имеет свойства Before и After.

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Примеры целевых объектов, которые включены в каждый шаг, см. в файле *Microsoft. кппбуилд. targets* .

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Если взглянуть на цели, например, вы увидите, что `_ClCompile` они не выполняют никаких действий напрямую, а зависят от других целей, в том числе `ClCompile` :

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` и другие целевые объекты для конкретного инструмента сборки определяются как пустые целевые объекты в *Microsoft. кппбуилд. targets*:

```xml
<Target Name="ClCompile"/>
```

Так как `ClCompile` целевой объект пуст, если он не переопределен набором инструментов, реальное действие сборки не выполняется. Целевые объекты набора инструментов могут переопределять `ClCompile` целевой объект, то есть они могут содержать еще одно `ClCompile` Определение после импорта *Microsoft. кппбуилд. targets*:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Несмотря на свое имя, созданное до реализации поддержки кросс-платформенной версии в Visual Studio, `ClCompile` целевому объекту не нужно вызывать CL.exe. Он также может вызывать Clang, GCC или другие компиляторы с помощью соответствующих задач MSBuild.

`ClCompile`Целевой объект не должен иметь каких-либо зависимостей `SelectClCompile` , кроме целевого объекта, который необходим для работы команды компиляции single file в интегрированной среде разработки.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Задачи MSBuild для использования в целях набора инструментов

Для вызова фактического средства сборки целевому объекту необходимо вызвать задачу MSBuild. Существует базовая [Задача Exec](../msbuild/exec-task.md) , которая позволяет указать командную строку для запуска. Однако средства сборки обычно имеют много параметров, входных. и выводят результаты для последовательного построения, поэтому имеет смысл иметь специальные задачи для них. Например, `CL` задача преобразует свойства MSBuild в параметры CL.exe, записывает их в файл ответов и вызывает CL.exe. Он также отслеживает все входные и выходные файлы для последующих добавочных сборок. Дополнительные сведения см. в разделе [добавочные сборки и актуальные проверки](#incremental-builds-and-up-to-date-checks).

Microsoft.Cpp.Common.Tasks.dll реализует следующие задачи:

- `BSCMake`

- `CL`

- `ClangCompile` (Clang — параметры GCC)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (например, Exec, но с отслеживанием входных и выходных данных)

- `SetEnv`

- `GetOutOfDateItems`

Если у вас есть средство, выполняющее те же действия, что и у существующего средства, и оно имеет аналогичные параметры командной строки (например, Clang-CL и CL Do), то для обеих задач можно использовать одну и ту же задачу.

Если необходимо создать новую задачу для инструмента построения, можно выбрать один из следующих вариантов.

1. Если вы используете эту задачу редко или в течение нескольких секунд не имеет значения для сборки, можно использовать встроенные задачи MSBuild:

   - Задача XAML (настраиваемое правило сборки)

     Пример объявления задачи XAML см. в разделе `$(VCTargetsPath)` \\ *буилдкустомизатионс* \\ *masm.xml* и сведения об использовании см. в разделе `$(VCTargetsPath)` \\ *буилдкустомизатионс* \\ *MASM. targets*.

   - [Задача "код"](../msbuild/msbuild-inline-tasks.md)

1. Если требуется более высокая производительность задач или требуются более сложные функции, используйте обычный процесс [записи задач](../msbuild/task-writing.md) MSBuild.

   Если не все входные и выходные данные средства указаны в командной строке средства, как в `CL` `MIDL` сценариях, и, `RC` а также если требуется автоматическое отслеживание входных и выходных файлов и создание файла журнала, создайте задачу из `Microsoft.Build.CPPTasks.TrackedVCToolTask` класса. В настоящее время в документации по базовому классу [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) нет примеров или документации для сведений о `TrackedVCToolTask` классе. Если это будет особым интересом, добавьте свой счет в запрос [сообщества разработчиков](https://aka.ms/feedback/suggest?space=62).

## <a name="incremental-builds-and-up-to-date-checks"></a>Добавочные сборки и актуальные проверки

Целевые объекты добавочной сборки MSBuild по умолчанию используют `Inputs` `Outputs` атрибуты и. Если указать их, MSBuild вызывает цель только в том случае, если какой-либо из входов имеет более новую отметку времени, чем все выходные данные. Поскольку исходные файлы часто содержат или импортируют другие файлы, а средства построения создают различные выходные данные в зависимости от параметров средства, трудно указать все возможные входные и выходные данные в целевых объектах MSBuild.

Для управления этой проблемой в сборке C++ используется другой метод для поддержки добавочных сборок. Большинство целевых объектов не указывают входные и выходные данные, и в результате всегда выполняется во время сборки. Задачи, вызываемые целями, записывают сведения обо всех входных и выходных данных в файлы *журнала отслеживания* с расширением журнала. Файлы журнала отслеживания используются в последующих сборках для проверки изменений и необходимости их перестроения и обновления. Файлы журнала отслеживания также являются единственным источником для проверки сборки по умолчанию в интегрированной среде разработки.

Чтобы определить все входные и выходные данные, задачи собственного инструмента используют tracker.exe и класс [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) , предоставляемый MSBuild.

Microsoft.Build.CPPTasks.Common.dll определяет `TrackedVCToolTask` открытый абстрактный базовый класс. Большинство задач машинного средства являются производными от этого класса.

Начиная с обновления Visual Studio 2017 с обновлением 15,8, можно использовать `GetOutOfDateItems` задачу, реализованную в Microsoft.Cpp.Common.Tasks.dll, для создания файлов журнала отслеживания для пользовательских целевых объектов с известными входными и выходными данными.
Кроме того, их можно создать с помощью `WriteLinesToFile` задачи. `_WriteMasmTlogs`В качестве примера см. Целевой объект в `$(VCTargetsPath)` \\ *буилдкустомизатионс* \\ *MASM. targets* .

## <a name="tlog-files"></a>файлы журнала отслеживания

Существует три типа файлов журнала отслеживания: *Чтение*, *запись* и *Командная строка*. Чтение и запись файлов журнала отслеживания использования осуществляется добавочными сборками и актуальными проверками в интегрированной среде разработки. Файлы журнала в командной строке используются только в инкрементных сборках.

MSBuild предоставляет эти вспомогательные классы для чтения и записи файлов журнала отслеживания:

- [каноникалтраккединпутфилес](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [каноникалтраккедаутпутфилес](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

Класс [флаттраккингдата](/dotnet/api/microsoft.build.utilities.flattrackingdata) можно использовать для доступа к файлам для чтения и записи журналов отслеживания, а также для выдачи новых входных данных, отличных от выходных, или в случае отсутствия выходных данных. Он используется в проверке на наличие обновлений.

Файлы из командной строки. журналы содержат сведения о командных строках, используемых в сборке. Они используются только для добавочных сборок, а не для проверки на актуальность, поэтому внутренний формат определяется задачей MSBuild, которая их создает.

### <a name="read-tlog-format"></a>Чтение формата журнала отслеживания

*Чтение* файлов журнала отслеживания ( \* . Read. \* . Журнал отслеживания) содержит сведения о исходных файлах и их зависимостях.

Знак крышки ( **^** ) в начале строки указывает на один или несколько источников. Источники, использующие одни и те же зависимости, разделяются вертикальной чертой ( **\|** ).

Файлы зависимостей перечисляются после источников, каждый из которых находится в отдельной строке. Все имена файлов являются полными путями.

Например, предположим, что источники проекта находятся в *языке F: \\ Test \\ ConsoleApplication1 \\ ConsoleApplication1*. Если исходный файл, *Class1. cpp*, содержит эти данные,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

Затем файл *CL. Read. 1. отслеживания* содержит исходный файл, за которым следуют две зависимости:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Не обязательно писать имена файлов в верхнем регистре, но для некоторых средств это удобно.

### <a name="write-tlog-format"></a>Запись формата журнала отслеживания

*Напишите* . журнал отслеживания ( \* . Write. \* . журналы отслеживания) — файлы соединяются с источниками и выходами.

Знак крышки ( **^** ) в начале строки указывает на один или несколько источников. Несколько источников разделяются вертикальной чертой ( **\|** ).

Выходные файлы, созданные из источников, должны быть перечислены после источников, каждый из которых находится в отдельной строке. Все имена файлов должны быть полными путями.

Например, для простого проекта Консолеаппликатион с дополнительным исходным файлом *Class1. cpp* файл *Link. Write. 1. журнала* может содержать:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Сборка во время разработки

В проектах IDE проекты. vcxproj используют набор целевых объектов MSBuild для получения дополнительных сведений из проекта и повторного создания выходных файлов. Некоторые из этих целей используются только в сборках времени разработки, но многие из них используются как в регулярных сборках, так и во время разработки.

Общие сведения о сборках времени разработки см. в документации CPS для [сборок времени разработки](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Эта документация частично применима только к Visual C++ным проектам.

`CompileDesignTime` `Compile` Целевые объекты и, упомянутые в документации по сборкам времени разработки, никогда не запускаются для проектов с поддержкой vcxproj. В проектах Visual C++. vcxproj для получения информации IntelliSense используются различные целевые объекты времени разработки.

### <a name="design-time-targets-for-intellisense-information"></a>Целевые объекты времени разработки для данных IntelliSense

Целевые объекты времени разработки, используемые в проектах. vcxproj, определяются в `$(VCTargetsPath)` \\ *Microsoft. cpp. DesignTime. targets*.

`GetClCommandLines`Целевой объект собирает параметры компилятора для IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` — целевые объекты только для времени разработки, необходимые для инициализации сборки во время разработки. Помимо прочего, эти целевые объекты отключают некоторые стандартные функции сборки для повышения производительности.

- `ComputeCompileInputsTargets` — набор целевых объектов, которые изменяют параметры и элементы компилятора. Эти целевые объекты выполняются как во время разработки, так и в обычных сборках.

Целевой объект вызывает `CLCommandLine` задачу, чтобы создать командную строку, используемую для IntelliSense. Опять же, несмотря на свое имя, оно может работать не только с параметрами CL, но также и с параметрами Clang и GCC. Тип переключателей компилятора управляется `ClangMode` свойством.

В настоящее время Командная строка, создаваемая `CLCommandLine` задачей, всегда использует параметры CL (даже в режиме Clang), так как механизм IntelliSense упрощает синтаксический анализ.

Если вы добавляете целевой объект, который выполняется перед компиляцией, как обычный или во время разработки, убедитесь, что он не нарушает сборки времени разработки или не влияет на производительность. Самый простой способ протестировать цель — открыть командную строку разработчика и выполнить следующую команду:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Эта команда создает подробный журнал сборки, *MSBuild. log*, содержащий сводку по производительности для целевых объектов и задач в конце.

Обязательно используйте `Condition ="'$(DesignTimeBuild)' != 'true'"` во всех операциях, которые имеют смысл только для обычных сборок, а не для сборок времени разработки.

### <a name="design-time-targets-that-generate-sources"></a>Целевые объекты времени разработки, которые создают источники

*Эта функция отключена по умолчанию для настольных машинных проектов и сейчас не поддерживается в кэшированных проектах*.

Если `GeneratorTarget` для элемента проекта определены метаданные, целевой объект запускается автоматически при загрузке проекта и изменении исходного файла.

::: moniker range="vs-2017"

Например, чтобы автоматически создать файлы. cpp или. h из файлов XAML, `$(VSInstallDir)` \\  \\  \\  \\  \\ \* \\ файлы *Microsoft. Windows. UI. XAML. cpp* .

::: moniker-end

::: moniker range=">=vs-2019"

Например, чтобы автоматически создать файлы. cpp или. h из файлов XAML, `$(VSInstallDir)` \\  \\  \\  \\  \\ \* \\ файлы *Microsoft. Windows. UI. XAML. cpp* . виндовсксамл.

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Чтобы использовать `Task.HostObject` для получения несохраненного содержимого исходных файлов, целевые объекты и задачи должны быть зарегистрированы как [мсбуилдхостобжектс](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017&preserve-view=true) для указанных проектов в pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++ расширяемость проектов в интегрированной среде разработки Visual Studio

Система проектов Visual C++ основана на [системе проектов VS](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)и использует ее точки расширения. Однако реализация иерархии проекта зависит от Visual C++, а не от CPS, поэтому расширяемость иерархии ограничена элементами проекта.

### <a name="project-property-pages"></a>Страницы свойств проекта

Общие сведения о проектировании см. в статье [многоплатформенная Настройка платформы для проектов VC + +](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

Проще говоря, страницы свойств, отображаемые в диалоговом окне **свойств проекта** для проекта C++, определяются файлами *правил* . Файл правил задает набор свойств, отображаемых на странице свойств, а также то, как и где они должны сохраняться в файле проекта. Файлы правил — это XML-файлы, которые используют формат XAML. Типы, используемые для их сериализации, описаны в [Microsoft. Build. Framework. ксамлтипес](/dotnet/api/microsoft.build.framework.xamltypes). Дополнительные сведения об использовании файлов правил в проектах см. в разделе [файлы правил XML страницы свойств](/cpp/build/reference/property-page-xml-files).

Файлы правил должны быть добавлены в `PropertyPageSchema` группу элементов:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` Метаданные ограничивают видимость правил, которые также управляются типом правила и могут иметь одно из следующих значений:

`Project` | `File` | `PropertySheet`

CPS поддерживает другие значения для типа контекста, но они не используются в проектах Visual C++.

Если правило должно быть видимым более чем в одном контексте, используйте точку с запятой (**;**), чтобы разделить значения контекста, как показано ниже:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Формат правила и основные типы

Формат правила прост, поэтому в этом разделе описываются только те атрибуты, которые влияют на то, как оно выглядит в пользовательском интерфейсе.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate`Атрибут определяет, как правило отображается в диалоговом окне **страницы свойств** . Атрибут может иметь одно из следующих значений:

| attribute | Описание |
|------------| - |
| `generic` | Все свойства отображаются на одной странице в разделе заголовки категорий.<br/>Правило может быть видимым для `Project` `PropertySheet` контекстов и `File` .<br/><br/> Пример: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Категории отображаются как вложенные страницы.<br/>Правило может быть видимым во всех контекстах: `Project` `PropertySheet` и `File` .<br/>Правило отображается в свойствах проекта только в том случае, если в проекте есть элементы с `ItemType` определенным в `Rule.DataSource` , если только имя правила не включено в `ProjectTools` группу элементов.<br/><br/>Пример: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | Страница отображается как часть страницы Отладка.<br/>Категории в данный момент игнорируются.<br/>Имя правила должно совпадать с атрибутом объекта MEF средства запуска отладки `ExportDebugger` .<br/><br/>Пример: `$(VCTargetsPath)` \\  \\ *\_ локальный \_windows.xmlотладчика* 1033 |
| *настройки* | Настраиваемый шаблон. Имя шаблона должно соответствовать `ExportPropertyPageUIFactoryProvider` атрибуту `PropertyPageUIFactoryProvider` объекта MEF. См. **Microsoft. VisualStudio. прожектсистем. Designers. Properties. ипропертипажеуифакторипровидер**.<br/><br/> Пример: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Если правило использует один из шаблонов на основе сетки свойств, оно может использовать эти точки расширения для своих свойств:

- [Редакторы значений свойств](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Поставщик динамических значений enum](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Расширение правила

Если вы хотите использовать существующее правило, но необходимо добавить или удалить (то есть скрыть) всего несколько свойств, можно создать [правило расширения](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Переопределение правила

Возможно, вы хотите, чтобы набор инструментов использовал большинство правил проекта по умолчанию, но можно заменить только один или несколько из них. Например, предположим, что нужно изменить только правило C/C++ для отображения различных параметров компилятора. Можно указать новое правило с тем же именем и отображаемым именем, что и у существующего правила, и включить его в `PropertyPageSchema` группу элементов после импорта целевых объектов cpp по умолчанию. В проекте используется только одно правило с заданным именем, а Последнее из них включено в `PropertyPageSchema` группу элементов.

#### <a name="project-items"></a>Элементы проекта

Файл *ProjectItemsSchema.xml* определяет `ContentType` `ItemType` значения и для элементов, которые обрабатываются как элементы проекта, и определяет `FileExtension` элементы для определения группы элементов, к которой добавляется новый файл.

Файл прожектитемссчема по умолчанию находится в `$(VCTargetsPath)` \\ *1033* \\ *ProjectItemsSchema.xml*. Чтобы расширить его, необходимо создать файл схемы с новым именем, например *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Затем в файле targets добавьте:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Пример: `$(VCTargetsPath)` \\ *буилдкустомизатионс* \\ *masm.xml*

### <a name="debuggers"></a>Отладчики

Служба отладки в Visual Studio поддерживает расширяемость для модуля отладки. Дополнительные сведения см. в следующих примерах:

- [Миенгине, проект с открытым исходным кодом, поддерживающий отладку lldb](https://github.com/Microsoft/MIEngine)

- [Пример модуля отладки Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Чтобы указать модули отладки и другие свойства для сеанса отладки, необходимо реализовать компонент MEF средства [отладки](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) и добавить `debugger` правило. Пример см `$(VCTargetsPath)` \\ \\ \_ . в файле localwindows.xml отладчика 1033 \_ .

### <a name="deploy"></a>Развертывание

в проектах. vcxproj для [развертывания поставщиков](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md)используется расширяемость системы проектов Visual Studio.

### <a name="build-up-to-date-check"></a>Проверка сборки

По умолчанию для проверки сборки требуется чтение журналов отслеживания и запись журналов. журналы, которые будут созданы в `$(TlogLocation)` папке во время сборки для всех входных и выходных данных сборки.

Использование пользовательской проверки на актуальную версию:

1. Отключите проверку по умолчанию на обновленную версию, добавив `NoVCDefaultBuildUpToDateCheckProvider` возможность в файл *набора инструментов. targets* :

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Реализуйте собственный [ибуилдуптодатечеккпровидер](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Обновление проекта

### <a name="default-vcxproj-project-upgrader"></a>Обновление проекта по умолчанию. vcxproj

Модуль обновления проекта по умолчанию. vcxproj изменяет `PlatformToolset` `ApplicationTypeRevision` версию набора инструментов MSBuild и платформу .NET Framework. Последние два значения всегда изменяются в версии Visual Studio по умолчанию, но их `PlatformToolset` `ApplicationTypeRevision` можно контролировать с помощью специальных свойств MSBuild.

Этот критерий используется для определения возможности обновления проекта.

1. Для проектов, которые определяют `ApplicationType` и `ApplicationTypeRevision` , существует папка с номером редакции выше текущей.

1. Свойство `_UpgradePlatformToolsetFor_<safe_toolset_name>` определено для текущего набора инструментов, а его значение не равно текущему набору инструментов.

   В этих именах свойств *\<safe_toolset_name>* представляет имя набора инструментов, в котором все символы, отличные от буквенно-цифровых, заменены символом подчеркивания ( **\_** ).

Если проект можно обновить, он участвует в *перенацелении решения*. Дополнительные сведения см. в разделе [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Если необходимо задекоративировать имена проектов в **Обозреватель решений** если в проектах используется определенный набор инструментов, определите `_PlatformToolsetShortNameFor_<safe_toolset_name>` свойство.

Примеры `_UpgradePlatformToolsetFor_<safe_toolset_name>` `_PlatformToolsetShortNameFor_<safe_toolset_name>` определений свойств и см. в файле *Microsoft. cpp. Default. props* . Примеры использования см `$(VCTargetPath)` \\ . в файле *Microsoft. cpp. Platform. targets* .

### <a name="custom-project-upgrader"></a>Пользовательский метод обновления проекта

Чтобы использовать пользовательский объект обновления проекта, реализуйте компонент MEF, как показано ниже:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Код может импортировать и вызвать объект обновления по умолчанию. vcxproj:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` определяется в *Microsoft.VisualStudio.ProjectSystem.VS.dll* и аналогичен `IVsRetargetProjectAsync` .

Определите `VCProjectUpgraderObjectName` свойство, чтобы система проектов предскажета использовать пользовательский объект обновления:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Отключить обновление проекта

Чтобы отключить обновление проекта, используйте `NoUpgrade` значение.

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Кэш проектов и расширяемость

Для повышения производительности при работе с большими решениями C++ в Visual Studio 2017 был введен [кэш проекта](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) . Он реализуется как база данных SQLite, заполненная данными проекта, а затем используется для загрузки проектов без загрузки проектов MSBuild или CPS в память.

Поскольку отсутствуют объекты CPS для проектов с расширением VCXPROJ, загруженных из кэша, компоненты MEF расширения, которые импортируются `UnconfiguredProject` или `ConfiguredProject` не могут быть созданы. Для поддержки расширяемости кэш проекта не используется, когда Visual Studio определяет, использует ли проект расширения MEF (или, скорее всего, будет использоваться).

Эти типы проектов всегда полностью загружены и имеют объекты CPS в памяти, поэтому для них создаются все расширения MEF:

- Запускаемые проекты

- Проекты, у которых есть пользовательский проект обновления, то есть они определяют `VCProjectUpgraderObjectName` свойство

- Проекты, которые не предназначены для настольных окон, то есть определяют `ApplicationType` свойство

- Проекты общих элементов (. vcxitems) и любые проекты, ссылающиеся на них, путем импорта проектов vcxitems.

Если ни одно из этих условий не обнаружено, создается кэш проекта. Кэш включает все данные проекта MSBuild, необходимые для ответа `get` на запросы в `VCProjectEngine` интерфейсах. Это означает, что все изменения на уровне PROPS и targets в MSBuild, выполненные расширением, должны просто работать в проектах, загруженных из кэша.

## <a name="shipping-your-extension"></a>Доставка расширения

Сведения о создании файлов VSIX см. в разделе [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Сведения о добавлении файлов в специальные места установки, например для добавления файлов в `$(VCTargetsPath)` , см. в разделе [Установка за пределами папки Extensions](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Дополнительные ресурсы

Система Microsoft Build ([MSBuild](../msbuild/msbuild.md)) предоставляет механизм сборки и расширяемый формат на основе XML для файлов проекта. Вы должны быть знакомы с основными [понятиями MSBuild](../msbuild/msbuild-concepts.md) и с тем, как работает [MSBuild для Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) , чтобы расширить Visual C++ систему проектов.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) предоставляет API расширения, используемые CPS и системой проектов Visual C++. Общие сведения об использовании MEF в CPS см. в разделе [CPS и MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) в [ВСПРОЖЕКТСИСТЕМ обзоре MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Можно настроить существующую систему сборки для добавления шагов сборки или новых типов файлов. Дополнительные сведения см. в разделе [Общие сведения о MSBuild (Visual C++)](/cpp/build/reference/msbuild-visual-cpp-overview) и [Работа со свойствами проекта](/cpp/build/working-with-project-properties).
