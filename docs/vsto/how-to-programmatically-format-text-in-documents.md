---
title: Руководство. Программное форматирование текста в документах
description: Узнайте, как можно использовать объект Range для программного форматирования текста в документе Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b91486c193b7b3fdba3b4c5cbbe86f58ffa7f06c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827881"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Руководство. Программное форматирование текста в документах
  Вы можете использовать объект <xref:Microsoft.Office.Interop.Word.Range> для форматирования текста в документе Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Следующий пример выделяет первый абзац в документе и изменяет размер шрифта, имя шрифта и тип выравнивания. Затем он выбирает диапазон и отображает окно сообщения о приостановке перед выполнением следующего раздела кода. В следующем разделе вызывается метод Undo <xref:Microsoft.Office.Tools.Word.Document> ведущего элемента (для настройки на уровне документа) или <xref:Microsoft.Office.Interop.Word.Document> класса (для надстройки VSTO) три раза. Применяется стиль «Обычный отступ» и отображается окно сообщения о приостановке выполнения кода. Затем код вызывает метод <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> один раз и показывает окно сообщения.

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="to-format-text-using-a-document-level-customization"></a>Форматирование текста с помощью настройки на уровне документа

1. Следующий пример можно использовать в настройке на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet62":::

## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Форматирование текста с использованием надстройки VSTO

1. Следующий пример можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet62":::

## <a name="see-also"></a>См. также статью
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Инструкции. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Руководство. Программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
