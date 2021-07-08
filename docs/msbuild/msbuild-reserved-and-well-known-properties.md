---
title: Зарезервированные и стандартные свойства MSBuild | Документы Майкрософт
description: Узнайте о зарезервированных и известных свойствах MSBuild, предопределенных свойствах, которые содержат сведения о файле проекта и двоичные файлы MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2edfd4b9391beed5c379817c55871759ff02eec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384932"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Зарезервированные и стандартные свойства MSBuild

MSBuild предоставляет набор предопределенных свойств для сохранения информации о файле проекта и двоичных файлах MSBuild. Значения этих свойств вычисляются так же, как и значения других свойств MSBuild. Например, для использования свойства `MSBuildProjectFile` необходимо ввести `$(MSBuildProjectFile)`

 Для определения зарезервированных и известных свойств в MSBuild используются значения, приведенные в следующей таблице. Зарезервированные свойства переопределить нельзя, тогда как известные свойства можно переопределить с помощью свойств с идентичными именами (свойства среды, глобальные свойства или свойства, определенные в файле проекта).

## <a name="reserved-and-well-known-properties"></a>Зарезервированные и стандартные свойства

В таблице в этом разделе показаны предопределенные свойства MSBuild. Пример столбца в таблице относится к следующему примеру файла проекта. Предполагается, что он находится здесь: `C:\Source\Repos\ConsoleApp1\ConsoleApp1`. Также показаны значения этих свойств при обращении к файлу проекта, когда MSBuild вызывается без специальных параметров командной строки с установленной предварительной сборкой Visual Studio 2019 версии 16.7.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

| Свойство. | Зарезервированное или стандартное | Описание | Пример |
|----------------------------------|------------------------| - | - |
| `MSBuildBinPath` | Зарезервированное | Абсолютный путь к папке, где находятся используемые в данный момент двоичные файлы MSBuild (например, *C:\Windows\Microsoft.Net\Framework\\\<versionNumber>* ). Это свойство удобно, если вам нужно ссылаться на файлы в каталоге MSBuild.<br /><br /> Не включайте в это свойство завершающую обратную косую черту. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | Стандартное | Введено в .NET Framework 4: разницы между значениями по умолчанию `MSBuildExtensionsPath` и `MSBuildExtensionsPath32` нет. Переменной среды `MSBUILDLEGACYEXTENSIONSPATH` можно присвоить значение, отличное от null, чтобы включить поведение, соответствующее значению по умолчанию `MSBuildExtensionsPath` в предыдущих версиях.<br /><br /> В .NET Framework 3.5 и более ранних версиях значение по умолчанию `MSBuildExtensionsPath` указывает на путь к вложенной папке MSBuild в папке  *Program Files\\*  или *Program Files (x86)* , в зависимости от разрядности текущего процесса. Например, для 32-разрядного процесса на 64-разрядном компьютере это свойство указывает папку на *\Program Files (x86)* . Для 64-разрядного процесса на 64-разрядном компьютере это свойство указывает на папку *\Program Files*.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.<br /><br /> Это расположение хорошо подходит для хранения пользовательских файлов целей. Например, файлы целей можно установить в папку *\Program Files\MSBuild\MyFiles\Northwind.targets*, а затем импортировать в файлы проекта с помощью следующего XML-кода:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | Стандартное | Путь к вложенной папке MSBuild в папке *\Program Files* или *\Program Files (x86)* . Путь всегда указывает на папку *\Program Files (x86)* на 32-разрядном компьютере и на папку *\Program Files* на 64-разрядном компьютере. См. также `MSBuildExtensionsPath` и `MSBuildExtensionsPath64`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | Стандартное | Путь к вложенной папке MSBuild в папке *\Program Files*. На 64-разрядном компьютере этот путь всегда указывает на папку *\Program Files*. На 32-разрядном компьютере этот путь будет пустым. См. также `MSBuildExtensionsPath` и `MSBuildExtensionsPath32`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту. | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | Зарезервированное | Значение `true`, если MSBuild работает в интерактивном режиме и позволяет пользователям вводить данные. Этот параметр управляется параметром командной строки `-interactive`. | `false` |
| `MSBuildLastTaskResult` | Зарезервированное | Значение `true`, если предыдущая задача завершилась без ошибок (даже если были предупреждения), или значение `false`, если в предыдущей задаче были ошибки. Обычно, если в задаче возникает ошибка, эта ошибка — последнее, что происходит в проекте. Следовательно, это свойство никогда не принимает значение `false`, кроме как в следующих сценариях:<br /><br /> — Когда для атрибута `ContinueOnError`[элемента Task (MSBuild)](../msbuild/task-element-msbuild.md) задано значение `WarnAndContinue` (или `true`) или `ErrorAndContinue`.<br /><br /> — Когда `Target` имеет [элемент OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) как дочерний элемент. | `true` |
| `MSBuildNodeCount` | Зарезервированное | Максимальное количество параллельных процессов, используемых при сборке. Это значение, заданное для параметра **-maxcpucount** в командной строке. Если параметр **-maxcpucount** указан без задания значения, `MSBuildNodeCount` определяет количество процессоров в компьютере. Дополнительные сведения см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md) и статье о [параллельном создании нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). | 1 |
| `MSBuildProgramFiles32` | Зарезервированное | Расположение 32-разрядной папки программы; например, *C:\Program Files (x86)* .<br /><br /> Не включайте в это свойство завершающую обратную косую черту. | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | Зарезервированное | Полный список целей, указанных в атрибуте `DefaultTargets` элемента `Project`. Например, для следующего элемента `Project` свойство `MSBuildDefaultTargets` будет иметь значение `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | Зарезервированное | Абсолютный путь к каталогу, где располагается файл проекта, например *C:\MyCompany\MyProduct*.<br /><br /> Не включайте в это свойство завершающую обратную косую черту. | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | Зарезервированное | Значение свойства `MSBuildProjectDirectory`, за исключением корневого диска.<br /><br /> Не включайте в это свойство завершающую обратную косую черту. | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | Зарезервированное | Расширение имени файла проекта, включая точку, например *.proj*. | `.csproj`|
| `MSBuildProjectFile` | Зарезервированное | Полное имя файла проекта, включая расширение, например *MyApp.proj*. | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | Зарезервированное | Абсолютный путь к файлу проекта и его полное имя, включая расширение, например *C:\MyCompany\MyProduct\MyApp.proj*. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | Зарезервированное | Имя файла проекта без расширения, например *MyApp*. | `ConsoleApp1` |
| `MSBuildRuntimeType` | Зарезервированное | Тип текущей среды выполнения. Представлено в MSBuild 15. Значение может быть не определено (до MSBuild 15), `Full` (указывает на то, что MSBuild выполняется на платформе .NET для ПК), `Core` (указывает на то, что MSBuild выполняется на платформе .NET Core, например в `dotnet build`) или `Mono` (указывает на то, что MSBuild выполняется на платформе на Mono). | `Full` |
| `MSBuildStartupDirectory` | Зарезервированное | Абсолютный путь к каталогу, из которого вызывается MSBuild. С помощью этого свойства можно выполнять сборку всего, что находится ниже конкретной точки в дереве проекта, без создания файлов *\<dirs>.proj* в каждом каталоге. Вместо этого у вас будет только один проект — например, *c:\traversal.proj*, как показано ниже:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Чтобы выполнить сборку в любой точке дерева, введите следующее:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Не включайте в это свойство завершающую обратную косую черту. | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | Зарезервированное | Часть `MSBuildThisFileFullPath`, представляющая собой имя и расширение файла. | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | Зарезервированное | Часть `MSBuildThisFileFullPath`, представляющая собой каталог.<br /><br /> Включите в путь завершающую обратную косую черту. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | Зарезервированное | Часть `MSBuildThisFileFullPath`, представляющая собой каталог, за исключением корневого диска.<br /><br /> Включите в путь завершающую обратную косую черту. | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | Зарезервированное | Часть `MSBuildThisFileFullPath`, представляющая собой расширение имени файла. | `.csproj` |
| `MSBuildThisFileFullPath` | Зарезервированное | Абсолютный путь файла проекта или файла целей, содержащего запущенную цель.<br /><br /> Совет. В файле целей можно указать относительный путь, являющийся относительным для файла целей и не являющийся относительным для файла исходного проекта. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | Зарезервированное | Часть `MSBuildThisFileFullPath`, представляющая собой имя файла без расширения. | `ConsoleApp1` |
| `MSBuildToolsPath` | Зарезервированное | Путь установки версии MSBuild, связанной со значением `MSBuildToolsVersion`.<br /><br /> Не включайте в путь завершающую обратную косую черту.<br /><br /> Это свойство нельзя переопределить. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | Зарезервированное | Версия набора инструментов MSBuild, используемая для сборки проекта.<br /><br /> Примечание. Набор инструментов MSBuild состоит из задач, целей и средств, используемых для сборки приложения. Средства включают компиляторы *csc.exe* и *vbc.exe*. Дополнительные сведения см. в статьях [Набор инструментов MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) и [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md). | `Current` |
| `MSBuildVersion` | Зарезервированное | Версия MSBuild, используемая для сборки проекта. <br /><br/> Это свойство нельзя переопределить. При попытке сделать это будет возвращено сообщение об ошибке `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.`. | 16.11.0 |
| `MSBuildAssemblyVersion` | Зарезервировано | Версия сборок MSBuild, используемая для сборки проекта. | 16,0 |
| `MSBuildFileVersion` | Зарезервировано | Версия сборок MSBuild из 4 частей, используемая для сборки проекта. | 16.11.0.30701 |
| `MSBuildSemanticVersion` | Зарезервировано | Полная версия semver 2.0 сборок MSBuild, используемая для сборки проекта. | 16.11.0-preview-21302-05+5e37cc992 |

## <a name="names-that-conflict-with-msbuild-elements"></a>Имена, которые конфликтуют с элементами MSBuild

Помимо указанных выше, имена, соответствующие элементам языка MSBuild, не могут использоваться для определяемых пользователем свойств, элементов и метаданных элементов:

* VisualStudioProject
* целевого объекта
* PropertyGroup
* Вывод
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Нажмите кнопку
* When
* Otherwise

## <a name="see-also"></a>См. также

- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)

- [Свойства MSBuild](../msbuild/msbuild-properties.md)
