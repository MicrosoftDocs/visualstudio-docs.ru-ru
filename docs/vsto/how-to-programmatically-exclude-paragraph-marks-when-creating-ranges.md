---
title: Исключать знаки абзаца при создании диапазонов программным способом
description: Узнайте, как программным способом исключить знаки абзаца при создании диапазонов в документе Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c0929ccf3bb2567099dc7f3b795ad2257da0edb3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825801"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Руководство. программное исключение знаков абзаца при создании диапазонов
  При каждом создании объекта <xref:Microsoft.Office.Interop.Word.Range> на основе абзаца все непечатаемые символы, такие как знаки абзаца, включаются в диапазон. Можно вставить текст из исходного абзаца в целевой абзац. Если вы не хотите разделять целевой абзац на отдельные абзацы, то необходимо сначала удалить знаки абзаца из исходного абзаца. Кроме того, поскольку сведения о форматировании абзаца хранятся в знаке абзаца, вы можете не захотеть включать их при вставке диапазона в существующий абзац.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 В приведенной ниже процедуре объявляются две строковые переменные, извлекается содержимое первого и второго абзаца в активном документе, а потом их содержимое обменивается. Затем в примере демонстрируется удаление знака абзаца из диапазона с помощью метода <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> и вставка текста в абзаце.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Управление структурой абзаца при вставке текста

1. Создайте две переменные диапазона для первого и второго абзаца и извлеките их содержимое при помощи свойства <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .

     Следующий пример кода можно использовать в настройке на уровне документа.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet27":::

     Приведенный ниже пример кода можно использовать в надстройке VSTO уровня приложения. В этом примере кода используется активный документ.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet27":::

2. Назначьте свойство <xref:Microsoft.Office.Interop.Word.Range.Text%2A> , переключающее текст между двумя абзацами.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet28":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet28":::

3. По очереди выбирайте каждый диапазон и делайте паузу, чтобы отобразить результаты в окне сообщения.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet29":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet29":::

4. Настройте `firstRange` с помощью метода <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> , чтобы символ абзаца больше не являлся частью `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet30":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet30":::

5. Замените оставшийся текст в первом абзаце, назначив новую строку в свойстве <xref:Microsoft.Office.Interop.Word.Range.Text%2A> диапазона.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet31":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet31":::

6. Замените текст в `secondRange`, включая знак абзаца.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet32":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet32":::

7. Выберите `firstRange` и сделайте паузу для отображения результатов в окне сообщения, а затем сделайте то же самое с `secondRange`.

     Поскольку `firstRange` был переопределен, чтобы исключить знак абзаца, первоначальное форматирование абзаца сохраняется. Однако вместо знака абзаца в `secondRange`было вставлено предложение, удаляющее отдельный абзац.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet33":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet33":::

     Исходное содержимое обоих диапазонов было сохранено в виде строк, поэтому можно восстановить исходное состояние документа.

8. Измените `firstRange` , чтобы включить знак абзаца с помощью <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> метода для односимвольной позиции.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet34":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet34":::

9. Удалите `secondRange`. Это восстановит третий абзац в исходное положение.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet35":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet35":::

10. Восстановите первоначальный текст абзаца в `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet36":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet36":::

11. Используйте метод <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> для вставки исходного содержимого второго абзаца после `firstRange`, а затем выберите `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet37":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet37":::

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Управление структурой абзаца при вставке текста в настройках уровня документа

1. В следующем примере показан полный метод для настройки на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet26":::

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Управление структурой абзаца при вставке текста в надстройку VSTO

1. В следующем примере показан полный метод для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet26":::

## <a name="see-also"></a>См. также статью
- [Руководство. программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Руководство. программное сворачивание диапазонов или выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Инструкции. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Как программно сбрасывать диапазоны в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
