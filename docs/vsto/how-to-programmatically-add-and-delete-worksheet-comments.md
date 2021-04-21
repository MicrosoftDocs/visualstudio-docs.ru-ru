---
title: Руководство. Программное добавление и удаление комментариев на листе
description: Сведения о программном добавлении и удалении комментариев в Microsoft Office листах Excel. Комментарии можно добавлять только в отдельные ячейки, а не в диапазоны с несколькими ячейками.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 20b718be3bec6cac3ee6c0b0985fa6efca867189
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826945"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Руководство. Программное добавление и удаление комментариев на листе
  Вы можете добавлять и удалять комментарии в листах Microsoft Office Excel программными средствами. Комментарии можно добавлять только в отдельные ячейки, а не в диапазоны из нескольких ячеек.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Добавление и удаление комментария в проекте уровня документа
 В следующих примерах предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `dateComment` в одной ячейке в листе с именем `Sheet1`.

### <a name="to-add-a-new-comment-to-a-named-range"></a>Добавление нового комментария в именованный диапазон

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> и укажите текст примечания. Этот код следует разместить в классе `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet30":::

#### <a name="to-delete-a-comment-from-a-named-range"></a>Удаление комментария из именованного диапазона

1. Проверьте наличие комментария в диапазоне и удалите его. Этот код следует разместить в классе `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet29":::

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Добавление и удаление комментария в проекте надстройки VSTO
 В следующих примерах предполагается, что имеется элемент управления <xref:Microsoft.Office.Interop.Excel.Range> с именем `dateComment` в одной ячейке в активном листе.

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Добавление нового комментария в диапазон Excel

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> элемента управления <xref:Microsoft.Office.Interop.Excel.Range> и укажите текст примечания.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet20":::

### <a name="to-delete-a-comment-from-an-excel-range"></a>Удаление нового комментария из диапазона Excel

1. Проверьте наличие комментария в диапазоне и удалите его.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet19":::

## <a name="see-also"></a>См. также статью
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Как программно отображать комментарии на листе](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
