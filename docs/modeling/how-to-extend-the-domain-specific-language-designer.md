---
title: Практическое руководство. Расширение конструктора доменного языка
description: Узнайте, как сделать расширения для конструктора, используемые для изменения определений доменного языка (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9354e3b846f48a79aa5cdd0f39a159bd007cdd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387221"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Практическое руководство. Расширение конструктора доменного языка

Вы можете сделать расширения конструктором, который используется для редактирования определений DSL. Типы расширений, которые можно сделать, включают добавление команд меню, добавление обработчиков для жестов перетаскивания и двойных щелчков, а также правила, активируемые при изменении определенных типов значений или связей. Расширения можно упаковать как расширение интеграции Visual Studio (VSIX) и распространить среди других пользователей.

Пример кода и дополнительные сведения об этой функции см. в [пакете SDK визуализации и моделирования](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)Visual Studio.

## <a name="set-up-the-solution"></a>Настройка решения

Настройте проект, содержащий код вашего расширения, и проект VSIX, который экспортирует проект. Решение может содержать другие проекты, включенные в один и тот же VSIX.

### <a name="to-create-a-dsl-designer-extension-solution"></a>Создание решения расширения Конструктор DSL

1. Создайте новый проект, используя шаблон проекта **библиотеки классов** . Этот проект будет содержать код ваших расширений.

2. Создание нового проекта **VSIX** .

     Выберите **Добавить в решение**.

     *Source. extension. vsixmanifest* откроется в редакторе манифеста VSIX.

3. Над полем содержимое щелкните **Добавить содержимое**.

4. В диалоговом окне **Добавление содержимого** установите **флажок выбрать тип содержимого** в **компоненте MEF** и задайте для параметра **проект** проект библиотеки классов.

5. Щелкните **Выбрать выпуски** и убедитесь, что **Visual Studio Enterprise** установлен.

6. Убедитесь, что проект VSIX является запускаемым проектом решения.

7. В проекте библиотеки классов добавьте ссылки на следующие сборки:

     Microsoft. VisualStudio. Кореутилити

     Microsoft. VisualStudio. моделирование. SDK. 11.0

     Microsoft. VisualStudio. моделирование. SDK. схемы. 11.0

     Microsoft. VisualStudio. моделирование. SDK. DslDefinition. 11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0;

     System.ComponentModel.Composition

     System.Drawing;

     System.Drawing.Design

     System.Windows.Forms.

## <a name="test-and-deployment"></a>Тестирование и развертывание

Чтобы протестировать любое из расширений в этом разделе, выполните сборку и запустите решение. Откроется экспериментальный экземпляр Visual Studio. В этом экземпляре откройте решение DSL. Измените схему DslDefinition. Поведение расширения можно увидеть.

Чтобы развернуть расширения в основном Visual Studio и на других компьютерах, выполните следующие действия.

1. Найдите файл установки VSIX в проекте VSIX в bin \\ * \\ \* . VSIX

2. Скопируйте этот файл на конечный компьютер, а затем в проводнике Windows (или в проводнике) дважды щелкните его.

     Откроется диспетчер расширений Visual Studio, чтобы убедиться, что расширение установлено.

Чтобы удалить расширение, выполните следующие действия.

1. в Visual Studio в меню **Сервис** выберите пункт **Диспетчер расширений**.

2. Выберите расширение и удалите его.

## <a name="add-a-shortcut-menu-command"></a>Добавление команды контекстного меню

Чтобы отобразить команду контекстного меню на Конструктор DSL поверхности или в окне обозревателя DSL, напишите класс, подобный приведенному ниже.

Класс должен реализовывать `ICommandExtension` и должен иметь атрибут `DslDefinitionModelCommandExtension` .

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handle-mouse-gestures"></a>Работа с жестами мыши

Код аналогичен коду команды меню.

```csharp
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="respond-to-value-changes"></a>Реагирование на изменения значений

Для правильной работы этого обработчика необходима модель предметной области. Мы предоставляем простую модель предметной области.

```csharp
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

В следующем коде реализуется простая модель. Создайте новый GUID, чтобы заменить заполнитель.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```