---
title: Инструкции. Программная вставка текста в документы Word
description: Сведения о программной вставке текста в документ Microsoft Word с помощью Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f17828b4617f84cb104761918787b4bbb79f7afc
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827361"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Инструкции. Программная вставка текста в документы Word
  Существует три основных способа вставки текста в документы Microsoft Office Word:

- вставка текста в диапазон;

- замена текста в диапазоне на новый текст;

- использование метода <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> объекта <xref:Microsoft.Office.Interop.Word.Selection> для вставки текста в позиции курсора или выделения.

> [!NOTE]
> Вы также можете вставить текст в элементы управления содержимым и закладки. Дополнительные сведения см. в разделе [элементы управления содержимым](../vsto/content-controls.md) и [элемент управления Bookmark](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Вставить текст в диапазон
 Используйте свойство <xref:Microsoft.Office.Interop.Word.Range.Text%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> для вставки текста в документ.

### <a name="to-insert-text-in-a-range"></a>Вставка текста в диапазон

1. Укажите диапазон в начале документа и вставьте текст **New Text**.

     Следующий пример кода можно использовать в настройке на уровне документа.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet51":::

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet51":::

2. Выберите объект <xref:Microsoft.Office.Interop.Word.Range> , который был расширен от одного символа до длины вставленного текста.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet52":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet52":::

## <a name="replace-text-in-a-range"></a>Замена текста в диапазоне
 Если указанный диапазон содержит текст, весь текст в диапазоне заменяется на вставленный текст.

### <a name="to-replace-text-in-a-range"></a>Замена текста в диапазоне

1. Создайте объект <xref:Microsoft.Office.Interop.Word.Range> , состоящий из первых 12 символов в документе.

     Следующий пример кода можно использовать в настройке на уровне документа.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet53":::

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet53":::

2. Замените эти символы строкой **New Text**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet54":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet54":::

3. Выберите диапазон.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet55":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet55":::

## <a name="insert-text-using-typetext"></a>Вставка текста с помощью TypeText
 Метод <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> вставляет текст в выделение. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> ведет себя по-разному в зависимости от параметров, заданных на компьютере пользователя. Код в следующей процедуре объявляет объектную переменную <xref:Microsoft.Office.Interop.Word.Selection> , а также отключает параметр **Overtype** , если он включен. Если параметр **Overtype** включен, любой текст рядом с курсором будет перезаписан.

### <a name="to-insert-text-using-the-typetext-method"></a>Вставка текста с помощью метода TypeText

1. Объявите переменную объекта <xref:Microsoft.Office.Interop.Word.Selection>.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet57":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet57":::

2. Отключите параметр **Overtype** , если он включен.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet58":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet58":::

3. Проверьте, находится ли текущее выделение у точки вставки.

    Если это так, код вставляет предложение с помощью <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>, а затем знак абзаца с помощью метода <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> .

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet59":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet59":::

4. Код в блоке **ElseIf** проверяет, является ли выделение обычным блоком выделения. Если это так, другой блок **If** проверяет, включен ли параметр **ReplaceSelection** . Если это так, код использует метод <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> выделения, чтобы свернуть его до точки вставки в начале выделенного блока текста. Вставьте текст и знак абзаца.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet60":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet60":::

5. Если выделение не является точкой вставки или блоком выделенного текста, код в блоке **Else** не выполняет никаких действий.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet61":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet61":::

   Можно также использовать <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> метод <xref:Microsoft.Office.Interop.Word.Selection> объекта, который имитирует функциональность клавиши **Backspace** на клавиатуре. Но когда дело доходит до вставки и изменения текста, объект <xref:Microsoft.Office.Interop.Word.Range> предоставляет больше возможностей для управления.

   В следующем примере показан полный код. Чтобы использовать этот пример, запустите код из класса `ThisDocument` или `ThisAddIn` в своем проекте.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet56":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet56":::

## <a name="see-also"></a>См. также статью
- [Руководство. Программное форматирование текста в документах](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Руководство. программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
