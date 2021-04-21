---
title: Как сопоставлять столбцы ListObject с данными
description: Узнайте, как можно сопоставлять столбцы, которые должны отображаться в ListObject при вызове метода Сетдатабиндинг.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68cb12503d0f8ad59de92f965c0ed51fbc0d7f40
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827465"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Как сопоставлять столбцы ListObject с данными
  При привязке элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> к <xref:System.Data.DataTable>вы можете не захотеть отображать все столбцы в списке или можете иметь некоторые столбцы, не привязанные к данным. Можно указать, какие столбцы должны отображаться в объекте <xref:Microsoft.Office.Tools.Excel.ListObject> , при вызове метода <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Сопоставление столбцов

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Сопоставление таблицы данных со столбцами в списке

1. Создайте <xref:System.Data.DataTable> на уровне класса.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet16":::

2. Добавьте образцы столбцов и данных в `Startup` обработчик событий `Sheet1` класса (в проекте уровня документа) или `ThisAddIn` класса (в проекте надстройки VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet17":::

3. Вызовите метод <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> и передайте в него имена столбцов в порядке их отображения. Объект списка будет привязан к только что созданному <xref:System.Data.DataTable> , но порядок столбцов в объекте списка будет отличаться от порядка, в котором они отображаются в <xref:System.Data.DataTable> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet18":::

## <a name="specify-unmapped-columns"></a>Указание несопоставленных столбцов
 При сопоставлении столбцов с <xref:System.Data.DataTable>можно также указать, что определенные столбцы не должны быть привязаны к данным, передав пустую строку. Затем новый столбец, не привязанный к данным, добавляется в элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> .

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Указание несопоставленного столбца при сопоставлении столбцов ListObject

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> и передайте в него имена столбцов в порядке их отображения. Используйте пустую строку, чтобы указать, где добавляется несопоставленный столбец; в данном случае такой столбец добавляется между столбцом заголовка столбца и столбцом фамилии.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet19":::

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере кода предполагается, что в листе, в котором этот код появляется, имеется существующий элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `list1` .

## <a name="see-also"></a>См. также статью
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Как заполнить элементы управления ListObject данными](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
