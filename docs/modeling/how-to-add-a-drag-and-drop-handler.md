---
title: Практическое руководство. Добавление обработчика перетаскивания
description: Узнайте, как добавлять обработчики для событий перетаскивания в DSL, чтобы пользователи могли перетаскивать элементы на схему из других схем.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 79b58ee6ebd4db3ee9727bf59b260f281ba00275
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390415"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Практическое руководство. Добавление обработчика перетаскивания

Вы можете добавлять обработчики для событий перетаскивания в DSL, чтобы пользователи могли перетаскивать элементы на схему из других схем или из других частей Visual Studio. Кроме того, можно добавить обработчики для таких событий, как двойной щелчок кнопки мыши. Вместе обработчики перетаскивания и двойного щелчка называются *обработчиками жестов*.

В этом разделе описываются жесты перетаскивания, которые происходят из других схем. Для событий перемещения и копирования в рамках одной схемы предпочтительнее определить подкласс `ElementOperations`. Дополнительные сведения см. в разделе [Настройка поведения копирования](../modeling/customizing-copy-behavior.md). Также может быть доступна настройка определения DSL.

## <a name="defining-gesture-handlers-by-overriding-shapeelement-methods"></a>Определение обработчиков жестов путем переопределения методов ShapeElement

`OnDragDrop`, `OnDoubleClick` , `OnDragOver` и другие методы можно переопределить.

Добавьте новый файл кода в проект DSL. Для обработчика жестов обычно требуются по крайней мере следующие `using` директивы:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

В новом файле определите частичный класс для класса фигуры или схемы, который должен отвечать на операцию перетаскивания. Переопределите следующие методы.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>— Этот метод вызывается, когда указатель мыши входит в фигуру во время операции перетаскивания. Ваш метод должен проверить перетаскиваемый пользователем элемент и задать свойство Effect, определяющее возможность перетаскивания элемента на эту фигуру. Свойство Effect определяет отображение указателя мыши, когда он находится на этой фигуре, а также возможность вызова `OnDragDrop()`, когда пользователь отпускает кнопку мыши.

    ```csharp
    partial class MyShape // MyShape generated from DSL Definition.
    {
        public override void OnDragOver(DiagramDragEventArgs e)
        {
          base.OnDragOver(e);
          if (e.Effect == System.Windows.Forms.DragDropEffects.None
               && IsAcceptableDropItem(e)) // To be defined
          {
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;
          }
        }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> — Этот метод вызывается, если пользователь отпускает кнопку мыши в то время, когда указатель мыши находится на этой фигуре или схеме, если `OnDragOver(DiagramDragEventArgs e)` ранее для него было задано `e.Effect` значение, отличное от `None` .

    ```csharp
    public override void OnDragDrop(DiagramDragEventArgs e)
    {
          if (!IsAcceptableDropItem(e))
          {
            base.OnDragDrop(e);
          }
          else
          { // Process the dragged item, for example merging a copy into the diagram
            ProcessDragDropItem(e); // To be defined
          }
    }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> — Этот метод вызывается, когда пользователь дважды щелкает форму или схему.

     Дополнительные сведения см. в разделе [как перехватить щелчок фигуры или декоратора](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Определите `IsAcceptableDropItem(e)`, чтобы задать допустимость перетаскиваемого элемента, и ProcessDragDropItem(e), чтобы обновить модель после перетаскивания элемента. Прежде всего, эти методы должны извлечь элемент из аргументов события. Сведения о том, как это сделать, см. в разделе [как получить ссылку на перетаскиваемый элемент](#to-send-an-object-from-a-source-dsl).

## <a name="define-gesture-handlers-by-using-mef"></a>Определение обработчиков жестов с помощью MEF

Используйте этот метод, чтобы разрешить сторонним разработчикам определять собственные обработчики в вашем DSL. В этом случае после установки вашего DSL пользователи смогут установить сторонние расширения.

MEF (Managed Extensibility Framework) позволяет определять компоненты, которые можно установить с минимальной конфигурацией. Дополнительные сведения см. в разделе [Managed Extensibility Framework](/dotnet/framework/mef/index).

### <a name="to-define-a-mef-gesture-handler"></a>Определение обработчика жестов MEF

1. Добавьте в проекты **DSL** и **DslPackage** файлы **мефекстенсион** , описанные в разделе [Расширение DSL с помощью MEF](../modeling/extend-your-dsl-by-using-mef.md).

2. Теперь можно определить обработчик жестов в качестве компонента MEF.

    ```csharp
    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }
    ```

     При наличии различных типов перетаскиваемых объектов можно создать еще один компонент обработчика жестов.

3. Добавьте определения разделяемого класса для классов целевой фигуры, соединителя или схемы и определите методы `IsAcceptableDropItem()` и `ProcessDragDropItem()`. Эти методы должны начинаться с извлечения перетаскиваемого элемента из аргументов события. Дополнительные сведения см. в разделе [как получить ссылку на перетаскиваемый элемент](#to-send-an-object-from-a-source-dsl).

## <a name="how-to-decode-the-dragged-item"></a>Декодирование перетаскиваемого элемента

Элементы можно перетаскивать из любого окна, рабочего стола и даже доменного языка.

Когда пользователь перетаскивает элемент на вашу схему или из одной части схему в другую, сведения о перетаскиваемом элементе появляются в `DiagramDragEventArgs`. Так как операция перетаскивания может начаться на любом объекте экрана, данные могут быть доступны в любом формате. Код должен распознавать форматы, с которыми он может работать.

Для поиска форматов, в которых доступны сведения об источнике перетаскивания, запустите код в режиме отладки, задав точку останова на входе в `OnDragOver()` или `CanDragDrop()`. Проверьте значения параметра `DiagramDragEventArgs`. Сведения предоставляются в двух формах.

- <xref:System.Windows.Forms.IDataObject>  `Data` — Это свойство переносит сериализованные версии исходных объектов, обычно в нескольких форматах. Наиболее полезные функции:

  - Диаграмевентаргс. Data. Жетдатаформатс () — содержит список форматов, в которых можно декодировать перетаскиваемый объект. Например, если пользователь перетаскивает файл с рабочего стола, доступные форматы включают имя файла ("`FileNameW`").

  - `diagramEventArgs.Data.GetData(format)` — Декодирует перетаскиваемый объект в указанном формате. Приведите объект в соответствующий тип. Пример.

    `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

    Также можно передавать такие объекты, как ссылки шины модели от источника в собственный пользовательский формат. Дополнительные сведения см. [в разделе Отправка ссылок на шину модели в перетаскивании](#to-send-an-object-from-a-source-dsl).

- <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>`Prototype`— Используйте это свойство, если требуется, чтобы пользователи перетащили элементы из модели DSL или UML. Прототип группы элементов содержит один или несколько объектов, ссылок и их значений свойств. Он также используется в операции вставки и при добавлении элемента из панели элементов. В прототипе объекты и их типы обозначаются идентификаторами GUID. Например, этот код позволяет пользователю перетаскивать элементы классов из схемы UML или Обозревателя моделей UML:

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }
    ```

     Чтобы принять фигуры UML, определите идентификаторы GUID классов фигур UML, выполнив эксперимент. Помните, что на любой схеме обычно бывает больше одного типа элементов. Кроме того, объект, перетаскиваемый из доменного языка или схемы UML, является фигурой, а не элементом модели.

`DiagramDragEventArgs` также имеет свойства, указывающие текущее расположение указателя мыши и то, нажаты ли клавиши CTRL, ALT или SHIFT.

## <a name="how-to-get-the-original-of-a-dragged-element"></a>Получение оригинала перетаскиваемого элемента

Если перетаскиваемый элемент является элементом DSL, можно открыть исходную модель и получить доступ к элементу.

Свойства `Data` и `Prototype` аргументов событий содержат только ссылку на перетаскиваемую фигуру. Обычно, чтобы создать объект в целевом DSL, созданном на основе прототипа, необходимо получить доступ к оригиналу, например прочитать содержимое файла или перейти к элементу модели, представленному фигурой. Для этого можно использовать шину модели Visual Studio.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Подготовка проекта доменного языка для шины модели

Сделайте исходный DSL доступным для шины модели Visual Studio:

1. Откройте файл определения исходного доменного языка в Конструкторе DSL. Щелкните правой кнопкой мыши область конструктора и выберите команду **включить ModelBus**. В диалоговом окне выберите один или оба указанных параметра.  Нажмите кнопку **OK**. В решение DSL будет добавлен новый проект ModelBus.

2. Щелкните **преобразовать все шаблоны** и перестроить решение.

### <a name="to-send-an-object-from-a-source-dsl"></a>Отправка объекта из исходного DSL

1. В подклассе ElementOperations переопределите `Copy()` таким образом, чтобы кодировать ссылку ModelBus в IDataObject. Этот метод будет вызываться, когда пользователь начнет перетаскивание из исходной схемы. Теперь кодированная ссылка ModelBus будет появляться в IDataObject при перетаскивании объекта в целевую схему.

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}
    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Получение ссылки ModelBus из доменного языка в целевом DSL или проекте UML

1. В проекте целевого DSL добавьте ссылки на проект в:

    - исходный проект доменного языка;

    - исходный проект ModelBus.

2. В файле кода обработчика жестов добавьте следующие ссылки на пространство имен:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;
    ```

3. В следующем примере показано, как получить доступ к исходному элементу модели.

    ```csharp
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }
    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>Принятие элемента, полученного из модели UML

- В следующем примере кода принимается объект, перетащенный из схемы UML.

    ```csharp
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Classes;
    using System;
    using System.ComponentModel.Composition;
    using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }
    ```

## <a name="using-mouse-actions-dragging-compartment-items"></a>Использование действий мыши: перетаскивание элементов секции

Можно написать обработчик, который перехватывает действия мыши в полях фигуры. В следующем примере показано, как пользователь переупорядочивает элементы в секции, перетаскивая их с помощью мыши.

Чтобы создать этот пример, создайте решение с помощью шаблона решения " **диаграммы классов** ". Добавьте файл кода и включите в него следующий код. Настройте пространство имен, чтобы оно было таким же, как ваше.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape. Yuk.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>См. также

- [Настройка функции копирования](../modeling/customizing-copy-behavior.md)
- [Развертывание решений на доменных языках](msi-and-vsix-deployment-of-a-dsl.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
