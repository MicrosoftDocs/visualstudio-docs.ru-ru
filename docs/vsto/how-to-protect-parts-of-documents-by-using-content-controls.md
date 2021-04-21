---
title: Пошаговое руководство. Защита частей документов с помощью элементов управления содержимым
description: Узнайте, как можно использовать Visual Studio для защиты частей документа Microsoft Word с помощью элементов управления содержимым.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc333871d4f371530db84a0c4f07ab891db2a937
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825476"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Пошаговое руководство. Защита частей документов с помощью элементов управления содержимым
  При защите части документа вы запрещаете пользователям изменять или удалять содержимое в ней. Для защиты частей документа Microsoft Office с помощью элементов управления содержимым можно использовать несколько способов:

- можно защитить элемент управления содержимым;

- можно защитить часть документа, расположенного вне элемента управления содержимым.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a> Защита элемента управления содержимым
 Вы можете запретить пользователям изменять или удалять элемент управления содержимым, задав свойства элемента управления в проекте уровня документа во время разработки или во время выполнения.

 Также можно защитить элементы управления содержимым, которые вы добавляете в документ во время выполнения с помощью проекта надстройки VSTO. Дополнительные сведения см. [в разделе руководство. Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md).

### <a name="to-protect-a-content-control-at-design-time"></a>Защита элемента управления содержимым во время разработки

1. В документе, размещенном в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], выберите элемент управления содержимым, который необходимо защитить.

2. В окне **Свойства** задайте одно или оба из следующих свойств.

    - Чтобы запретить пользователям изменять элемент управления, установите для **локкконтентс** значение **true**.

    - Чтобы запретить пользователям удалять элемент управления, установите для **локкконтентконтрол** значение **true**.

3. Нажмите кнопку **ОК**.

### <a name="to-protect-a-content-control-at-run-time"></a>Защита элемента управления содержимым во время выполнения

1. Задайте `LockContents` для свойства элемента управления содержимым **значение true** , чтобы запретить пользователям изменять элемент управления, и присвойте `LockContentControl` свойству **значение true** , чтобы запретить пользователям удалять элемент управления.

     В следующем примере кода показано использование свойств <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> и <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> двух разных объектов <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в проекте на уровне документа. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `AddProtectedContentControls` обработчика событий `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet2":::

     В следующем примере кода показано использование свойств <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> и <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> двух разных объектов <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в проекте надстройки VSTO. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `AddProtectedContentControls` обработчика событий `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet14":::

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Защита части документа, не входящего в элемент управления содержимым
 Вы можете запретить пользователям изменять часть документа, поместив ее в <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Это полезно в следующих случаях:

- вы хотите защитить область, которая не содержит элементов управления содержимым;

- вы хотите защитить область, в которой уже есть элементы управления содержимым, но текст или другие элементы, которые необходимо защитить, расположены вне элементов управления содержимым.

> [!NOTE]
> При создании элемента <xref:Microsoft.Office.Tools.Word.GroupContentControl>, который содержит внедренные элементы управления содержимым, такие элементы автоматически не защищаются. Чтобы запретить пользователям изменять внедренный элемент управления содержимым, используйте свойство **локкконтентс** элемента управления.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Защита области документа во время разработки

1. В документе, размещенном в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], выберите область, которую необходимо защитить.

2. На ленте перейдите на вкладку **Разработчик** .

    > [!NOTE]
    > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [инструкции. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. В группе **элементы управления** щелкните раскрывающийся список **Группа** , а затем выберите пункт **Группа**.

     Объект <xref:Microsoft.Office.Tools.Word.GroupContentControl>, содержащий защищенную область, создается автоматически в классе `ThisDocument` в проекте. Граница, представляющая элемент управления группы, видна во время разработки, но не во время выполнения.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Защита области документа во время выполнения

1. Программными средствами выберите область, которую требуется защитить, а затем вызовите метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> для создания <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

     Следующий пример кода для проекта уровня документа добавляет текст в первый абзац документа, выделяет первый абзац и создает экземпляр <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `ProtectFirstParagraph` обработчика событий `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet1":::

     Следующий пример кода для проекта надстройки VSTO добавляет текст в первый абзац активного документа, выделяет первый абзац и создает экземпляр <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `ProtectFirstParagraph` обработчика событий `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet15":::

## <a name="see-also"></a>См. также статью
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Элементы управления содержимым](../vsto/content-controls.md)
- [Как добавить элементы управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
