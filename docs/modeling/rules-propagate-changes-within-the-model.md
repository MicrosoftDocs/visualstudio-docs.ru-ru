---
title: Правила распространяют изменения в пределах модели
description: Узнайте, как создать правило хранения для распространения изменений из одного элемента в другой в пакете SDK для визуализации и моделирования (VMSDK).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bde67bd8375e3752370b3b815f8ed155d3123741
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387597"
---
# <a name="rules-propagate-changes-within-the-model"></a>Правила распространяют изменения в пределах модели
Вы можете создать правило хранения, чтобы распространить изменения с одного элемента на другой в пакете SDK визуализации и моделирования (VMSDK). Когда происходит изменение в любом элементе хранилища, запланировано выполнение правил, обычно при фиксации самой внешней транзакции. Существуют различные типы правил для различных типов событий, например добавление элемента или его удаление. Правила можно присоединять к конкретным типам элементов, фигур или диаграмм. Многие встроенные функции определяются правилами. Например, правила обеспечивают обновление схемы при изменении модели. Вы можете настроить доменный язык, добавив собственные правила.

 Правила хранения особенно полезны для распространения изменений в магазине, то есть изменений элементов модели, связей, фигур или соединителей, а также свойств домена. Правила не выполняются, когда пользователь вызывает команды отмены или повтора. Вместо этого диспетчер транзакций гарантирует, что содержимое хранилища будет восстановлено в нужном состоянии. Если вы хотите распространить изменения на ресурсы за пределами хранилища, используйте события хранилища. Дополнительные сведения см. в разделе " [обработчики событий" распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Например, предположим, что необходимо указать, что каждый раз, когда пользователь (или ваш код) создает новый элемент типа Ексампледомаинкласс, в другой части модели создается дополнительный элемент другого типа. Можно написать Аддруле и связать его с Ексампледомаинкласс. Необходимо написать код в правиле, чтобы создать дополнительный элемент.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;

namespace ExampleNamespace
{
 // Attribute associates the rule with a domain class:
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class MyAddRule : AddRule
 {
  // Override the abstract method:
  public override void ElementAdded(ElementAddedEventArgs e)
  {
    base.ElementAdded(e);
    ExampleDomainClass element = e.ModelElement;
    Store store = element.Store;
    // Ignore this call if we're currently loading a model:
    if (store.TransactionManager.CurrentTransaction.IsSerializing)
       return;

    // Code here propagates change as required - for example:
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);
      echo.Name = element.Name;
      echo.Parent = element.Parent;
    }
  }
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
   protected override Type[] GetCustomDomainModelTypes()
   {
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
     types.Add(typeof(MyAddRule));
     // If you add more rules, list them here.
     return types.ToArray();
   }
 }
}
```

> [!NOTE]
> Код правила должен изменять состояние только элементов внутри хранилища. Это значит, что правило должно изменять только элементы модели, связи, фигуры, соединители, схемы или их свойства. Если требуется распространить изменения на ресурсы за пределами хранилища, определите события магазина. Дополнительные сведения см. в разделе " [обработчики событий" распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Определение правила

1. Определите правило как класс с префиксом `RuleOn` . Атрибут связывает правило с одним из классов предметной области, связей или элементов схемы. Правило будет применено к каждому экземпляру этого класса, который может быть абстрактным.

2. Зарегистрируйте правило, добавив его в набор, возвращенный `GetCustomDomainModelTypes()` в классе модели предметной области.

3. Создайте класс правил на основе одного из абстрактных классов правил и напишите код метода выполнения.

   В следующих разделах данные шаги описаны более подробно.

### <a name="to-define-a-rule-on-a-domain-class"></a>Определение правила для доменного класса

- В файле пользовательского кода определите класс и добавьте к нему префикс с помощью <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> атрибута:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Тип субъекта в первом параметре может быть классом домена, отношением домена, фигурой, соединителем или схемой. Обычно правила применяются к доменным классам и связям.

     `FireTime`Обычно это `TopLevelCommit` . Это гарантирует, что правило будет выполняться только после внесения всех основных изменений транзакции. Альтернативные варианты являются встроенными, что выполняет правило вскоре после изменения; и Локалкоммит, которая выполняет правило в конце текущей транзакции (которая может быть не внешней). Можно также задать приоритет правила, чтобы повлиять на его порядок в очереди, но это ненадежный метод достижения требуемого результата.

- В качестве типа субъекта можно указать абстрактный класс.

- Правило применяется ко всем экземплярам класса subject.

- Значение по умолчанию для параметра `FireTime` — тиметофире. топлевелкоммит. Это приводит к тому, что правило будет выполняться при фиксации самой внешней транзакции. Альтернативой является Тиметофире. Inline. Это приводит к тому, что правило будет выполняться вскоре после события, запускающего событие.

### <a name="to-register-the-rule"></a>Регистрация правила

- Добавьте класс правил в список типов, возвращаемых `GetCustomDomainModelTypes` в модели предметной области:

    ```csharp
    public partial class ExampleDomainModel
     {
       protected override Type[] GetCustomDomainModelTypes()
       {
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
         types.Add(typeof(MyAddRule));
         // If you add more rules, list them here.
         return types.ToArray();
       }
     }

    ```

- Если вы не знаете имя класса модели предметной области, найдите в файле **дсл\женератедкоде\домаинмодел.КС**

- Напишите этот код в файл пользовательского кода в проекте DSL.

### <a name="to-write-the-code-of-the-rule"></a>Написание кода правила

- Создайте класс правил на основе одного из следующих базовых классов:

  | Базовый класс | Триггер |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Добавляется элемент, ссылка или фигура.<br /><br /> Используйте его для обнаружения новых связей в дополнение к новым элементам. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Изменено значение свойства домена. Аргумент метода предоставляет старое и новое значения.<br /><br /> Для фигур это правило активируется при изменении встроенного `AbsoluteBounds` свойства, если фигура перемещена.<br /><br /> Во многих случаях удобнее переопределять `OnValueChanged` или использовать `OnValueChanging` обработчик свойств. Эти методы вызываются непосредственно перед изменением и после него. В отличие от этого правило обычно выполняется в конце транзакции. Дополнительные сведения см. в разделе [обработчики изменений значений свойств домена](../modeling/domain-property-value-change-handlers.md). **Примечание.**  Это правило не срабатывает при создании или удалении ссылки. Вместо этого запишите `AddRule` и `DeleteRule` для доменной связи. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Активируется при удалении элемента или ссылки. Свойство ModelElement. удаления имеет значение true до окончания транзакции. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Выполняется при удалении элемента или ссылки. Правило выполняется после выполнения всех других правил, включая Делетингрулес. ModelElement. IsDeleted имеет значение false, а ModelElement. IsTrue имеет значение true. Чтобы обеспечить дальнейшую отмену, элемент фактически не удаляется из памяти, но удаляется из Store. Елементдиректори. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Элемент перемещается из одного раздела хранилища в другой.<br /><br /> (Обратите внимание, что это не связано с графической позицией фигуры.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Это правило применяется только к доменным связям. Он активируется, если элемент модели явным образом назначается либо к концу ссылки. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Активируется при изменении порядка ссылок на или из элемента с помощью методов Мовебефоре или Моветоиндекс в ссылке. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Выполняется при создании транзакции. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Выполняется при фиксации транзакции. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Выполняется, когда транзакция собирается откатить. |

- Каждый класс имеет переопределяемый метод. Введите `override` свой класс, чтобы обнаружить его. Параметр этого метода определяет изменяемый элемент.

  Обратите внимание на следующие моменты правил:

1. Набор изменений в транзакции может вызвать несколько правил. Обычно правила выполняются при фиксации самой внешней транзакции. Они выполняются в неопределенном порядке.

2. Правило всегда выполняется внутри транзакции. Поэтому нет необходимости создавать новую транзакцию для внесения изменений.

3. Правила не выполняются при откате транзакции или при выполнении операций отмены или повтора. Эти операции сбрасывают все содержимое хранилища до предыдущего состояния. Таким образом, если правило изменяет состояние какого-либо за пределами магазина, оно может не храниться в синчронисм с содержимым магазина. Чтобы обновить состояние за пределами хранилища, лучше использовать события. Дополнительные сведения см. в разделе " [обработчики событий" распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Некоторые правила выполняются при загрузке модели из файла. Чтобы определить, выполняется ли загрузка или сохранение, используйте `store.TransactionManager.CurrentTransaction.IsSerializing` .

5. Если код правила создает дополнительные триггеры правил, они будут добавлены в конец списка срабатываний и будут выполнены до завершения транзакции. Делетедрулес выполняются после всех остальных правил. Одно правило может выполняться несколько раз в транзакции по одному времени для каждого изменения.

6. Чтобы передать сведения в правила и из правил, можно сохранить сведения в `TransactionContext` . Это просто словарь, который поддерживается во время транзакции. Он удаляется после завершения транзакции. Аргументы события в каждом правиле предоставляют доступ к нему. Помните, что правила не выполняются в прогнозируемом порядке.

7. Используйте правила после рассмотрения других альтернатив. Например, если необходимо обновить свойство при изменении значения, рассмотрите возможность использования вычисляемого свойства. Если необходимо ограничить размер или расположение фигуры, используйте `BoundsRule` . Если вы хотите ответить на изменение значения свойства, добавьте `OnValueChanged` обработчик в свойство. Дополнительные сведения см. [в разделе реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Пример
 В следующем примере свойство обновляется при создании связи между доменами для связывания двух элементов. Правило будет запускаться не только при создании пользователем ссылки на диаграмме, но и при создании ссылки в коде программы.

 Чтобы протестировать этот пример, создайте DSL с помощью шаблона решения для потока задач и вставьте следующий код в файл в проекте DSL. Выполните сборку и запустите решение и откройте пример файла в проекте отладки. Нарисуйте ссылку на комментарий между фигурой комментария и элементом Flow. Текст в комментарии изменится на отчет по последнему элементу, к которому вы подключились.

 На практике обычно создается DeleteRule для каждого Аддруле.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.TaskRuleExample
{

  [RuleOn(typeof(CommentReferencesSubjects))]
  public class RoleRule : AddRule
  {

    public override void ElementAdded(ElementAddedEventArgs e)
    {
      base.ElementAdded(e);
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;
      Comment comment = link.Comment;
      FlowElement subject = link.Subject;
      Transaction current = link.Store.TransactionManager.CurrentTransaction;
      // Don't want to run when we're just loading from file:
      if (current.IsSerializing) return;
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";
    }

  }

  public partial class TaskRuleExampleDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(RoleRule));
      return types.ToArray();
    }
  }

}
```

## <a name="see-also"></a>См. также

- [Обработчики событий распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md)