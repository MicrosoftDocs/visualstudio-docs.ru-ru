---
title: Руководство. программное выполнение вычислений Excel
description: Узнайте, как можно использовать Visual Studio для программного выполнения вычислений в книге Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9fdc9cbc1966ac0fd862b795d66c7004f5089499
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823968"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Руководство. программное выполнение вычислений Excel
  Аналогичный процесс используется для выполнения вычислений в <xref:Microsoft.Office.Tools.Excel.NamedRange> элементе управления или в собственном объекте Excel Range.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Выполнение вычислений в элементе управления NamedRange
 В следующем примере создается в <xref:Microsoft.Office.Tools.Excel.NamedRange> ячейке a1, а затем вычисляется ячейка. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

### <a name="to-run-calculations-in-a-namedrange-control"></a>Выполнение вычислений в элементе управления NamedRange

1. Создайте именованный диапазон.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet75":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet75":::

2. Вызовите <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> метод указанного диапазона.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet76":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet76":::

## <a name="run-calculations-in-a-native-excel-range"></a>Выполнение вычислений в собственном диапазоне Excel

### <a name="to-run-calculations-in-a-native-excel-range"></a>Выполнение вычислений в собственном диапазоне Excel

1. Создайте именованный диапазон.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet30":::

2. Вызовите <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> метод указанного диапазона.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet31":::

## <a name="see-also"></a>См. также статью
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
