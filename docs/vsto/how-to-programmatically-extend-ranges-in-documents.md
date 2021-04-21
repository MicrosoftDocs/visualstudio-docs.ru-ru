---
title: Руководство. программное расширение диапазонов в документах
description: Узнайте, как можно программным способом расширить диапазоны начальной и конечной точек в документе Microsoft Word на уровне документа или приложения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7a539bbbc4ad8d73477e660ef9903ac51dce712f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826529"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Руководство. программное расширение диапазонов в документах
  После определения объекта <xref:Microsoft.Office.Interop.Word.Range> в документе Microsoft Office Word вы изменяете его начальную и конечную точки с помощью методов <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> и <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . Методы <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> и <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> принимают те же два аргумента, *Unit* и *Count*. Методы *Count* — это количество единиц для перемещения, и аргумент *Unit* может иметь одно из следующих <xref:Microsoft.Office.Interop.Word.WdUnits> значений:

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  В следующем примере определяется диапазон в семь символов. Затем начальная позиция этого диапазона перемещается на семь символов после исходной начальной позиции. Поскольку конечная позиция диапазона также находится через семь символов после начальной позиции, результатом является диапазон, состоящий из нуля символов. Затем код перемещает конечную позицию на семь символов после текущей конечной позиции.

## <a name="to-extend-a-range"></a>Расширение диапазона

1. Определите диапазон символов. Дополнительные сведения см. в разделе [инструкции. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

     Следующий пример кода можно использовать в настройке на уровне документа.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet39":::

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet39":::

2. Используйте метод <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> , чтобы переместить начальную позицию диапазона.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet40":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet40":::

3. Используйте метод <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> , чтобы переместить конечную позицию диапазона.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet41":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet41":::

## <a name="document-level-customization-code"></a>Код настройки уровня документа

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Расширение диапазона в настройке на уровне документа

1. В следующем примере показан полный код для настройки на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet38":::

## <a name="vsto-add-in-code"></a>Код надстройки VSTO

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Расширение диапазона в надстройке VSTO уровня приложения

1. В следующем примере показан полный код для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet38":::

## <a name="see-also"></a>См. также статью
- [Как программно сбрасывать диапазоны в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Руководство. программное сворачивание диапазонов или выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Как программно получить начальные и конечные символы в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Руководство. программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
