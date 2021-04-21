---
title: Руководство. Программная печать документов
description: Узнайте, как напечатать весь документ Microsoft Word или часть документа на принтере по умолчанию.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 47f295a6259b8d722c9c3c714b62fe648bdea1c6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827205"
---
# <a name="how-to-programmatically-print-documents"></a>Руководство. Программная печать документов
  Вы можете распечатать весь документ Microsoft Office Word или часть документа, на принтере по умолчанию.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Печать документа, который является частью настройки на уровне документа

### <a name="to-print-the-entire-document"></a>Печать всего документа

1. Чтобы напечатать весь документ, вызовите в своем проекте метод <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> класса `ThisDocument` . Чтобы использовать этот пример, запустите код из класса `ThisDocument` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-the-document"></a>Печать текущей страницы документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> класса `ThisDocument` в своем проекте и укажите, что необходимо напечатать одну копию текущей страницы. Чтобы использовать этот пример, запустите код из класса `ThisDocument` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet12":::

## <a name="print-a-document-by-using-a-vsto-add-in"></a>Печать документа с помощью надстройки VSTO

### <a name="to-print-an-entire-document"></a>Печать всего документа

1. Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> документа <xref:Microsoft.Office.Interop.Word.Document> , который требуется напечатать. В следующем примере кода печатается активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-a-document"></a>Печать текущей страницы документа

1. Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> класса <xref:Microsoft.Office.Interop.Word.Document> объекта, который требуется напечатать, и укажите, что необходимо напечатать одну копию текущей страницы. В следующем примере кода печатается активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet12":::

## <a name="see-also"></a>См. также статью
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
