---
title: Расширение процесса сборки
description: Изучите различные способы изменения процесса сборки, чтобы контролировать и настраивать сборку проектов.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94e5680f8e8635c969e25555463a21bba069284a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055821"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Практическое руководство. Расширение процесса сборки Visual Studio

Процесс сборки Visual Studio определяется рядом файлов *.targets* MSBuild, которые импортируются в файл проекта. Один из этих импортированных файлов — *Microsoft.Common.targets* — можно расширить, чтобы выполнять настраиваемые задачи в нескольких точках в процессе сборки. В этой статье описаны два метода, которые можно использовать для расширения процесса сборки Visual Studio:

- Переопределение конкретных предварительно заданных целевых объектов, определенных в списке стандартных целевых объектов (в файле *Microsoft.Common.targets* или импортируемых им файлах).

- Переопределение свойств DependsOn, определенных в списке стандартных целевых объектов.

## <a name="override-predefined-targets"></a>Переопределение предопределенных целевых объектов

Список стандартных целевых объектов содержит набор предопределенных пустых целевых объектов, которые вызываются до и после некоторых основных целевых объектов в процессе сборки. Например, MSBuild вызывает целевой объект `BeforeBuild` перед основным целевым объектом `CoreBuild`, а целевой объект `AfterBuild` — после целевого объекта `CoreBuild`. По умолчанию пустые целевые объекты в списке стандартных целевых объектов не выполняют никаких действий, но их поведение по умолчанию можно переопределить, определив нужные целевые объекты в файле проекта, куда импортируются стандартные целевые объекты. Переопределяя предварительно заданные целевые объекты, вы можете использовать задачи MSBuild, чтобы получить больший контроль над процессом сборки.

> [!NOTE]
> В проектах в стиле SDK имеется неявная директива импорта целевых объектов *после последней строки в файле проекта*. Это означает, что переопределить целевые объекты по умолчанию можно только в том случае, если директивы импорта указаны вручную, как описано в статье [Информация об использовании пакетов SDK проекта MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Переопределение предопределенного целевого объекта

1. Выберите в списке стандартных целевых объектов предварительно заданный целевой объект, который требуется переопределить. Приведенная ниже таблица содержит полный список целевых объектов, которые можно безопасно переопределить.

2. Определите один или несколько целевых объектов в конце файла проекта, прямо перед тегом `</Project>`. Пример:

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Выполните сборку файла проекта.

В приведенной ниже таблице представлены все стандартные целевые объекты, которые можно безопасно переопределить.

|Имя целевого объекта|Описание|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после основной компиляции. Основная часть настроек выполняется в одном из этих двух целевых объектов.|
|`BeforeBuild`, `AfterBuild`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после остальной части сборки. **Примечание.** Целевые объекты `BeforeBuild` и `AfterBuild` уже определены в комментариях в конце большинства файлов проекта, поэтому вы можете легко добавлять события до и после сборки в файл проекта.|
|`BeforeRebuild`, `AfterRebuild`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после вызова основной функции перестроения. В *Microsoft.Common.targets* действует следующий порядок выполнения целевых объектов: `BeforeRebuild`, `Clean`, `Build`, а затем `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после вызова основной функции очистки.|
|`BeforePublish`, `AfterPublish`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после вызова основной функции публикация.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после разрешения ссылок на сборки.|
|`BeforeResGen`, `AfterResGen`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после создания ресурсов.|

## <a name="example-aftertargets-and-beforetargets"></a>Пример. Атрибуты AfterTargets и BeforeTargets

В приведенном ниже примере показано, как использовать атрибут `AfterTargets` для добавления пользовательского целевого объекта, который выполняет некоторые действия с выходными файлами. В данном случае он копирует выходные файлы в новую папку *CustomOutput*.  В примере также показано, как очистить файлы, созданные пользовательской операцией сборки с целевым объектом `CustomClean`, с помощью атрибута `BeforeTargets` и указать, что пользовательская операция очистки должна выполняться до целевого объекта `CoreClean`.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
     <TargetFramework>netcoreapp3.1</TargetFramework>
     <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

  <Target Name="CustomAfterBuild" AfterTargets="Build">
    <ItemGroup>
      <_FilesToCopy Include="$(OutputPath)**\*"/>
    </ItemGroup>
    <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

    <Message Text="DestFiles:
        @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

    <Copy SourceFiles="@(_FilesToCopy)"
          DestinationFiles=
          "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> Используйте имена, отличные от имен предопределенных целевых объектов, перечисленных в таблице в предыдущем разделе (например, пользовательский целевой объект сборки назван здесь `CustomAfterBuild`, а не `AfterBuild`), так как эти объекты переопределяются операцией импорта пакета SDK, в которой они определены. Вы не видите операцию импорта целевого файла, который переопределяет эти целевые объекты, но она неявно добавляется в конец файла проекта при использовании метода атрибута `Sdk` для ссылки на пакет SDK.

## <a name="override-dependson-properties"></a>Переопределение свойств DependsOn

Переопределение предопределенных целевых объектов позволяет легко расширить процесс сборки, но так как MSBuild оценивает определение целевых объектов последовательно, не существует способа запретить другому проекту, который импортирует ваш проект, переопределить целевые объекты, которые вы уже переопределили. Например, последний целевой объект `AfterBuild`, определенный в файле проекта, после импорта всех остальных проектов будет использоваться в процессе сборки.

Вы можете предусмотреть защиту от нежелательных переопределений целевых объектов, переопределив свойства DependsOn, которые используются в атрибутах `DependsOnTargets` по всему списку стандартных целевых объектов. Например, целевой объект `Build` содержит значение атрибута `DependsOnTargets`, равное `"$(BuildDependsOn)"`. Необходимо учесть следующие моменты.

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Этот фрагмент XML-кода указывает, что перед выполнением целевого объекта `Build` должны быть выполнены все целевые объекты, указанные в свойстве `BuildDependsOn`. Свойство `BuildDependsOn` определено следующим образом:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Значение этого свойства можно переопределить, объявив другое свойство с именем `BuildDependsOn` в конце файла проекта. Включив предыдущее свойство `BuildDependsOn` в новое, можно добавить новые целевые объекты в начало и конец списка целевых объектов. Пример:

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

Проекты, импортирующие ваши файлы проекта, могут переопределить эти свойства, не переопределяя внесенные вами настройки.

#### <a name="to-override-a-dependson-property"></a>Переопределение свойства DependsOn

1. Выберите в списке стандартных целевых объектов предварительно заданное свойство DependsOn, которое требуется переопределить. Приведенная ниже таблица содержит список часто переопределяемых свойств DependsOn.

2. Определите еще один экземпляр свойства или свойств в конце файла проекта. Включите исходное свойство, например `$(BuildDependsOn)`, в новое свойство.

3. Определите пользовательские целевые объекты до или после определения свойства.

4. Выполните сборку файла проекта.

### <a name="commonly-overridden-dependson-properties"></a>Часто переопределяемые свойства DependsOn

|Имя свойства|Описание|
|-------------------|-----------------|
|`BuildDependsOn`|Свойство, которое следует переопределить, если нужно вставить пользовательские целевые объекты до или после всего процесса сборки.|
|`CleanDependsOn`|Свойство, которое следует переопределить, если нужно убрать выходные данные из пользовательского процесса сборки.|
|`CompileDependsOn`|Свойство, которое следует переопределить, если нужно вставить пользовательские процессы до или после этапа компиляции.|

## <a name="example-builddependson-and-cleandependson"></a>Пример. Атрибуты BuildDependsOn и CleanDependsOn

Приведенный ниже пример похож на пример с атрибутами `BeforeTargets` и `AfterTargets`, и в нем решается аналогичная задача. В нем сборка расширяется путем добавления с помощью атрибута `BuildDependsOn` собственной задачи `CustomAfterBuild`, которая копирует выходные файлы после сборки, а также добавления соответствующей задачи `CustomClean` с помощью `CleanDependsOn`.  

В этом примере проект имеет стиль пакета SDK. Как упоминалось в примечании о проектах в стиле пакета SDK ранее в этой статье, вместо атрибута `Sdk`, применяемого средой Visual Studio при создании файлов проекта, необходимо использовать импорт вручную.

```xml
<Project>
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk"/>

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk"/>

  <PropertyGroup>
    <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

  <Target Name="CustomAfterBuild">
    <ItemGroup>
      <_FilesToCopy Include="$(OutputPath)**\*"/>
    </ItemGroup>
    <Message Importance="high" Text="_FilesToCopy: @(_FilesToCopy)"/>

    <Message Text="DestFiles:
      @(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

    <Copy SourceFiles="@(_FilesToCopy)"
          DestinationFiles="@(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Importance="high" Text="Inside Custom Clean"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files="@(_CustomFilesToDelete)"/>
  </Target>
</Project>
```

Порядок элементов важен. Элементы `BuildDependsOn` и `CleanDependsOn` должны следовать после импорта стандартного файла целей построения пакета SDK.

## <a name="see-also"></a>Дополнительно

- [интеграция Visual Studio](../msbuild/visual-studio-integration-msbuild.md);
- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
- [TARGETS-файлы](../msbuild/msbuild-dot-targets-files.md)
