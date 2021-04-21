---
title: Как изменить размер элементов управления ListObject
description: Узнайте, как можно использовать Visual Studio для программного изменения размера элементов управления ListObject в книге Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a2fd0b8ce46ba15066ab4cf070807e2457c21e70
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828960"
---
# <a name="how-to-resize-listobject-controls"></a>Как изменить размер элементов управления ListObject
  Размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> задается при добавлении его в книгу Microsoft Office Excel; однако позднее может потребоваться изменить его размер. Например, в список из двух столбцов может потребоваться добавить третий столбец.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В проектах уровня документа вы можете изменять размер элементов управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время разработки или во время выполнения. Вы можете изменить размер <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления во время выполнения в проекте надстройки VSTO.

 В этом разделе описываются следующие задачи.

- [Изменение размера элементов управления ListObject во время разработки](#designtime)

- [Изменение размера элементов управления ListObject во время выполнения в проекте уровня документа](#runtimedoclevel)

- [Изменение размера элементов управления ListObject во время выполнения в проекте надстройки VSTO](#runtimeaddin)

  Дополнительные сведения об элементах <xref:Microsoft.Office.Tools.Excel.ListObject> управления см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> Изменение размера элемента управления ListObject во время разработки
 Чтобы изменить размер списка, можно щелкнуть и перетащить один из маркеров размера или переопределить его размер в диалоговом окне **изменения размеров списка** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Изменение размеров списка в диалоговом окне изменения размера списка

1. Щелкните в любом месте  <xref:Microsoft.Office.Tools.Excel.ListObject> таблицы. Откроется вкладка Конструктор **инструментов таблиц**  >   на ленте.

2. В разделе Свойства щелкните **изменить размер таблицы**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Выберите новый диапазон данных для таблицы.

4. Нажмите кнопку **ОК**.

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Изменение размера элемента управления ListObject во время выполнения в проекте уровня документа
 Вы можете изменить размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время выполнения с помощью метода <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Этот метод нельзя использовать для перемещения элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> на новое место в листе. Заголовки должны оставаться в той же строке, а измененный элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> должен совмещаться с первоначальным объектом-списком. Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с измененным размером должен содержать строку заголовка и хотя бы одну строку данных.

### <a name="to-resize-a-list-object-programmatically"></a>Изменение размеров объекта-списка программными средствами

1. Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который охватывает ячейки от **A1** до **В3** в `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet6":::

2. Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Изменение размера элемента ListObject во время выполнения в проекте надстройки VSTO
 Размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно изменять во время выполнения на любом открытом листе. Дополнительные сведения о добавлении <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления на лист с помощью надстройки VSTO см. в разделе [как добавить элементы управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Изменение размеров объекта-списка программными средствами

1. Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который охватывает ячейки от **A1** до **В3** в `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet12":::

2. Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>См. также статью
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
- [Как добавить элементы управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Как изменить размер элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Как изменить размер элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)
