---
title: Обновление фигур и соединителей в соответствии с моделью
description: Узнайте, что на предметно-ориентированном языке в Visual Studio внешний вид фигуры отражает состояние базовой модели.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6439a01de2a02361914ce227c43d903f1b24b405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388572"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Изменение фигур и соединителей в соответствии с моделью

На предметно-ориентированном языке в Visual Studio можно сделать так, чтобы внешний вид фигуры отражал состояние базовой модели.

Примеры кода в этом разделе следует добавить в `.cs` файл в `Dsl` проекте. Эти директивы понадобятся в каждом файле:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Настройка свойств карт фигур для управления видимостью декоратора

Можно управлять видимостью декоратора без написания программного кода, настроив сопоставление между фигурой и классом домена в определении DSL. Дополнительные сведения см. [в разделе Определение языка Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Предоставить цвет и стиль фигуры как свойства

В определении DSL щелкните правой кнопкой мыши класс Shape, наведите указатель на пункт **добавить предоставленный** и выберите один из таких элементов, как **Цвет заливки**.

Теперь фигура имеет свойство предметной области, которое можно задать в программном коде или в качестве пользователя. Например, чтобы задать его в программном коде команды или правила, можно написать:

`shape.FillColor = System.Drawing.Color.Red;`

Если нужно сделать переменную свойства только под управлением программы, а не пользователем, выберите новое свойство домена, такое как **Цвет заливки** на схеме определения DSL. Затем в окно свойств задайте для **параметра можно просмотреть** `false` или задать значение **Пользовательский интерфейс ReadOnly** `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Определить правила изменения, чтобы цвет, стиль или расположение зависели от свойств элемента модели
 Можно определить правила, которые обновляют внешний вид фигуры, зависят от других частей модели. Например, можно определить правило изменения для элемента модели, который обновляет цвет его фигуры в зависимости от свойств элемента модели. Дополнительные сведения о правилах изменения см. в разделе [правила распространяют изменения в модели](../modeling/rules-propagate-changes-within-the-model.md).

 Правила следует использовать только для обновления свойств, которые хранятся в хранилище, так как правила не вызываются при выполнении команды undo. Сюда не входят некоторые графические функции, такие как размер и видимость фигуры. Сведения об обновлении этих функций фигуры см. в разделе [обновление графических функций, не связанных с хранением](#OnAssociatedProperty).

 В следующем примере предполагается, что вы предоставляли `FillColor` как свойство домена, как описано в предыдущем разделе.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Использование Ончилдконфигуред для инициализации свойств фигуры

Чтобы задать свойства фигуры при ее первоначальном создании, переопределение `OnChildConfigured()` в частичном определении класса схемы. Класс схемы указан в определении DSL, а созданный код — в **Дсл\женератед коде\диаграм.КС**. Пример.

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

Этот метод можно использовать как для свойств домена, так и для функций, не связанных с хранилищем, таких как размер фигуры.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Использование АссоЦиатевалуевис () для обновления других функций фигуры

Для некоторых функций фигуры, например, имеет ли она тень или стиль стрелки соединителя, встроенный метод предоставления этой функции в качестве свойства предметной области отсутствует.  Изменения таких функций не управляются системой транзакций. Таким образом, не рекомендуется обновлять их с помощью правил, так как правила не вызываются, когда пользователь выполняет команду «Отменить».

Вместо этого эти функции можно обновить с помощью <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . В следующем примере стиль стрелки для соединителя управляется значением свойства домена в связи, отображаемой соединителем.

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` должен вызываться один раз для каждого свойства домена, которое необходимо зарегистрировать. После вызова все изменения указанного свойства будут вызываться `OnAssociatedPropertyChanged()` в любой фигуре, представляющей элемент модели свойства.

Нет необходимости вызывать `AssociateValueWith()` для каждого экземпляра. Хотя Инитиализересаурцес является методом экземпляра, он вызывается только один раз для каждого класса Shape.
