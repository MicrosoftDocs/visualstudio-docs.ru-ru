---
title: Как программно отображать комментарии на листе
description: Сведения о программном отображении и скрытии комментариев в листе Microsoft Excel на уровне документа или приложения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af327a6756189c73f80f624205451274abf19264
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828674"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Как программно отображать комментарии на листе
  Вы можете отображать и скрывать комментарии в листах Microsoft Office Excel программными средствами.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Отображение всех комментариев на листе в настройке уровня документа

1. Присвойте свойству <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> значение **true** , если нужно отображать комментарии; в противном случае присвойте ему значение **false**. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet31":::

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Отображение всех комментариев на листе в надстройке VSTO уровня приложения

1. Присвойте свойству <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> значение **true** , если нужно отображать комментарии; в противном случае присвойте ему значение **false**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet21":::

## <a name="see-also"></a>См. также статью
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Руководство. Программное добавление и удаление комментариев на листе](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
