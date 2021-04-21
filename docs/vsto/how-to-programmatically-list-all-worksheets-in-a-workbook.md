---
title: Руководство. Программное перечисление всех листов в книге
description: Узнайте, как программным путем получить список всех листов в книге Microsoft Excel с помощью Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c0cdd57c801617d8b3c37df28b91faae378bc4cc
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824904"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Руководство. Программное перечисление всех листов в книге
  Класс <xref:Microsoft.Office.Interop.Excel.Workbook> предоставляет объект <xref:Microsoft.Office.Interop.Excel.Worksheets>. Этот объект содержит коллекцию всех объектов <xref:Microsoft.Office.Interop.Excel.Worksheet> в книге.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Составление списка существующих в книге листов в настройке уровня документа

1. Следует выполнить итерацию коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets> и отправить имя каждого листа в смещение ячейки из элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet21":::

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Составление списка существующих в книге листов в надстройке VSTO

1. Следует выполнить итерацию коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets> и отправить имя каждого листа в смещение ячейки из объекта <xref:Microsoft.Office.Interop.Excel.Range>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>См. также статью
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Как программно добавлять новые листы в книги](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Руководство. Программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
