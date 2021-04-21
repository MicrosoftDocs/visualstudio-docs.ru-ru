---
title: Руководство. Программная сортировка данных на листах
description: Узнайте, как можно использовать Visual Studio для программной сортировки данных, содержащихся в диапазонах и списках на листе во время выполнения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 024bf53b7fc7f3a6e32e10b7107c9a62d8c40cee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825021"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Руководство. Программная сортировка данных на листах
  Вы можете сортировать данные, содержащиеся в списках и диапазонах листа во время выполнения. Следующий код сортирует диапазон из нескольких столбцов с именем `Fruits` по данным в первом столбце, а затем по данным во втором столбце.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Сортировка данных в настройке на уровне документа

### <a name="to-sort-data-in-a-namedrange-control"></a>Сортировка данных в элементе управления NamedRange

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>. В следующем примере на листе должен находиться элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `Fruits`. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet78":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet78":::

   Поместите следующий код в *Лист1. vb* или *Sheet1. CS* для сортировки данных в <xref:Microsoft.Office.Tools.Excel.ListObject> элементе управления. В коде предполагается, что на листе с именем `Sheet1` есть элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `fruitList`.

### <a name="to-sort-data-in-a-listobject-control"></a>Сортировка данных в элементе управления ListObject

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> свойства <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet79":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet79":::

## <a name="sort-data-in-a-vsto-add-in"></a>Сортировка данных в надстройке VSTO

### <a name="to-sort-data-in-a-native-range"></a>Сортировка данных в собственном диапазоне

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> неуправляемого элемента управления <xref:Microsoft.Office.Interop.Excel.Range> Excel. В следующем примере на листе должен находиться неуправляемый элемент управления Excel с именем `Fruits`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet23":::

### <a name="to-sort-data-in-a-listobject-control"></a>Сортировка данных в элементе управления ListObject

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> свойства <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> неуправляемого элемента управления <xref:Microsoft.Office.Interop.Excel.ListObject> Excel. В следующем примере предполагается, что на активном листе есть неуправляемый элемент управления <xref:Microsoft.Office.Interop.Excel.ListObject> Excel с именем `fruitList`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet24":::

## <a name="see-also"></a>См. также статью
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Руководство. программное автоматическое заполнение диапазонов путем постепенного изменения данных](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Как программно ссылаться на диапазоны листов в коде](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
