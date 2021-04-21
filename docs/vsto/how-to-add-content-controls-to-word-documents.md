---
title: Как добавить элементы управления содержимым в документы Word
description: Узнайте, что в проектах на уровне документа Word элементы управления содержимым можно добавлять в документ в проекте во время разработки или во время выполнения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a902e85f8c53aa7a3d1ebe3b6480a7c68fa60601
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827907"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Как добавить элементы управления содержимым в документы Word
  В проектах на уровне документа Word элементы управления содержимым можно добавлять в документ во время разработки или во время выполнения. В проектах надстройки VSTO для Word элементы управления содержимым можно добавлять в любой открытый документ во время выполнения.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 В этом разделе описываются следующие задачи.

- [Добавление элементов управления содержимым во время разработки](#designtime)

- [Добавление элементов управления содержимым во время выполнения в проекте уровня документа](#runtimedoclevel)

- [Добавление элементов управления содержимым во время выполнения в проекте надстройки VSTO](#runtimeaddin)

  Дополнительные сведения об элементах управления содержимым см. в разделе [элементы управления содержимым](../vsto/content-controls.md).

## <a name="add-content-controls-at-design-time"></a><a name="designtime"></a> Добавление элементов управления содержимым во время разработки
 Вы можете добавить элементы управления содержимым в документ Word в проекте на уровне документа во время разработки несколькими способами.

- Добавьте элемент управления содержимым из вкладки **Элементы управления Word****панели элементов**.

- Добавьте элемент управления содержимым в документ так же, как вы добавляете управляемый элемент управления содержимым в Word.

- Перетащите элемент управления в документ из окна **Источники данных** . Это полезно, если нужно одновременно привязать элемент управления к данным при его создании. Дополнительные сведения см. в статьях [как заполнить документы данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md) и [как заполнять документы данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Добавление элемента управления содержимым в документ с помощью панели элементов

1. В документе, который размещен в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , поместите курсор там, где необходимо добавить элемент управления содержимым, или выделите текст, который заменит элемент управления содержимым.

2. Откройте **панель элементов** и щелкните вкладку **Элементы управления Word** .

3. Добавьте элемент управления одним из следующих способов.

    - Дважды щелкните элемент управления содержимым в **панели элементов**.

         или

    - Щелкните элемент управления содержимым на **панели элементов** и нажмите клавишу **Ввод** .

         или

    - Перетащите элемент управления содержимым из **панели элементов** в документ. Элемент управления содержимым добавляется в текущее выделение в документе, а не в позиции указателя мыши.

> [!NOTE]
> Невозможно добавить <xref:Microsoft.Office.Tools.Word.GroupContentControl> с помощью **панели элементов**. <xref:Microsoft.Office.Tools.Word.GroupContentControl> можно добавлять только в Word или во время выполнения.

> [!NOTE]
> Visual Studio не предоставляет элемент управления содержимым «Флажок» в панели элементов. Чтобы добавить элемент управления содержимым «Флажок» в документ, необходимо создать <xref:Microsoft.Office.Tools.Word.ContentControl> программно. Дополнительные сведения см. в разделе [элементы управления содержимым](../vsto/content-controls.md).

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Добавление элемента управления содержимым «Флажок» в документ из Word

1. В документе, который размещен в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , поместите курсор там, где необходимо добавить элемент управления содержимым, или выделите текст, который заменит элемент управления содержимым.

2. На ленте перейдите на вкладку **Разработчик** .

    > [!NOTE]
    > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [инструкции. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. В группе **Элементы управления** щелкните значок элемента управления содержимым, который требуется добавить.

## <a name="add-content-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Добавление элементов управления содержимым во время выполнения в проекте уровня документа
 Элементы управления содержимым можно добавить в документ программным образом во время выполнения с помощью методов свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> класса `ThisDocument` в проекте. У каждого метода есть три перегрузки, которые можно использовать для добавления элемента управления содержимым следующими способами:

- добавление элемента управления в текущее выделение;

- добавление элемента управления в указанный диапазон;

- добавление элемента управления, основанного на управляемом элементе управления содержимым, в документ.

  При закрытии документа динамически созданные элементы управления содержимым не сохраняются в документе. Однако неуправляемый элемент управления содержимым остается в документе. Можно повторно создать элемент управления содержимым, основанный на управляемом элементе управления содержимым, при очередном открытии документа. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

> [!NOTE]
> Чтобы добавить элемент управления содержимым «Флажок» в документ в проекте Word 2010, необходимо создать объект <xref:Microsoft.Office.Tools.Word.ContentControl> . Дополнительные сведения см. в разделе [элементы управления содержимым](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Добавление элемента управления содержимым в текущее выделение

1. Используйте <xref:Microsoft.Office.Tools.Word.ControlCollection> метод с именем `Add` \<*control class*> (где *Control class* — это имя класса элемента управления содержимым, который вы хотите добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), и у которого есть единственный параметр для имени нового элемента управления.

     Следующий пример кода использует метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> , чтобы добавить новый <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в начало документа. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `AddRichTextControlAtSelection` обработчика событий `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet700":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet700":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Добавление элемента управления в указанный диапазон

1. Используйте <xref:Microsoft.Office.Tools.Word.ControlCollection> метод с именем `Add` \<*control class*> (где *Control class* — это имя класса элемента управления содержимым, который вы хотите добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), и у которого есть <xref:Microsoft.Office.Interop.Word.Range> параметр.

     Следующий пример кода использует метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> , чтобы добавить новый <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в начало документа. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `AddRichTextControlAtRange` обработчика событий `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet701":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet701":::

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Добавление элемента управления содержимым, основанного на управляемом элементе управления содержимым

1. Используйте <xref:Microsoft.Office.Tools.Word.ControlCollection> метод с именем `Add` \<*control class*> (где *Control class* — это имя класса элемента управления содержимым, который вы хотите добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), и у которого есть `Microsoft.Office.Interop.Word.ContentControl` параметр.

     В следующем примере кода метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> используется для создания нового объекта <xref:Microsoft.Office.Tools.Word.RichTextContentControl> для каждого управляемого элемента управления форматированием текста, который есть в документе. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `CreateRichTextControlsFromNativeControls` обработчика событий `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet702":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet702":::

## <a name="add-content-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Добавление элементов управления содержимым во время выполнения в проекте надстройки VSTO
 Вы можете добавить элементы управления содержимым программным способом в любой открытый документ во время выполнения с помощью надстройки VSTO. Для этого следует создать ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> , основанный на открытом документе, а затем использовать методы свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> этого ведущего элемента. У каждого метода есть три перегрузки, которые можно использовать для добавления элемента управления содержимым следующими способами:

- добавление элемента управления в текущее выделение;

- добавление элемента управления в указанный диапазон;

- добавление элемента управления, основанного на управляемом элементе управления содержимым, в документ.

  При закрытии документа динамически созданные элементы управления содержимым не сохраняются в документе. Однако неуправляемый элемент управления содержимым остается в документе. Можно повторно создать элемент управления содержимым, основанный на управляемом элементе управления содержимым, при очередном открытии документа. Дополнительные сведения см. [в разделе Сохранение динамических элементов управления в документах Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Дополнительные сведения о создании ведущих элементов в проектах надстроек VSTO см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

> [!NOTE]
> Чтобы добавить элемент управления содержимым «Флажок», необходимо создать объект <xref:Microsoft.Office.Tools.Word.ContentControl> . Дополнительные сведения см. в разделе [элементы управления содержимым](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Добавление элемента управления содержимым в текущее выделение

1. Используйте <xref:Microsoft.Office.Tools.Word.ControlCollection> метод с именем `Add` \<*control class*> (где *Control class* — это имя класса элемента управления содержимым, который вы хотите добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), и у которого есть единственный параметр для имени нового элемента управления.

     Следующий пример кода использует метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> , чтобы добавить новый <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в начало активного документа. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `AddRichTextControlAtSelection` обработчика событий `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet1":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Добавление элемента управления в указанный диапазон

1. Используйте <xref:Microsoft.Office.Tools.Word.ControlCollection> метод с именем `Add` \<*control class*> (где *Control class* — это имя класса элемента управления содержимым, который вы хотите добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), и у которого есть <xref:Microsoft.Office.Interop.Word.Range> параметр.

     Следующий пример кода использует метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> , чтобы добавить новый <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в начало активного документа. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `AddRichTextControlAtRange` обработчика событий `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet2":::

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Добавление элемента управления содержимым, основанного на управляемом элементе управления содержимым

1. Используйте <xref:Microsoft.Office.Tools.Word.ControlCollection> метод с именем `Add` \<*control class*> (где *Control class* — это имя класса элемента управления содержимым, который вы хотите добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), и у которого есть `Microsoft.Office.Interop.Word.ContentControl` параметр.

     В следующем примере кода метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> используется для создания нового объекта <xref:Microsoft.Office.Tools.Word.RichTextContentControl> для каждого управляемого элемента управления форматированием текста в документе после его открытия. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet3":::

     Для C# необходимо присоединить обработчик `Application_DocumentOpen` к событию <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>См. также статью
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)
