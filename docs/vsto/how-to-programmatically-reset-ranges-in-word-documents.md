---
title: Как программно сбрасывать диапазоны в документах Word
description: Узнайте, как можно использовать Visual Studio для программного изменения размера существующего диапазона в документе Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ae3b8f92231b77d81c1ef68e0929ccd000653b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824150"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Как программно сбрасывать диапазоны в документах Word
  Используйте метод <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> для изменения размеров существующего диапазона в документе Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Сброс существующего диапазона

1. Установите исходный диапазон, начиная с первых семи знаков в документе.

     Следующий пример кода можно использовать в настройке на уровне документа.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet43":::

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet43":::

2. Используйте <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> для начала диапазона во втором предложении и завершения его в конце пятого предложения.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet44":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet44":::

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Сброс существующего диапазона в настройке уровня документа

1. В следующем примере показан полный код для настройки уровня документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet42":::

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Сброс существующего диапазона в надстройке VSTO

1. В следующем примере показан полный пример для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet42":::

## <a name="see-also"></a>См. также статью
- [Руководство. программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Как программно получить начальные и конечные символы в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Руководство. программное сворачивание диапазонов или выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
