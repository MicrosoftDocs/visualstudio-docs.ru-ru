---
title: Задача Csc | Документы Майкрософт
description: В этой статье описывается задача Csc MSBuild, которая создает программу-оболочку для компилятора C# (csc.exe) и файлы с расширениями PRODUCES, EXE, DLL или NETMODULE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10a63b114379f56ca5f253f853a1ff6bdd6c60dc
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588479"
---
# <a name="csc-task"></a>Csc - задача

Использует программу-оболочку для файла *csc.exe* и создает исполняемые файлы (*EXE*-файлы), библиотеки динамической компоновки (*DLL*-файлы) или модули кода (*NETMODULE*-файлы). Дополнительные сведения о программе *csc.exe* см. в разделе [Параметры компилятора C#](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи `Csc` .

| Параметр | Описание |
|------------------------------| - |
| `AdditionalLibPaths` | Необязательный параметр `String[]`.<br /><br /> Задает дополнительные каталоги для поиска ссылок. Дополнительные сведения см. в разделе [-lib (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Необязательный параметр `String`.<br /><br /> Задает один или несколько модулей, которые должны быть частью сборки. Дополнительные сведения см. в разделе [-addmodule (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Необязательный параметр `Boolean`.<br /><br /> Если этот параметр равен `true`, то компилируется код, в котором используется ключевое слово [unsafe](/dotnet/csharp/language-reference/keywords/unsafe). Дополнительные сведения см. в разделе [-unsafe (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Необязательный параметр `String`.<br /><br /> Задает файл конфигурации приложения, содержащий параметры привязки сборки. |
| `BaseAddress` | Необязательный параметр `String`.<br /><br /> Указывает предпочтительный базовый адрес для загрузки DLL. Базовый адрес по умолчанию для библиотеки DLL задается в среде CLR платформы .NET Framework. Дополнительные сведения см. в разделе [-baseaddress (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Необязательный параметр `Boolean`.<br /><br /> Указывает, должны ли целочисленные арифметические операции, вызывающие переполнение типа данных, вызывать исключение во время выполнения. Дополнительные сведения см. в разделе [-checked (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Необязательный параметр `Int32`.<br /><br /> Задает кодовую страницу, которая будет использоваться для всех файлов исходного кода при компиляции. Дополнительные сведения см. в разделе [-codepage (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Необязательный параметр `String`.<br /><br /> Задает тип отладки. `DebugType` может иметь значение `full`или `pdbonly`. По умолчанию задано значение `full`, разрешающее подключение отладчика к исполняемой программе. Значение `pdbonly` разрешает отладку исходного кода при запуске программы в отладчике, но при этом ассемблерный код отображается только при подключении исполняемой программы к отладчику.<br /><br /> Этот параметр переопределяет параметр `EmitDebugInformation`.<br /><br /> Дополнительные сведения см. в разделе [-debug (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Необязательный параметр `String`.<br /><br /> Определяет символы препроцессора. Дополнительные сведения см. в разделе [-define (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Необязательный параметр `Boolean`.<br /><br /> Значение `true` предписывает лишь поместить в сборку открытый ключ. Значение `false` предписывает создание полностью подписанной сборки.<br /><br /> Этот параметр не оказывает никакого эффекта, если не используется вместе с параметром `KeyFile` или `KeyContainer`.<br /><br /> Дополнительные сведения см. в разделе [-delaysign (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Необязательный параметр `Boolean`.<br/><br/> Если задано значение `true`, компилятор будет выдавать сборку, чье двоичное содержимое идентично в разных компиляциях, если входные данные идентичны.<br/><br/>Дополнительные сведения см. в разделе [-deterministic (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Необязательный параметр `String`.<br /><br /> Задает список предупреждений, которые следует отключить. Дополнительные сведения см. в разделе [-nowarn (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Необязательный параметр `String`.<br /><br /> Обрабатывает комментарии к документации в XML-файл. Дополнительные сведения см. в разделе [-doc (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmbedAllSources` | Необязательный параметр `Boolean`.<br /><br /> Внедрение всех исходных файлов в PDB-файл. Дополнительные сведения см. в разделе [-embed (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically). |
| `EmitDebugInformation` | Необязательный параметр `Boolean`.<br /><br /> Если этот параметр равен `true`, задача генерирует отладочную информацию и помещает ее в файл базы данных программы (PDB-файл). Если задано значение `false`, задача не генерирует отладочную информацию. Значение по умолчанию — `false`. Дополнительные сведения см. в разделе [-debug (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Необязательный параметр `String`.<br /><br /> Предоставляет удобный способ для сообщения о внутренней ошибке C# в корпорацию Майкрософт. Этот параметр может иметь значение `prompt`, `send` или `none`. Если установлено значение `prompt`, в случае внутренней ошибки компилятора будет выведено сообщение с предложением отправить электронный отчет об ошибке в корпорацию Майкрософт. Если установлено значение `send`, сообщение об ошибке отправляется автоматически. Если установлено значение `none`, отчет об ошибке выводится только в текстовых выходных данных компилятора. Значение по умолчанию — `none`. Дополнительные сведения см. в разделе [-errorreport (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Необязательный параметр `Int32`.<br /><br /> Задает размер разделов в выходном файле. Дополнительные сведения см. в разделе [-filealign (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Необязательный параметр `Boolean`.<br /><br /> Если этот параметр равен `true`, то в выходных данных компилятора задается абсолютный путь к файлу. Если установлено значение `false`, задается имя файла. Значение по умолчанию — `false`. Дополнительные сведения см. в разделе [-fullpaths (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Необязательный параметр `String`.<br /><br /> Задает имя контейнера криптографического ключа. Дополнительные сведения см. в разделе [-keycontainer (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Необязательный параметр `String`.<br /><br /> Задает имя файла, содержащего криптографический ключ. Дополнительные сведения см. в разделе [-keyfile (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Необязательный параметр `String`.<br /><br /> Задает используемую версию языка. Дополнительные сведения см. в разделе [-langversion (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Создается ссылка на ресурс .NET Framework в выходном файле. Файл ресурса не помещается в выходной файл.<br /><br /> Элементы, передаваемые в этот параметр, могут иметь необязательные метаданные `LogicalName` и `Access`. `LogicalName` соответствует аргументу `identifier` параметра `/linkresource`, а `Access` соответствует аргументу `accessibility-modifier`. Дополнительные сведения см. в разделе [-linkresource (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Необязательный параметр `String`.<br /><br /> Указывает расположение метода `Main`. Дополнительные сведения см. в разделе [-main (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Необязательный параметр `String`.<br /><br /> Задает имя сборки, частью которой будет этот модуль. |
| `NoConfig` | Необязательный параметр `Boolean`.<br /><br /> Значение `true` предписывает компилятору не использовать файл *csc.rsp*. Дополнительные сведения см. в разделе [-noconfig (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Необязательный параметр `Boolean`.<br /><br /> Если этот параметр равен `true`, отображение заголовка компилятора отключается. Дополнительные сведения см. в разделе [-nologo (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Необязательный параметр `Boolean`.<br /><br /> Значение `true` отключает импорт библиотеки *mscorlib.dll*, определяющей все пространство имен System. Используйте этот параметр, если вы хотите определить или создать собственное пространство имен System и соответствующие объекты. Дополнительные сведения см. в разделе [-nostdlib (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Необязательный параметр `Boolean`.<br /><br /> Если значение `true`, манифест Win32 по умолчанию не включается. |
| `Optimize` | Необязательный параметр `Boolean`.<br /><br /> Значение `true` включает оптимизации. Значение `false` отключает оптимизации. Дополнительные сведения см. в разделе [-optimize (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Необязательный выходной параметр `String`.<br /><br /> Задает имя выходного файла. Дополнительные сведения см. в разделе [-out (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Необязательный параметр `String`.<br /><br /> Задает имя выходного файла базовой сборки. Дополнительные сведения см. в разделе [-refout (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Необязательный параметр `String`.<br /><br /> Задает имя файла отладочной информации. По умолчанию используется имя файла выходных данных с расширением *.pdb*. |
| `Platform` | Необязательный параметр `String`.<br /><br /> Указывает целевую платформу процессора для выходного файла. Этот параметр может иметь значение `x86`, `x64` или `anycpu`. Значение по умолчанию — `anycpu`. Дополнительные сведения см. в разделе [-platform (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Вызывает импорт задачей информации об открытых типах из заданных элементов в текущий проект. Дополнительные сведения см. в разделе [-reference (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Вы можете задать псевдоним ссылки C# в файле MSBuild, добавив метаданные `Aliases` к исходному элементу "Reference". Например, требуется установить псевдоним LS1 в следующей командной строке CSC.<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Для этого используется следующий код.<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Внедряет ресурс .NET Framework в выходной файл.<br /><br /> Элементы, передаваемые в этот параметр, могут иметь необязательные метаданные `LogicalName` и `Access`. `LogicalName` соответствует аргументу `identifier` параметра `/resource`, а `Access` соответствует аргументу `accessibility-modifier`. Дополнительные сведения см. в разделе [-resource (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Необязательный параметр `String`.<br /><br /> Задает файл ответов, содержащий команды для этой задачи. Дополнительные сведения см. в документации синтаксиса [@ (указание файла ответа)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает один или несколько исходных файлов C#. |
| `TargetType` | Необязательный параметр `String`.<br /><br /> Задает формат выходного файла. Этот параметр может принимать одно из следующих значений: `library` (создается библиотека кода), `exe` (создается консольное приложение), `module` (создается модуль) или `winexe` (создается программа Windows). Значение по умолчанию — `library`. Дополнительные сведения см. в разделе [-target (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Необязательный параметр `Boolean`.<br /><br /> Если этот параметр равен `true`, все предупреждения обрабатываются как ошибки. Дополнительные сведения см. в разделе [-warnaserror (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Необязательный параметр `Boolean`.<br /><br /> Предписывает задаче использовать внутрипроцессный объект компилятора, если он доступен. Используется только в Visual Studio. |
| `Utf8Output` | Необязательный параметр `Boolean`.<br /><br /> Регистрирует выходные данные компилятора в кодировке UTF-8. Дополнительные сведения см. в разделе [-utf8output (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Необязательный параметр `Int32`.<br /><br /> Задает уровень предупреждений, которые должны отображаться компилятором. Дополнительные сведения см. в разделе [-warn (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Необязательный параметр `String`.<br /><br /> Задает список предупреждений, которые следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [-warnaserror (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Этот параметр переопределяет параметр `TreatWarningsAsErrors`. |
| `WarningsNotAsErrors` | Необязательный параметр `String`.<br /><br /> Задает список предупреждений, которые не следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [-warnaserror (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Этот параметр имеет смысл только в том случае, если для параметра `TreatWarningsAsErrors` задано значение `true`. |
| `Win32Icon` | Необязательный параметр `String`.<br /><br /> Вставляет файл *ICO* в сборку, которая придает выходному файлу необходимый вид в **проводнике**. Дополнительные сведения см. в разделе [-win32icon (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Необязательный параметр `String`.<br /><br /> Задает манифест Win32, который требуется включить. |
| `Win32Resource` | Необязательный параметр `String`.<br /><br /> Вставляет файл ресурсов Win32 (*RES-файл*) в выходной файл. Дополнительные сведения см. в разделе [-win32res (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Пример

В следующем примере задача `Csc` используется для компиляции исполняемого файла из исходных файлов в коллекции элементов `Compile`.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>См. также

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Задачи](../msbuild/msbuild-tasks.md)
