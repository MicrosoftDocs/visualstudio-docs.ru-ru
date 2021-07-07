---
title: Задача Delete | Документация Майкрософт
description: Сведения о параметрах и особенностях использования задачи Delete MSBuild для удаления указанных файлов.
ms.custom: SEO-VS-2020
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09945306a2260bed5b264d380dcea745ff3f7c07
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280429"
---
# <a name="delete-task"></a>Delete - задача

Удаляет указанные файлы.

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи `Delete` .

|Параметр|Описание|
|---------------|-----------------|
|`DeletedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает файлы, которые были успешно удалены.|
|`Files`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает файлы для удаления.|
|`TreatErrorsAsWarnings`|Необязательный параметр `Boolean`.<br /><br /> Если `true`, ошибки регистрируются как предупреждения. Значение по умолчанию — `false`.|

## <a name="remarks"></a>Примечания

Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Будьте осторожны при использовании подстановочных знаков в задаче `Delete`. Вы можете случайно удалить не те файлы, используя такие выражения, как `$(SomeProperty)\**\*.*` или `$(SomeProperty)/**/*.*`, особенно если для свойства задана пустая строка. В этом случае параметр `Files` может затронуть корень диска и удалить гораздо больше, чем требовалось.

## <a name="example"></a>Пример

В следующем примере удаляется файл *ConsoleApp1.pdb* при выполнении сборки целевого объекта `DeleteDebugSymbolFile`.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

Если необходимо отслеживать удаленные файлы, задайте для `TaskParameter` значение `DeletedFiles` с именем элемента, как показано ниже:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Вместо того чтобы напрямую использовать подстановочные знаки в задаче `Delete`, создайте `ItemGroup` файлов для удаления и выполнения задачи `Delete`. Но обязательно аккуратно разместите `ItemGroup`. Если поместить `ItemGroup` на верхнем уровне в файле проекта, он будет вычисляться на раннем этапе до начала сборки и поэтому не будет содержать файлы, созданные в ходе процесса сборки. Поэтому поместите `ItemGroup`, который создает список элементов для удаления в целевом объекте, близко к задаче `Delete`. Чтобы не создавать список элементов с путем, который начинается в корня диска, укажите условие. Это позволит убедиться, что свойство не является пустым.

Задача `Delete` предназначена для удаления файлов. Если вы хотите удалить каталог, используйте задачу [RemoveDir](removedir-task.md).

Задача `Delete` не предоставляет возможность удалять файлы, доступные только для чтения. Чтобы удалить файлы, доступные только для чтения, можно использовать задачу `Exec` для выполнения команды `del` или ее эквивалента с соответствующим параметром. Обратите внимание на длину списка входных элементов, так как в командной строке существуют ограничения. Кроме того нужно выполнять обработку имен файлов с пробелами, как показано в следующем примере:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

Как правило, при написании скриптов сборки следует определить, является ли удаление логической частью операции `Clean`. Если необходимо очистить некоторые файлы в рамках обычной операции `Clean`, их можно добавить в список `@(FileWrites)` и они будут удалены при следующем выполнении `Clean`. Если необходимо выполнить дополнительную пользовательскую обработку, определите целевой объект и запустите его, задав атрибут `BeforeTargets="Clean"` или `AfterTargets="Clean"`. Вы также можете определить пользовательскую версию целевых объектов `BeforeClean` или `AfterClean`. Дополнительные сведения см. в статье [Настройка сборки](customize-your-build.md).

## <a name="see-also"></a>См. также

- [Задача RemoveDir](removedir-task.md)
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
