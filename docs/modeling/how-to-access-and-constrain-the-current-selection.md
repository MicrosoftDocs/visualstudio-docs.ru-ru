---
title: Практическое руководство. Предоставление и ограничение доступа к текущему выделению
description: Узнайте, как можно определить, какой элемент пользователь щелкнул правой кнопкой мыши при написании команды или обработчика жестов для конкретного доменного языка.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 28d0f99743535965b3cf203d461fac5d0193607c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386609"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Практическое руководство. Предоставление и ограничение доступа к текущему выделению

При написании команды или обработчика жестов для конкретного доменного языка можно определить, какой элемент пользователь щелкнул правой кнопкой мыши. Можно также запретить выбор некоторых фигур или полей. Например, можно задать, что при нажатии пользователем декоратора значка выбирается фигура, содержащая этот элемент. Ограничение выбора таким способом сокращает количество обработчиков, которые необходимо написать. Это также упрощает для пользователя, который может щелкнуть в любом месте фигуры, не избегая декоратора.

## <a name="access-the-current-selection-from-a-command-handler"></a>Доступ к текущему выделению из обработчика команд

Класс набора команд для доменного языка содержит обработчики команд для пользовательских команд. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>Класс, от которого наследуется класс набора команд для конкретного доменного языка, предоставляет несколько элементов для доступа к текущему выделению.

В зависимости от команды обработчик команд может потребовать выбора в конструкторе моделей, в обозревателе моделей или в активном окне.

### <a name="to-access-selection-information"></a>Доступ к сведениям о выборе

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>Класс определяет следующие члены, которые можно использовать для доступа к текущему выделению.

    |Член|Описание|
    |-|-|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Возвращает `true` , если какой-либо из элементов, выбранных в конструкторе моделей, является фигурой секции; в противном случае — значение `false` .|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Возвращает `true` , если схема выбрана в конструкторе моделей; в противном случае — значение `false` .|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Возвращает `true` , если в конструкторе моделей выбран ровно один элемент; в противном случае — значение `false` .|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Возвращает `true` , если в активном окне выбран ровно один элемент; в противном случае — значение `false` .|
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Возвращает доступную только для чтения коллекцию элементов, выбранных в конструкторе моделей.|
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Возвращает доступную только для чтения коллекцию элементов, выбранных в активном окне.|
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Возвращает первичный элемент выбранного элемента в конструкторе моделей.|
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Возвращает первичный элемент выделенного фрагмента в активном окне.|

2. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> класса предоставляет доступ к <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> объекту, который представляет окно конструктора моделей и предоставляет дополнительный доступ к выбранным элементам в конструкторе моделей.

3. Кроме того, созданный код определяет свойство окна инструментов обозревателя и свойство выбора обозревателя в классе набора команд для предметно-ориентированного языка.

    - Свойство окна инструментов обозревателя возвращает экземпляр класса окна инструментов обозревателя для предметно-ориентированного языка. Класс окна инструментов обозревателя является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> класса и представляет обозреватель моделей для предметно-ориентированного языка.

    - `ExplorerSelection`Свойство возвращает выбранный элемент в окне обозревателя моделей для предметно-ориентированного языка.

## <a name="determine-which-window-is-active"></a>Определение активного окна

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>Интерфейс содержит определение элементов, которые предоставляют доступ к текущему состоянию выбора в оболочке. Объект можно получить <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> из класса Package или класса набора команд для доменного языка с помощью `MonitorSelection` свойства, определенного в базовом классе каждого. Класс Package является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> класса, а класс набора команд является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> класса.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Определение типа активного окна с помощью обработчика команд

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> класса возвращает <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> объект, который предоставляет доступ к текущему состоянию выбора в оболочке.

2. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> интерфейса получает активный контейнер выбора, который может отличаться от активного окна.

3. Добавьте следующие свойства в класс набора команд для конкретного доменного языка, чтобы определить, какой тип окна является активным.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Ограничить выбор

Добавляя правила выбора, можно управлять выбором элементов при выборе пользователем элемента модели. Например, чтобы разрешить пользователю обрабатывать несколько элементов как единое целое, можно использовать правило выбора.

### <a name="to-create-a-selection-rule"></a>Создание правила выбора

1. Создание файла пользовательского кода в проекте DSL

2. Определите класс правил выбора, производный от <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> класса.

3. Переопределите <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> метод класса правила выбора, чтобы применить критерии выбора.

4. Добавьте определение разделяемого класса для класса ClassDiagram в файл пользовательского кода.

     `ClassDiagram`Класс является производным от <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> класса и определяется в созданном файле кода Diagram. cs в проекте DSL.

5. Переопределите <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> свойство класса, `ClassDiagram` чтобы оно возвращало настраиваемое правило выбора.

     Реализация свойства по умолчанию <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> получает объект правила выбора, который не изменяет выделенный фрагмент.

### <a name="example"></a>Пример

В следующем файле кода создается правило выбора, которое расширяет выделенный фрагмент, добавляя все экземпляры каждой из первоначально выбранных фигур домена.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>