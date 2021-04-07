---
title: Написание задач | Документы Майкрософт
description: Узнайте, как создавать собственные задачи для предоставления кода, выполняемого во время сборки MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0db9504404142e5bfdd17a66471820ddad790130
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214555"
---
# <a name="task-writing"></a>Написание задач

Задачи содержат код, который выполняется в процессе сборки. Задачи содержатся в целевых объектах. В MSBuild включена библиотека типичных задач, но вы также можете создавать собственные задачи. Дополнительные сведения о библиотеке задач, включенных в MSBuild, см. в статье [Справочник по задачам MSBuild](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Задания

 Примеры задач: [Copy](../msbuild/copy-task.md) — копирование одного или нескольких файлов; [MakeDir](../msbuild/makedir-task.md) — создание каталога; [Csc](../msbuild/csc-task.md) — компиляция файлов исходного кода C#. Каждая задача реализуется в виде класса платформы .NET, реализующего интерфейс <xref:Microsoft.Build.Framework.ITask>, который определяется в сборке *Microsoft.Build.Framework.dll*.

 Существуют два подхода к реализации задачи:

- Прямая реализация интерфейса <xref:Microsoft.Build.Framework.ITask>.

- Произведите класс от вспомогательного класса <xref:Microsoft.Build.Utilities.Task>, который определен в сборке *Microsoft.Build.Utilities.dll*. Задача реализует интерфейс ITask и обеспечивает реализации по умолчанию некоторых элементов ITask. Кроме того, упрощается ведение журнала.

В обоих случаях необходимо добавить в свой класс метод `Execute`, то есть метод, который вызывается при выполнении задачи. Этот метод не принимает параметров и возвращает значение типа `Boolean`: `true`, если задача успешно выполнена, или `false`, если задачу выполнить не удалось. В приведенном ниже примере показана задача, не выполняющая никакого действия и возвращающая значение `true`.

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }
    }
}
```

 Эта задача запускается из следующего файла проекта:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Если свойства .NET создаются в классе задач, то выполняющиеся задачи могут получать входные данные из файла проекта. MSBuild задает эти свойства непосредственно перед вызовом метода `Execute` задачи. Чтобы создать свойство строки, используйте код задачи следующего вида:

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }

        public string MyProperty { get; set; }
    }
}
```

 Следующий файл проекта запускает эту задачу и присваивает свойству `MyProperty` указанное значение:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Регистрация задач

 Если проекту предстоит запускать задачу, MSBuild необходимо знать, как найти сборку, содержащую класс задачи. Задачи регистрируются с помощью [элемента UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Файл MSBuild в *Microsoft.Common.Tasks* — это файл проекта, который содержит список элементов `UsingTask`, регистрирующих все задачи предоставленные в MSBuild. Этот файл включается автоматически при сборке каждого проекта. Если задача, зарегистрированная в *Microsoft.Common.Tasks*, зарегистрирована также в текущем файле проекта, текущий файл проекта имеет приоритет. Таким образом можно переопределить задачу по умолчанию собственной задачей с тем же именем.

> [!TIP]
> Чтобы увидеть список задач, включенных в MSBuild, просмотрите содержимое файла *Microsoft.Common.Tasks*.

## <a name="raise-events-from-a-task"></a>Создание событий из задачи

 Если задача является производной от вспомогательного класса <xref:Microsoft.Build.Utilities.Task>, вы можете использовать любой из следующих вспомогательных методов класса <xref:Microsoft.Build.Utilities.Task> для создания событий, которые будут перехватываться и отображаться зарегистрированными средствами ведения журнала:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Если задача реализует интерфейс <xref:Microsoft.Build.Framework.ITask> напрямую, вы также можете создавать эти события, но необходимо использовать интерфейс IBuildEngine. В следующем примере показана задача, реализующая интерфейс ITask и создающая пользовательское событие:

```csharp
public class SimpleTask : ITask
{
    public IBuildEngine BuildEngine { get; set; }

    public override bool Execute()
    {
        TaskEventArgs taskEvent =
            new TaskEventArgs(BuildEventCategory.Custom,
            BuildEventImportance.High, "Important Message",
           "SimpleTask");
        BuildEngine.LogBuildEvent(taskEvent);
        return true;
    }
}
```

## <a name="require-task-parameters-to-be-set"></a>Обязательные параметры задачи

 Некоторые свойства задачи можно пометить как "обязательные", чтобы в любом файле проекта, из которого запускается задача, значения этих свойств должны были быть заданы, чтобы сборка не завершилась сбоем. Примените к свойству .NET в задаче атрибут `[Required]` следующим образом:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 Атрибут `[Required]` определяется классом <xref:Microsoft.Build.Framework.RequiredAttribute> в пространстве имен <xref:Microsoft.Build.Framework>.

## <a name="how-msbuild-invokes-a-task"></a>Как MSBuild вызывает задачу

При вызове задачи MSBuild сначала создает экземпляр класса задачи, а затем вызывает методы задания свойств этого объекта для параметров задачи, указанных в элементе задачи в файле проекта. Если в элементе задачи не указан параметр или если результатом вычисления выражения, указанного в элементе, является пустая строка, метод задания свойства не вызывается.

Например, в проекте

```xml
<Project>
 <Target Name="InvokeCustomTask">
  <CustomTask Input1=""
              Input2="$(PropertyThatIsNotDefined)"
              Input3="value3" />
 </Target>
</Project>
```

вызывается только метод задания для `Input3`.

Задача не должна зависеть от относительного порядка, в котором вызываются методы задания свойств.

### <a name="task-parameter-types"></a>Типы параметров задачи

MSBuild изначально обрабатывает свойства типов `string`, `bool`, `ITaskItem` и `ITaskItem[]`. Если задача принимает параметр другого типа, MSBuild вызывает <xref:System.Convert.ChangeType%2A> для преобразования `string` (со всеми развернутыми свойствами и ссылками на элементы) в целевой тип. Если преобразование для любого входного параметра завершается неудачно, MSBuild выдает ошибку и не вызывает метод `Execute()` задачи.

## <a name="example-1"></a>Пример 1

### <a name="description"></a>Описание

В этом классе C# показана задача, производная от вспомогательного класса <xref:Microsoft.Build.Utilities.Task>. Эта задача возвращает значение `true`, указывающее на успешное выполнение.

### <a name="code"></a>Код

```csharp
using System;
using Microsoft.Build.Utilities;

namespace SimpleTask1
{
    public class SimpleTask1: Task
    {
        public override bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-2"></a>Пример 2

### <a name="description"></a>Описание

В этом классе C# показана задача, реализующая интерфейс <xref:Microsoft.Build.Framework.ITask>. Эта задача возвращает значение `true`, указывающее на успешное выполнение.

### <a name="code"></a>Код

```csharp
using System;
using Microsoft.Build.Framework;

namespace SimpleTask2
{
    public class SimpleTask2: ITask
    {
        //When implementing the ITask interface, it is necessary to
        //implement a BuildEngine property of type
        //Microsoft.Build.Framework.IBuildEngine. This is done for
        //you if you derive from the Task class.
        public IBuildEngine BuildEngine { get; set; }

        // When implementing the ITask interface, it is necessary to
        // implement a HostObject property of type object.
        // This is done for you if you derive from the Task class.
        public object HostObject { get; set; }

        public bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-3"></a>Пример 3

### <a name="description"></a>Описание

В этом классе C# показана задача, производная от вспомогательного класса <xref:Microsoft.Build.Utilities.Task>. В ней задается обязательное строковое свойство и создается событие, отображаемое всеми зарегистрированными средствами ведения журнала.

### <a name="code"></a>Код

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs" id="Snippet1":::

## <a name="example-4"></a>Пример 4

### <a name="description"></a>Описание

В этом примере показан файл проекта, в котором вызывается задача из предыдущего примера (SimpleTask3).

### <a name="code"></a>Код

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <UsingTask TaskName="SimpleTask3.SimpleTask3"
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>

    <Target Name="MyTarget">
        <SimpleTask3 MyProperty="Hello!"/>
    </Target>
</Project>
```

## <a name="see-also"></a>См. также раздел

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
