---
title: Руководство. Программное определение и выбор диапазонов в документах
description: Узнайте, как можно программно определять и выбирать диапазоны в документах Microsoft Word с помощью объекта Range.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3a5dc0c7fb9f3e9a2b4a15447f81239db973c215
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825957"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Руководство. Программное определение и выбор диапазонов в документах
  Вы можете определить диапазон в документе Microsoft Office Word с помощью объекта <xref:Microsoft.Office.Interop.Word.Range>. Можно выбрать весь документ несколькими способами, например с помощью <xref:Microsoft.Office.Interop.Word.Range.Select%2A> метода <xref:Microsoft.Office.Interop.Word.Range> объекта или с помощью свойства Content <xref:Microsoft.Office.Tools.Word.Document> класса (в настройке на уровне документа) или <xref:Microsoft.Office.Interop.Word.Document> класса (в надстройке VSTO)...

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Определение диапазона
 В следующем примере показано, как создать объект <xref:Microsoft.Office.Interop.Word.Range>, включающий первые семь символов в активном документе, в том числе непечатаемые символы. Затем выполняется выбор текста в пределах диапазона.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Определение диапазона в настройке на уровне документа

1. Добавьте диапазон в документ, передав начальный и последний символ в метод <xref:Microsoft.Office.Tools.Word.Document.Range%2A> класса <xref:Microsoft.Office.Tools.Word.Document>. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet18":::

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Определение диапазона с помощью надстройки VSTO

1. Добавьте диапазон в документ, передав начальный и последний символ в метод <xref:Microsoft.Office.Interop.Word._Document.Range%2A> класса <xref:Microsoft.Office.Interop.Word.Document>. Следующий пример кода добавляет диапазон в активный документ. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet18":::

## <a name="select-a-range-in-a-document-level-customization"></a>Выбор диапазона в настройке на уровне документа
 В следующих примерах показано, как выделить весь документ с помощью метода <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> или с помощью свойства <xref:Microsoft.Office.Tools.Word.Document.Content%2A> класса <xref:Microsoft.Office.Tools.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Выбор всего документа как диапазона с помощью метода Select

1. Используйте метод <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>, который содержит весь документ. Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Выбор всего документа как диапазона с помощью свойства Content

1. Используйте свойство <xref:Microsoft.Office.Tools.Word.Document.Content%2A>, чтобы определить диапазон, который содержит весь документ.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet20":::

   Для определения диапазона также можно использовать методы и свойства других объектов.

### <a name="to-select-a-sentence-in-the-active-document"></a>Выделение предложения в активном документе

1. Задайте диапазон с помощью коллекции <xref:Microsoft.Office.Interop.Word.Sentences>. Используйте индекс предложения, которое нужно выбрать.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet21":::

   Еще один способ выделения предложения состоит в том, чтобы вручную установить начальное и конечное значение для диапазона.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Выделение предложения вручную с помощью установки начального и конечного значений

1. Создайте переменную диапазона.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet23":::

2. Проверьте, есть ли в документе по крайней мере два предложения, задайте *начальные* и *конечные* аргументы диапазона, а затем выберите диапазон.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet24":::

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Выбор диапазона с помощью надстройки VSTO
 В следующих примерах показано, как выделить весь документ с помощью метода <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> или с помощью свойства <xref:Microsoft.Office.Interop.Word._Document.Content%2A> класса <xref:Microsoft.Office.Interop.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Выбор всего документа как диапазона с помощью метода Select

1. Используйте метод <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>, который содержит весь документ. Следующий пример кода выделяет содержимое активного документа. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Выбор всего документа как диапазона с помощью свойства Content

1. Используйте свойство <xref:Microsoft.Office.Interop.Word._Document.Content%2A>, чтобы определить диапазон, который содержит весь документ.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet20":::

   Для определения диапазона также можно использовать методы и свойства других объектов.

### <a name="to-select-a-sentence-in-the-active-document"></a>Выделение предложения в активном документе

1. Задайте диапазон с помощью коллекции <xref:Microsoft.Office.Interop.Word.Sentences>. Используйте индекс предложения, которое нужно выбрать.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet21":::

   Еще один способ выделения предложения состоит в том, чтобы вручную установить начальное и конечное значение для диапазона.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Выделение предложения вручную с помощью установки начального и конечного значений

1. Создайте переменную диапазона.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet23":::

2. Проверьте, есть ли в документе по крайней мере два предложения, задайте *начальные* и *конечные* аргументы диапазона, а затем выберите диапазон.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet24":::

## <a name="see-also"></a>См. также статью
- [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)
- [Руководство. программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Как программно получить начальные и конечные символы в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Руководство. программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Как программно сбрасывать диапазоны в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Руководство. программное сворачивание диапазонов или выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Руководство. программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
