---
title: Добавление команд и жестов в схемы зависимостей
description: Узнайте, как можно определить команды контекстного меню и обработчики жестов на схемах зависимостей в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43d6cf5410aed3d79814d5304705a424bcc71e89
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387454"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Добавление команд и жестов в схемы зависимостей

Вы можете определить команды контекстного меню и обработчики жестов на схемах зависимостей в Visual Studio. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension (VSIX) и предоставить их другим пользователям Visual Studio.

Если нужно, можно определить несколько команд и обработчиков жестов в том же проекте Visual Studio. Можно также объединить несколько проектов в одно расширение VSIX. Например, можно определить один VSIX-файл, включающий команды слоев, и доменный язык.

> [!NOTE]
> Также можно настроить проверку архитектуры, в которой исходный код пользователей сравнивается с диаграммами зависимостей. Проверку архитектуры следует определять в отдельном проекте Visual Studio. Его можно добавить в то же расширение VSIX, что и другие расширения. Дополнительные сведения см. [в разделе Добавление пользовательской проверки архитектуры в схемы зависимостей](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Требования

См. раздел [требования](../modeling/extend-layer-diagrams.md#requirements).

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>Определение команды или жеста в новом расширении VSIX

Самый быстрый способ создания расширения заключается в использовании шаблона проекта. В этом случае код и манифест VSIX размещаются в одном и том же проекте.

1. Создание нового **расширения команд конструктора слоев** или проекта **расширения жестов конструктора слоев** .

   Шаблон создает проект, который содержит небольшой рабочий пример.

2. Чтобы проверить расширение, нажмите клавиши **CTRL** + **F5** или **F5**.

    Запускается экспериментальный экземпляр Visual Studio. В этом экземпляре Создайте схему зависимостей. Расширение команды или жеста должно работать в этой схеме.

3. Закройте экспериментальный экземпляр и измените пример кода.

4. В тот же самый проект можно добавить дополнительные команды или обработчики жестов. Дополнительные сведения см. в одном из следующих разделов:

    [Определение команды меню](#command)

    [Определение обработчика жестов](#gesture)

::: moniker range="vs-2017"

5. Чтобы установить расширение в основном экземпляре Visual Studio или на другом компьютере, найдите *VSIX* файл в каталоге *bin* . Скопируйте его на компьютер, а затем дважды щелкните его. Чтобы удалить его, выберите **расширения и обновления** в меню **Сервис** .

::: moniker-end

::: moniker range=">=vs-2019"

5. Чтобы установить расширение в основном экземпляре Visual Studio или на другом компьютере, найдите *VSIX* файл в каталоге *bin* . Скопируйте его на компьютер, а затем дважды щелкните его. Чтобы удалить его, выберите **Управление расширениями** в меню **расширения** .

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>Добавление команды или жеста в отдельный VSIX-объект

Если нужно создать один файл VSIX, который содержит проверяющие элементы слоев, команды и другие расширения, рекомендуется создать один проект для определения VSIX и отдельные проекты для обработчиков.

1. Создайте проект **Библиотека классов**. Этот проект будет содержать классы команд или обработчиков жестов.

   > [!NOTE]
   > В одной библиотеке классов можно определить более одного класса команд или обработчиков жестов, однако классы проверки слоев следует определять в отдельной библиотеке классов.

2. Добавьте или создайте проект VSIX в решении. Проект VSIX содержит файл с именем **source. extension. vsixmanifest**.

3. В **Обозреватель решений** щелкните правой кнопкой мыши проект VSIX и выберите **Назначить запускаемым проектом**.

4. В **source.extension.vsixmanifest** в разделе **Активы** добавьте проект команды или обработчика жестов в качестве компонента MEF.

    1. На вкладке **Активы** выберите команду **Создать**.

    2. В поле **Тип** выберите **Microsoft.VisualStudio.MefComponent**.

    3. В поле **Источник** выберите **Проект в текущем решении** и выберите имя проекта команды или обработчика жестов.

    4. Сохраните файл.

5. Вернитесь к проекту команды или обработчика жестов и добавьте следующие ссылки на проект:

   |**Ссылка**|**Возможности**|
   |-|-|
   |Program Files\Microsoft Visual Studio [версия]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Создание и редактирование слоев|
   |Microsoft.VisualStudio.Uml.Interfaces|Создание и редактирование слоев|
   |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Изменение фигур на схемах|
   |System.ComponentModel.Composition|Определение компонентов с помощью Managed Extensibility Framework (MEF)|
   |Microsoft.VisualStudio.Modeling.Sdk.[версия]|Определение расширений моделирования|
   |Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[версия]|Обновление фигур и схем|

6. Измените файл класса в проекте библиотеки классов C# таким образом, чтобы он содержал код вашего расширения. Дополнительные сведения см. в одном из следующих разделов:

     [Определение команды меню](#command)

     [Определение обработчика жестов](#gesture)

7. Чтобы протестировать функцию, нажмите клавиши **CTRL** + **F5** или **F5**.

   Откроется экспериментальный экземпляр Visual Studio. В этом экземпляре Создайте или откройте схему зависимостей.

8. Чтобы установить VSIX в основном экземпляре Visual Studio или на другом компьютере, найдите **VSIX** файл в каталоге **bin** проекта VSIX. Скопируйте его на компьютер, где требуется выполнить установку VSIX. Дважды щелкните VSIX-файл в проводнике.

## <a name="defining-a-menu-command"></a><a name="command"></a> Определение команды меню

В существующий проект жестов или команд можно добавить дополнительные определения команд меню. Каждая команда определяется классом, имеющим указанные ниже характеристики.

- Класс объявляется следующим образом:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- Пространство имен и имя класса не имеют значения.

- Методы, реализующие `ICommandExtension` , указаны ниже.

  - `string Text {get;}` — метка, которая отображается в меню.

  - `void QueryStatus(IMenuCommand command)` — вызывается, когда пользователь щелкает схему правой кнопкой мыши и определяет, должна ли команда отображаться и быть доступна для выбранного пользователем элемента.

  - `void Execute(IMenuCommand command)` — вызывается, когда пользователь выбирает команду.

- Для определения текущего выделенного элемента можно импортировать `IDiagramContext`:

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

Чтобы добавить новую команду, создайте файл кода, содержащий приведенный ниже пример. После этого измените и протестируйте его.

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for dependency diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> Определение обработчика жестов

Обработчик жестов реагирует, когда пользователь перетаскивает элементы на схему зависимостей, и когда пользователь дважды щелкает в любом месте схемы.

В существующий проект VSIX команды или обработчика жестов можно добавить файл кода, определяющий обработчик жестов:

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

Об обработчиках свойств необходимо помнить следующее.

- Члены `IGestureExtension` показаны ниже:

     **OnDoubleClick** — вызывается при двойном щелчке в любом месте на схеме.

     **CanDragDrop** — вызывается несколько раз в том случае, когда пользователь перемещает указатель мыши на схему при перетаскивании элемента. Должен работать быстро.

     **OnDragDrop** — вызывается, когда пользователь перетаскивает элемент на схему.

- Первым аргументом каждого метода является `IShape`, из которого можно получить элемент слоя. Пример.

    ```csharp
    public void OnDragDrop(IShape target, IDataObject data)
    {
        ILayerElement element = target.GetLayerElement();
        if (element is ILayer)
        {
            // ...
        }
    }
    ```

- Обработчики для некоторых типов перетаскиваемых элементов уже определены. Например, пользователь может перетаскивать элементы из обозреватель решений на схему зависимостей. Для этих типов элементов нельзя определить обработчик перетаскивания. В этих случаях ваши методы `DragDrop` не вызываются.

## <a name="see-also"></a>См. также

- [Добавление пользовательской проверки архитектуры в схемы зависимостей](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
