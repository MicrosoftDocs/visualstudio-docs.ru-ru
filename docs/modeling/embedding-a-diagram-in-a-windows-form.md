---
title: Встраивание схемы в форму Windows
description: Сведения о внедрении схемы DSL в элемент управления Windows, который отображается в окне Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4db60267b835882a69a08c990af644b902697bad
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388988"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Внедрение схемы в Windows-форму

Схему DSL можно внедрить в элемент управления Windows, который отображается в окне Visual Studio.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Внедрение схемы DSL в элемент управления Windows

1. Добавьте новый файл **пользовательского элемента управления** в проект DslPackage.

2. Добавьте элемент управления Panel в пользовательский элемент управления. Эта панель будет содержать схему DSL.

     Добавьте другие необходимые элементы управления.

     Задайте свойства привязки элементов управления.

3. В обозреватель решений щелкните правой кнопкой мыши файл пользовательского элемента управления и выберите пункт **Просмотреть код**. Добавьте этот конструктор и переменную в код:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Добавьте новый файл в проект DslPackage со следующим содержимым:

    ```csharp
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }
    ```

5. Чтобы проверить DSL, нажмите клавишу **F5** и откройте файл образца модели. Схема отображается внутри элемента управления. Область элементов и другие функции работают нормально.

## <a name="update-the-form-using-store-events"></a>Обновление формы с помощью событий хранилища

1. В конструкторе форм добавьте **ListBox** с именем `listBox1` . Отобразится список элементов модели. Он синхронизируется с моделью с помощью *событий хранилища*. Дополнительные сведения см. в разделе " [обработчики событий" распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. В файле пользовательского кода Переопределите дополнительные методы для класса DocView:

    ```csharp
    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }
    ```

3. В коде, который находится за пользовательским элементом управления, вставьте методы для прослушивания добавленных и удаленных элементов:

    ```csharp
    public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }
    ```

4. Чтобы проверить DSL, нажмите клавишу **F5** и в экспериментальном экземпляре Visual Studio откройте файл образца модели.

     Обратите внимание, что в списке отображается список элементов в модели и они верны после добавления или удаления, а также после операций отмены и повтора.

## <a name="see-also"></a>См. также

- [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)
