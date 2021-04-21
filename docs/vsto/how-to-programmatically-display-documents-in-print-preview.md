---
title: Руководство. программное отображение документов в режиме предварительного просмотра
description: Сведения о программном отображении документов в режиме предварительного просмотра в документе Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 90979fbc7cd0b46329b8d9e9bc142e8cf0066db0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825892"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Руководство. программное отображение документов в режиме предварительного просмотра
  Если решение создает отчет, может потребоваться отображение отчета пользователю в режиме предварительного просмотра отчета.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Процедуры для настроек на уровне документа

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Отображение документа в режиме предварительного просмотра путем вызова метода PrintPreview

1. Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> класса <xref:Microsoft.Office.Tools.Word.Document> . Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Отображение документа в режиме предварительного просмотра путем установки свойства PrintPreview

1. Присвойте свойству <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> объекта <xref:Microsoft.Office.Interop.Word.Application> значение **true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="procedures-for-vsto-add-ins"></a>Процедуры для надстроек VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Отображение документа в режиме предварительного просмотра путем вызова метода PrintPreview

1. Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> документа <xref:Microsoft.Office.Interop.Word.Document> , который требуется открыть в режиме предварительного просмотра. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Отображение документа в режиме предварительного просмотра путем установки свойства PrintPreview

1. Присвойте свойству <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> объекта <xref:Microsoft.Office.Interop.Word.Application> значение **true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="see-also"></a>См. также статью
- [Руководство. Программная печать документов](../vsto/how-to-programmatically-print-documents.md)
- [Руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)
- [Руководство. Программное создание новых документов](../vsto/how-to-programmatically-create-new-documents.md)
