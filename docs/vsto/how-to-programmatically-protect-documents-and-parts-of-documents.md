---
title: Программная защита документов и частей документов
description: Узнайте, как можно добавить защиту в документы Microsoft Word, чтобы запретить пользователям вносить изменения в документ.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af3cc1d9c34bf0d6dc503ca2aabe35de5848265c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827608"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Руководство. Программная защита документов и частей документов
  Вы можете добавлять защиту в документы Microsoft Office Word, чтобы запретить пользователям вносить изменения в документ.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Вы также можете помечать определенные части документа как исключения, чтобы указанные пользователи могли изменять только эти области документа. Например, можно защитить весь документ, кроме определенной закладки. При необходимости можно добавить пароль, чтобы пользователи, не знающие пароль, не могли удалить защиту документа.

> [!NOTE]
> В следующем примере защита паролем не используется; однако вы можете рассмотреть возможность использования пароля при добавлении защиты документов. Дополнительные сведения см. в образце средства защиты документов в примерах [разработки Office и пошаговых руководствах](../vsto/office-development-samples-and-walkthroughs.md).

 Для защиты частей документов можно также использовать элементы управления содержимым. Дополнительные сведения см. [в разделе руководство. Защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Защита документа, который является частью настройки уровня документа

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Защита документа, который является частью настройки уровня документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> класса `ThisDocument` в проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Исключение элемента управления "Закладка" из защиты документа

1. Защитите весь документ при помощи метода <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

2. Исключите `Bookmark1` из защиты документа.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet112":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet112":::

### <a name="compile-the-code"></a>Компиляция кода
 Чтобы использовать эти примеры кода, выполняйте их из класса `ThisDocument` в своем проекте. В этих примерах кода предполагается, что элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> с именем `Bookmark1` существует в документе, в котором отображается этот код.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Защита документа с помощью надстройки VSTO

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Защита документа с помощью надстройки VSTO уровня приложения

1. Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> документа <xref:Microsoft.Office.Interop.Word.Document> , который требуется защитить.

     В следующем примере кода защищается активный документ. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet111":::

## <a name="see-also"></a>См. также статью
- [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)
- [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)
- [Как разрешите выполнение кода для документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
