---
title: Как программно печатать листы
description: Узнайте, как можно использовать Visual Studio для программной печати любого листа в книге Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129493f726967776aa669eb92f6e912ed9c1b11b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827153"
---
# <a name="how-to-programmatically-print-worksheets"></a>Как программно печатать листы

Любой лист в книге можно напечатать.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Печать листа в настройке на уровне документа

### <a name="to-print-a-worksheet"></a>Печать листа

1. Вызовите метод `PrintOut``Sheet1`, запросите две копии и просмотрите документ перед печатью.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet22":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet22":::

   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>Метод позволяет отображать указанный объект в окне **предварительного просмотра** . В следующем коде предполагается, что существует ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> с именем `Sheet1`.

### <a name="to-preview-a-page-before-printing"></a>Предварительный просмотр страницы перед печатью

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> листа.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet23":::

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Печать листа в надстройке VSTO

### <a name="to-print-a-worksheet"></a>Печать листа

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> активного листа, запросите две копи и просмотрите документ перед печатью.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet14":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet14":::

   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>Метод позволяет отображать указанный объект в окне **предварительного просмотра** .

### <a name="to-preview-a-page-before-printing"></a>Предварительный просмотр страницы перед печатью

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> активного листа.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>См. также статью

- [Работа с листами](../vsto/working-with-worksheets.md)
- [Руководство. Программная проверка орфографии на листах](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Ведущий элемент листа](../vsto/worksheet-host-item.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
