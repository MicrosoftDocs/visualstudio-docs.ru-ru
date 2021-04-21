---
title: Программное добавление изображений и документов Word Art в документы
description: Узнайте, как можно добавлять рисунки и графические объекты в документы во время разработки или во время выполнения.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 445857200dfb269dd71f7cb3d446d025048cb3ac
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828440"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Руководство. Программное добавление изображений и документов Word Art в документы
  Вы можете добавлять изображения и графические объекты в документы во время разработки или во время выполнения. WordArt позволяет добавлять декоративный текст в документы Microsoft Office Word. Эти специальные текстовые эффекты представляют собой графические объекты, которые можно настроить и вставить в документ.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Добавление рисунка во время разработки
 При создании настройки на уровне документа вы можете добавить изображение в документ во время разработки.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Добавление рисунка в документ Word во время разработки

1. Поместите курсор в место вставки изображения в документе.

2. Щелкните вкладку **Вставка** ленты.

3. В группе **иллюстраций** щелкните **Рисунок**.

4. В диалоговом окне **Вставка рисунка** перейдите к рисунку, который необходимо вставить, и нажмите кнопку **Вставить**.

     Рисунок добавляется в документ в текущем положении курсора.

## <a name="add-a-picture-at-run-time"></a>Добавить изображение во время выполнения
 Рисунок можно вставить в документ в текущем положении курсора.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Добавление рисунка в позиции курсора

1. Вызовите метод <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> коллекции <xref:Microsoft.Office.Interop.Word.InlineShapes> и передайте имя файла.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet108":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet108":::

## <a name="add-wordart-at-design-time"></a>Добавление объекта WordArt во время разработки
 При создании настройки на уровне документа вы можете добавить объект WordArt в документ во время разработки.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Добавление объекта WordArt в документ Word во время разработки

1. Поместите курсор в место вставки объекта WordArt в документе.

2. Щелкните вкладку **Вставка** ленты.

3. В **текстовой** группе щелкните **объект WordArt**, а затем выберите стиль WordArt.

4. Добавьте текст, который должен появиться в документе, в диалоговое окно **изменение текста WordArt** и нажмите кнопку **ОК**.

     Текст добавляется к документу с выбранным стилем WordArt.

## <a name="add-wordart-at-run-time"></a>Добавление объекта WordArt во время выполнения
 Вы можете вставить объект WordArt в документ в текущем положении курсора. Процедура вставки отличается для настроек на уровне документа и надстроек VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Добавление объекта WordArt в положении курсора в настройке уровня документа

1. Получите левую и верхнюю позицию текущего положения курсора.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet109":::

2. Вызовите метод <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> объекта <xref:Microsoft.Office.Interop.Word.Shapes> в документе.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet110":::

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Добавление объекта WordArt в положении курсора в надстройке VSTO

1. Получите левую и верхнюю позицию текущего положения курсора.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet109":::

2. Вызовите метод <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> объекта <xref:Microsoft.Office.Interop.Word.Shapes> активного документа (или другого указанного документа).

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet110":::

## <a name="compile-the-code"></a>Компиляция кода

- На диске C должен существовать рисунок с именем *SamplePicture.jpg* .

## <a name="see-also"></a>См. также статью
- [Руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)
- [Инструкции. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Как программным способом восстановить выделенные элементы после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Руководство. Программное сохранение документов](../vsto/how-to-programmatically-save-documents.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
