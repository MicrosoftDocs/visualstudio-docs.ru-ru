---
title: Руководство. изменение размеров элементов управления в ячейках листа
description: Узнайте, как можно использовать Visual Studio для изменения размеров элементов управления в ячейках листа Microsoft Excel во время разработки и во время выполнения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7b42c10fd82ec077b295a8bc683fa138c2eb095b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825749"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Руководство. изменение размеров элементов управления в ячейках листа
  При изменении размера столбцов или строк на листе все элементы управления ведущего приложения в ячейках автоматически изменяются по высоте или ширине ячейки, размер которой был изменен. По умолчанию размеры элементов управления Windows Forms не изменяются автоматически.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 При добавлении элементов управления во время разработки необходимо задать параметры позиционирования для каждого элемента управления.

 Если добавить элемент управления Windows Forms программно и указать аргумент Range, элемент управления автоматически изменит размер при изменении размера ячейки в диапазоне. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Изменение размеров элементов управления во время разработки

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Изменение размера элементов управления с помощью ячеек во время разработки

1. Из **панели элементов** перетащите элемент управления Windows Forms на лист.

2. Щелкните элемент управления правой кнопкой мыши и выберите пункт **Формат элемента управления**.

3. В диалоговом окне **Формат элемента управления** откройте вкладку **свойства** .

4. В разделе **позиционирование объектов** установите флажок **переместить и изменить размер с ячейками** , а затем нажмите кнопку **ОК**.

     При изменении размера ячейки, содержащей элемент управления, размер элемента управления изменяется в соответствии с ячейкой.

## <a name="resize-controls-at-run-time"></a>Изменение размеров элементов управления во время выполнения
 Если добавить элемент управления Windows Forms во время выполнения и передать в <xref:Microsoft.Office.Interop.Excel.Range> качестве расположения для элемента управления, элемент управления автоматически изменит размер при изменении размера ячейки листа, содержащей диапазон.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Изменение размера элементов управления с помощью ячеек во время выполнения

1. Добавьте элемент управления в диапазон a1.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet5":::

     При изменении размера ячейки, содержащей элемент управления, размер элемента управления изменяется в соответствии с ячейкой.

## <a name="reset-control-placement"></a>Сброс размещения элемента управления
 Можно сбросить размещение и изменить размер элемента управления, задав `Placement` для свойства одно из следующих <xref:Microsoft.Office.Interop.Excel.XlPlacement> значений:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Изменение поведения элемента управления таким образом, чтобы он не изменял размер или перемещаться вместе с ячейкой

1. Вызовите свойство размещения элемента управления и задайте для него значение <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet6":::

## <a name="see-also"></a>См. также статью
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление Windows Forms элементов управления в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Как скрыть элементы управления на листах при печати](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ограничения элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
