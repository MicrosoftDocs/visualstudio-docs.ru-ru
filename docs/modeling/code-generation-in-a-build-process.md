---
title: Создание кода в процессе построения
description: Узнайте, как можно вызывать преобразование текста как часть процесса сборки решения Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7db1b41df5007678c84be71f34aea110c04348c1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389752"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Вызов преобразования текста в процессе сборки

[Преобразование текста](../modeling/code-generation-and-t4-text-templates.md) можно вызвать как часть [процесса сборки](/azure/devops/pipelines/index) решения Visual Studio. Имеются задачи сборки, которые специализируются на преобразовании текста. Задачи сборки T4 запускают выполнение текстовых шаблонов времени разработки, а также компилируют текстовые шаблоны времени выполнения (предварительно обработанные).

Возможности задач построения несколько отличаются в зависимости от используемого обработчика сборки. При сборке решения в Visual Studio текстовый шаблон может получить доступ к API Visual Studio (EnvDTE), если задан атрибут [hostspecific = "true"](../modeling/t4-template-directive.md) . Но это не верно при построении решения из командной строки или при запуске серверной сборки с помощью Visual Studio. В таких случаях сборка выполняется в MSBuild и используется другой узел T4. Это означает, что при создании текстового шаблона с помощью MSBuild доступ к таким файлам, как имена файлов проекта, невозможен. Тем не менее [сведения о среде можно передать в текстовые шаблоны и обработчики директив с помощью параметров сборки](#parameters).

## <a name="configure-your-machines"></a><a name="buildserver"></a> Настройка компьютеров

Чтобы включить задачи сборки на компьютере разработчика, установите пакет SDK моделирования для Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Если [сервер сборки](/azure/devops/pipelines/agents/agents) запущен на компьютере, на котором не установлен Visual Studio, скопируйте следующие файлы на компьютер сборки с компьютера разработки:

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.15.0.dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.Interfaces.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.VSHost.15.0.dll

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft.VisualStudio.TextTemplating.Modeling.15.0.dll

> [!TIP]
> Если вы получаете `MissingMethodException` метод для метода Microsoft. CodeAnalysis при запуске целевых объектов сборки TextTemplating на сервере сборки, убедитесь, что сборки Roslyn находятся в каталоге с именем *Roslyn* , который находится в том же каталоге, что и исполняемый файл сборки (например, *msbuild.exe*).

## <a name="edit-the-project-file"></a>Изменение файла проекта

Измените файл проекта, чтобы настроить некоторые функции в MSBuild, например Импорт целевых объектов преобразования текста.

В **Обозреватель решений** в контекстном меню проекта выберите пункт **выгрузить** . Это позволит изменить CSPROJ- или VBPROJ-файл в редакторе XML. Завершив редактирование, нажмите кнопку **перезагрузить**.

## <a name="import-the-text-transformation-targets"></a>Импорт целевых объектов преобразования текста

В VBPROJ- или CSPROJ-файле найдите строку, аналогичную следующей:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- или -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

После этой строки вставьте директиву импорта текстового шаблона:

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

## <a name="transform-templates-in-a-build"></a>Преобразование шаблонов в сборке

Предусмотрено несколько свойств, которые можно вставлять в файл проекта для управления задачей преобразования.

- Выполнять задачу преобразования в начале каждой сборки:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Перезапишите файлы, доступные только для чтения, например, так как они не извлечены.

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Каждый раз преобразовывать все шаблоны:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     По умолчанию задача T4 MSBuild повторно создает выходной файл, если он старше:

     - файл шаблона
     - Все включаемые файлы
     - все файлы, которые ранее были считаны шаблоном или используемым процессором директив

     Это более мощный тест зависимостей, чем используемый командой **преобразовать все шаблоны** в Visual Studio, который сравнивает только даты шаблона и выходного файла.

Чтобы выполнить только преобразования текста в проекте, вызовите задачу TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Чтобы преобразовать определенный текстовый шаблон:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

В команде TransformFile можно использовать символы подстановки:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Система управления версиями

Не существует специальной встроенной интеграции с системой управления версиями. Однако можно добавить собственные расширения, например, чтобы извлечь и вернуть созданный файл. По умолчанию задача преобразования текста позволяет избежать перезаписи файла, помеченного как доступное только для чтения. При обнаружении такого файла в список ошибок Visual Studio регистрируется ошибка, и задача завершается с ошибкой.

Чтобы указать, что доступные только для чтения файлы следует перезаписывать, вставьте такое свойство:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Если вы не настроили шаг обработки, в список ошибок при перезаписи файла предупреждение будет записано в журнал.

## <a name="customize-the-build-process"></a>Настройка процесса сборки

Преобразование текста производится перед выполнением других задач в процессе сборки. Задачи, которые вызываются до и после преобразования, можно задавать, устанавливая свойства `$(BeforeTransform)` и `$(AfterTransform)`.

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
</PropertyGroup>
<Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
</Target>
<Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
</Target>
```

В свойстве `AfterTransform` можно указывать списки файлов:

- GeneratedFiles – список файлов, сгенерированных данным процессом. Для файлов, которые перезаписали существующие файлы только для чтения, `%(GeneratedFiles.ReadOnlyFileOverwritten)` будут иметь значение true. Эти файлы можно извлекать из системы управления версиями.

- NonGeneratedFiles – список доступных только для чтения файлов, которые не были перезаписаны.

Например, можно определить задачу для извлечения GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath и OutputFileName

Эти свойства используются только в MSBuild. Они не влияют на создание кода в Visual Studio. Они перенаправляют созданный выходной файл в другую папку или файл. Целевая папка должна уже существовать.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Полезной папкой для перенаправления является `$(IntermediateOutputPath)` .

Если указать имя выходного файла, оно имеет приоритет над расширением, заданным в директиве Output в шаблонах.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Указывать OutputFileName или OutputFilePath не рекомендуется, если вы также преобразуете шаблоны в Visual Studio, используя **Преобразование ALL** или запуск генератора одиночных файлов. В итоге вы получите разные пути к файлам в зависимости от того, как вы активировали преобразование. Это может сбить с толку.

## <a name="add-reference-and-include-paths"></a>Добавление ссылок и путей включения

Узел имеет набор путей по умолчанию, по которым производится поиск сборок, указанных в шаблонах. Для добавления в этот набор:

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Чтобы задать папки, в которых будет производиться поиск включаемых файлов, укажите список через точку с запятой. Обычно производится добавление в существующий список папок.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="pass-build-context-data-into-the-templates"></a><a name="parameters"></a> Передача данных контекста сборки в шаблоны

Можно задать значения параметров в файле проекта. Например, можно передать свойства [сборки](../msbuild/msbuild-properties.md) и [переменные среды](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

В текстовом шаблоне задайте атрибут `hostspecific` в директиве template. Используйте директиву [Parameter](../modeling/t4-parameter-directive.md) для получения значений:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

В обработчике директив можно вызвать метод [итексттемплатинженгинехост. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` Получает данные `T4ParameterValues` только при использовании MSBuild. При преобразовании шаблона с помощью Visual Studio параметры имеют значения по умолчанию.

## <a name="use-project-properties-in-assembly-and-include-directives"></a><a name="msbuild"></a> Использование свойств проекта в директивах сборки и включения

Макросы Visual Studio, такие как **$ (SolutionDir)** , не работают в MSBuild. Вместо этого можно использовать свойства проекта.

Измените файл *CSPROJ* или *VBPROJ* , чтобы определить свойство проекта. В этом примере определяется свойство с именем **милибфолдер**:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

Теперь можно использовать ваше свойство проекта в директивах assembly и include:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

Эти директивы получают значения из T4parameterValues как в узлах MSBuild, так и в узлах Visual Studio.

## <a name="q--a"></a>Вопросы и ответы

**Зачем нужно преобразовывать шаблоны на сервере сборки? Я уже преписал шаблоны в Visual Studio, прежде чем я вернул код.**

При обновлении включаемого файла или другого файла, прочитанного шаблоном, Visual Studio не преобразует файл автоматически. Преобразование шаблонов в рамках сборки гарантирует актуальность всех компонентов.

**Имеют ли другие варианты преобразования текстовых шаблонов?**

- [Служебную программу TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) можно использовать в скриптах команд. В большинстве случаев проще использовать MSBuild.

- [Вызов преобразования текста в расширении Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md).

- [Текстовые шаблоны времени разработки](../modeling/design-time-code-generation-by-using-t4-text-templates.md) преобразуются в Visual Studio.

- [Текстовые шаблоны времени выполнения](../modeling/run-time-text-generation-with-t4-text-templates.md) преобразуются во время выполнения в приложении.

## <a name="see-also"></a>См. также

::: moniker range="vs-2017"

- В шаблоне T4 MSbuild есть хорошие рекомендации по адресу `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- В шаблоне T4 MSbuild есть хорошие рекомендации по адресу `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)
