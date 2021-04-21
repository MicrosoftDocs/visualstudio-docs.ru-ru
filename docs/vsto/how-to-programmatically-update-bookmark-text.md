---
title: Руководство. Программное обновление текста закладок
description: Узнайте, как можно использовать Visual Studio для программной вставки текста в закладку заполнителя в документе Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f67dbbe4d1d5c24d617f9cbc49a58ec2d134e90b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826204"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Руководство. Программное обновление текста закладок
  Вы можете вставить текст в закладку-заполнитель в документе Microsoft Office Word, чтобы позднее извлечь или заменить текст закладки. При разработке настройки на уровне документа можно обновить текст в элементе управления <xref:Microsoft.Office.Tools.Word.Bookmark> с привязкой к данным. Дополнительные сведения см. [в разделе Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Объект закладки может быть одного из двух типов.

- Элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark>.

   Элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> расширяют неуправляемые объекты <xref:Microsoft.Office.Interop.Word.Bookmark>, реализуя привязку к данным и предоставляя события. Дополнительные сведения об элементах управления ведущего приложения см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

- Собственный объект <xref:Microsoft.Office.Interop.Word.Bookmark>.

   У объектов <xref:Microsoft.Office.Interop.Word.Bookmark> нет событий или возможностей для привязки данных.

  Поведение <xref:Microsoft.Office.Interop.Word.Bookmark> и <xref:Microsoft.Office.Tools.Word.Bookmark> при назначении текста закладке отличается. Дополнительные сведения см. в разделе [элемент управления Bookmark](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Использование элементов управления ведущего приложения

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Обновление содержимого закладки с помощью элемента управления Bookmark

1. Создайте процедуру, которая принимает аргумент `bookmark` в качестве имени закладки и аргумент `newText` в качестве строки, назначаемой свойству <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.

    > [!NOTE]
    > Назначение текста свойству <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> или <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> не приводит к удалению закладки.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet63":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet63":::

2. Назначьте строку *newText* <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> свойству объекта <xref:Microsoft.Office.Tools.Word.Bookmark> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet64":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet64":::

## <a name="use-word-objects"></a>Использование объектов Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Обновление содержимого закладки с помощью объекта Bookmark приложения Word

1. Создайте процедуру, которая принимает аргумент `bookmark` в качестве имени <xref:Microsoft.Office.Interop.Word.Bookmark> и аргумент `newText` в качестве строки, назначаемой свойству <xref:Microsoft.Office.Interop.Word.Range.Text%2A> закладки.

    > [!NOTE]
    > При присвоении текста собственному объекту <xref:Microsoft.Office.Interop.Word.Bookmark> Word закладка удаляется.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet65":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet65":::

2. Назначьте строку *newText* <xref:Microsoft.Office.Interop.Word.Range.Text%2A> свойству закладки, которая автоматически удаляет закладку. Затем снова добавьте закладку в коллекцию <xref:Microsoft.Office.Interop.Word.Bookmarks>.

     Следующий пример кода можно использовать в настройке на уровне документа.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet66":::

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet66":::

## <a name="see-also"></a>См. также статью
- [Инструкции. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)
- [Элемент управления Bookmark](../vsto/bookmark-control.md)
