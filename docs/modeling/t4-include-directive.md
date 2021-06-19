---
title: Директива Include T4
description: 'Сведения о том, как использовать текстовый шаблон в Visual Studio, можно включить текст из другого файла с помощью @include директивы < # # >.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7361d92b05fd6838d20b32ea9f0b3b14530266fa
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386310"
---
# <a name="t4-include-directive"></a>Директива Include T4

В текстовом шаблоне в Visual Studio можно включить текст из другого файла с помощью `<#@include#>` директивы. Директивы `include` можно разместить в любом месте текстового шаблона перед первым блоком возможностей класса `<#+ ... #>`. Включенные файлы также могут содержать директивы `include` и другие директивы. Это позволяет использовать один и тот же код шаблона и стандартный текст в нескольких шаблонах.

## <a name="using-include-directives"></a>Использование директив Include

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` может быть абсолютным или относительным для текущего файла шаблона.

   Кроме того, конкретные расширения Visual Studio могут указывать собственные каталоги для поиска включаемых файлов. Например, если вы установили пакет SDK визуализации и моделирования (средства DSL), в список включения добавляется следующая папка: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates` .

   Эти дополнительные папки включения могут зависеть от расширения включающего файла. Например, папка включения DSL Tools доступна только для включающих файлов с расширением `.tt`.

- `filePath` может включать переменные среды, отделенные знаком "%". Пример.

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- В имени включенного файла не обязательно использовать расширение `".tt"`.

   Для включенных файлов можно использовать другое расширение, например `".t4"`. Это связано с тем, что при добавлении `.tt` файла в проект Visual Studio автоматически присваивает свойству **пользовательского инструмента** значение `TextTemplatingFileGenerator` . Как правило, не нужно, чтобы включенные файлы преобразовывались по отдельности.

   С другой стороны, нужно помнить, что в некоторых случаях расширение файла влияет на то, в каких дополнительных папках будет выполнен поиск файлов включения. Это может оказаться важным при наличии включенного файла, содержащего другие файлы.

- Включенное содержимое обрабатывается почти так же, как если бы оно было частью включающего текстового шаблона. Однако можно включить файл, содержащий блок возможностей класса `<#+...#>`, даже если за директивой `include` следуют обычный текст и стандартные управляющие блоки.

- Используйте, `once="true"` чтобы убедиться, что шаблон включен только один раз, даже если он вызывается из нескольких других включаемых файлов.

   Эта функция упрощает создание библиотеки многократно используемых фрагментов T4, которые можно включить в, не заботясь о том, что они уже включены в какой-либо другой фрагмент.  Например, предположим, что имеется библиотека очень детализированных фрагментов кода, которые связаны с обработкой шаблонов и созданием C#.  В свою очередь, они используются некоторыми другими специальными служебными программами, такими как создание исключений, которые затем можно использовать из любого другого шаблона приложения. Если нарисовать граф зависимостей, можно увидеть, что некоторые фрагменты кода были бы включены несколько раз. Но параметр `once` предотвращает последующие включения.

  **MyTextTemplate.tt:**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>
```

 **TextFile1.t4:**

```
   Output Message 2 (from included file).
<#@ include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>
```

 **TextFile2.t4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>
```

 **Сгенерированный в результате файл, MyTextTemplate.txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a> Использование свойств проекта в MSBuild и Visual Studio
 Хотя в директиве include можно использовать макросы Visual Studio, такие как $ (SolutionDir), они не работают в MSBuild. Если требуется преобразовывать шаблоны на компьютере сборки, необходимо использовать свойства проекта.

 Измените CSPROJ- или VBPROJ-файл для определения свойства проекта. В этом примере определяется свойство с именем `myIncludeFolder`.

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Теперь можно использовать свойство проекта в текстовых шаблонах, которые будут правильно преобразовываться как в Visual Studio, так и в MSBuild:

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```
