---
title: Расширение доменного языка с помощью MEF
description: Узнайте, как расширить доменный язык (DSL) с помощью Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a4572a7210203d6c7525a278430210c954c3405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388884"
---
# <a name="extend-your-dsl-by-using-mef"></a>Расширение доменного языка с помощью MEF

Вы можете расширить доменный язык DSL с помощью Managed Extensibility Framework (MEF). Вы или другие разработчики смогут создавать расширения для DSL без изменения определения DSL и программного кода. Такие расширения включают команды меню, обработчики перетаскивания и проверку. Пользователи смогут установить DSL, а затем при необходимости установить расширения для него.

Кроме того, при включении MEF в DSL может быть проще написать некоторые функции DSL, даже если они все вместе основаны на DSL.

Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Включение расширения DSL с помощью MEF

1. Создайте новую папку с именем **мефекстенсион** в проекте **DslPackage** . Добавьте в него следующие файлы:

     Имя файла: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Задать GUID в этом файле так же, как GUID Коммандсетид, определенный в Дслпаккаже\женератедкоде\константс.ТТ

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    Имя файла: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    Имя файла: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    Имя файла: `ValidationExtensionRegistrar.tt`

    При добавлении этого файла необходимо включить проверку в DSL, используя хотя бы один из параметров в **едиторвалидатион** в обозревателе DSL.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Имя файла: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. Создайте новую папку с именем **мефекстенсион** в проекте **DSL** . Добавьте в него следующие файлы:

     Имя файла: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    Имя файла: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    Имя файла: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. Добавьте следующую строку в существующий файл с именем **дслпаккаже\коммандс.вскт**:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Вставьте строку после существующей `<Include>` директивы.

4. Откройте *DslDefinition. DSL*.

5. В обозревателе DSL выберите **едитор\валидатион**.

6. В окно свойств убедитесь, что по крайней мере одно из свойств с именем **использует** `true` .

7. На панели инструментов **Обозреватель решений** нажмите кнопку **преобразовать все шаблоны**.

     Дочерние файлы появятся под каждым из добавленных файлов.

8. Выполните сборку и запустите решение, чтобы убедиться, что оно по-прежнему работает.

Теперь ваш DSL включен. В качестве расширений MEF можно создавать команды меню, обработчики жестов и ограничения проверки. Эти расширения можно писать в решении DSL вместе с другим пользовательским кодом. Кроме того, вы или другие разработчики могут создавать отдельные расширения Visual Studio, расширяющие возможности DSL.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Создание расширения для DSL с поддержкой MEF

Если у вас есть доступ к DSL с поддержкой MEF, созданному вами или другим пользователем, вы можете написать для него расширения. Расширения можно использовать для добавления команд меню, обработчиков жестов или ограничений проверки. Для создания этих расширений используется решение расширения Visual Studio (VSIX). Решение состоит из двух частей: проекта библиотеки классов, который строит сборку кода, и проекта VSIX, который упаковывает сборку.

### <a name="to-create-a-dsl-extension-vsix"></a>Создание VSIX расширения DSL

1. Создайте проект **Библиотека классов**.

2. В новом проекте добавьте ссылку на сборку DSL.

   - Эта сборка, как правило, имеет имя, заканчивающееся на ".Dsl.dll".

   - Если у вас есть доступ к проекту DSL, файл сборки можно найти в каталоге **DSL \\ bin \\ \*** .

   - Если у вас есть доступ к файлу VSIX DSL, сборку можно найти, изменив расширение имени файла VSIX на «.zip». Распакуйте файл .zip.

3. Добавьте ссылки на следующие сборки .NET:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Создание нового проекта **VSIX** .

5. В **Обозреватель решений** щелкните правой кнопкой мыши проект VSIX и выберите **Назначить запускаемым проектом**.

6. В новом проекте откройте **source. extension. vsixmanifest**.

7. Нажмите кнопку **Добавить содержимое**. В диалоговом окне задайте для параметра **тип содержимого** значение **компонент MEF** и **исходный проект** в проект библиотеки классов.

8. Добавьте ссылку VSIX в DSL.

   1. В **source. extension. vsixmanifest** нажмите кнопку **Добавить ссылку** .

   2. В диалоговом окне щелкните **добавить полезные данные** , а затем найдите VSIX файл DSL. VSIX-файл строится в решении DSL в **DslPackage \\ bin \\ \***.

       Это позволяет пользователям одновременно установить DSL и расширение. Если пользователь уже установил DSL, будет установлено только расширение.

9. Проверьте и обновите другие поля **source. extension. vsixmanifest**. Щелкните **Выбрать выпуски** и убедитесь, что установлены правильные выпуски Visual Studio.

10. Добавьте код в проект библиотеки классов. Используйте примеры, приведенные в следующем разделе, в качестве примера.

     Можно добавить любое количество классов команд, жестов и проверки.

11. Чтобы проверить расширение, нажмите клавишу **F5**. В экспериментальном экземпляре Visual Studio создайте или откройте файл с примером DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Написание расширений MEF для DSL

Вы можете писать расширения в проекте кода сборки для отдельного решения расширения DSL. Вы также можете использовать MEF в проекте DslPackage, чтобы легко писать команды, жесты и код проверки как часть DSL.

### <a name="menu-commands"></a>Команды меню

Чтобы создать команду меню, определите класс, реализующий интерфейс, <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> и добавьте к нему префикс с атрибутом, определенным в DSL, с именем *йоурдсл* `CommandExtension` . Можно создать более одного класса команд меню.

`QueryStatus()` вызывается всякий раз, когда пользователь щелкает схему правой кнопкой мыши. Он должен проверить текущее выделение и задать параметр, `command.Enabled` чтобы указать, когда команда применима.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>Обработчики жестов

Обработчик жестов может обрабатывать объекты, перетаскиваемые на схему из любого места, внутри или за пределами Visual Studio. Следующий пример позволяет пользователю перетаскивать файлы из проводника Windows на схему. Он создает элементы, которые содержат имена файлов.

Можно написать обработчики для обработки перетаскивания из других моделей DSL и моделей UML. Дополнительные сведения см. [в разделе инструкции. Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md).

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>Ограничения проверки

Методы проверки помечаются `ValidationExtension` атрибутом, созданным DSL, а также с помощью <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . Метод может присутствовать в любом классе, который не помечен атрибутом.

Дополнительные сведения см. [в разделе Проверка на Domain-Specific языке](../modeling/validation-in-a-domain-specific-language.md).

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>См. также

- [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Практическое руководство. Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Проверка в доменных языках](../modeling/validation-in-a-domain-specific-language.md)
