---
title: Руководство. Добавление элементов управления Bookmark в документы Word
description: Изучите, что в проектах уровня документа можно добавлять элементы управления Bookmark в документ в проекте во время разработки или во время выполнения.
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0a5520582db9919417b1c70d773355901ac0b0a5
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826607"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Руководство. Добавление элементов управления Bookmark в документы Word
  В проектах на уровне документа элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> можно добавлять в документ во время разработки или во время выполнения. В проектах надстроек VSTO вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в любой открытый документ во время выполнения.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 В этом разделе описываются следующие задачи.

- [Добавление элементов управления Bookmark во время разработки](#designtime)

- [Добавление элементов управления Bookmark во время выполнения в проекте уровня документа](#runtimedoclevel)

- [Добавление элементов управления Bookmark во время выполнения в проекте надстройки VSTO](#runtimeaddin)

  Дополнительные сведения об <xref:Microsoft.Office.Tools.Word.Bookmark> элементах управления см. в разделе [элемент управления Bookmark](../vsto/bookmark-control.md).

## <a name="add-bookmark-controls-at-design-time"></a><a name="designtime"></a> Добавление элементов управления Bookmark во время разработки
 Вы можете добавить элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документ Word в проекте на уровне документа во время разработки несколькими способами.

- Из **панели элементов** Visual Studio.

   Вы можете перетащить элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> из области **Панель элементов** в документ. Этот способ удобен, если вы уже используете **панель элементов** для добавления элементов управления Windows Forms в документ.

- Из приложения Word.

   Вы можете добавить элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документ так же, как и закладку. Преимущество этого способа заключается в том, что вы можете задать имя элемента управления во время его создания.

- Из окна **Источники данных** .

   Вы можете перетащить элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> из окна **Источники данных** . Это удобно, если нужно одновременно привязать элемент управления к данным. Можно добавить элемент управления ведущего приложения так же, как вы добавляете элемент управления Windows Form из окна **Источники данных** . Дополнительные сведения см. в разделе [Привязка данных и Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Добавление элемента управления Bookmark в документ из панели элементов

1. Откройте **панель элементов** и щелкните вкладку **Элементы управления Word** .

2. Перетащите элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документ.

     Отображается диалоговое окно **Добавление закладки** .

3. Выберите текст или другие элементы, которые необходимо включить в закладку.

4. Нажмите кнопку **ОК**.

     Если вы не хотите использовать имя закладки по умолчанию, измените его в окне **Свойства** .

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Добавление элемента управления Bookmark в документ из Word

1. В документе, который размещен в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , поместите курсор туда, куда необходимо добавить закладку, или выделите текст, который требуется добавить в закладку.

2. На вкладке **Вставка** ленты в группе **Ссылки** нажмите кнопку **Закладка** .

3. В диалоговом окне **Закладка** введите имя новой закладки и нажмите кнопку **Добавить**.

## <a name="add-bookmark-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Добавление элементов управления Bookmark во время выполнения в проекте уровня документа
 Элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> можно добавить в документ программным образом во время выполнения с помощью методов свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> класса `ThisDocument` в проекте. Существуют две перегрузки метода, которые можно использовать для добавления элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> следующими способами:

- добавление <xref:Microsoft.Office.Tools.Word.Bookmark> в указанный диапазон;

- добавление <xref:Microsoft.Office.Tools.Word.Bookmark> , основанного на собственной закладке, в документ (т. е. <xref:Microsoft.Office.Interop.Word.Bookmark>).

  При закрытии документа динамически созданные элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в нем не сохраняются. Однако собственный объект <xref:Microsoft.Office.Interop.Word.Bookmark> остается в документе. Можно повторно создать <xref:Microsoft.Office.Tools.Word.Bookmark> , основанный на собственной закладке, при очередном открытии документа. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Добавление элемента управления Bookmark в документ программными средствами

1. Вставьте следующий код в обработчике событий `ThisDocument_Startup` в проекте, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> в первый абзац документа.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet1":::

    > [!NOTE]
    > Если необходимо создать элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> на основе существующего <xref:Microsoft.Office.Interop.Word.Bookmark>, используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> и передайте его в существующий <xref:Microsoft.Office.Interop.Word.Bookmark>.

## <a name="add-bookmark-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Добавление элементов управления Bookmark во время выполнения в проекте надстройки VSTO
 Вы можете добавить элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> программным способом в любой открытый документ во время выполнения с помощью надстройки VSTO. Для этого следует создать ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> , основанный на открытом документе, а затем использовать методы свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> этого ведущего элемента. Существуют две перегрузки метода, которые можно использовать для добавления элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> следующими способами:

- добавление <xref:Microsoft.Office.Tools.Word.Bookmark> в указанный диапазон;

- добавление <xref:Microsoft.Office.Tools.Word.Bookmark> , основанного на собственной закладке, в документ (т. е. <xref:Microsoft.Office.Interop.Word.Bookmark>).

  При закрытии документа динамически созданные элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в нем не сохраняются. Однако собственный объект <xref:Microsoft.Office.Interop.Word.Bookmark> остается в документе. Можно повторно создать <xref:Microsoft.Office.Tools.Word.Bookmark> , основанный на собственной закладке, при очередном открытии документа. Дополнительные сведения см. [в разделе Сохранение динамических элементов управления в документах Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Дополнительные сведения о создании ведущих элементов в проектах надстроек VSTO см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Добавление элемента управления Bookmark в указанный диапазон

1. Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> и передайте ему объект <xref:Microsoft.Office.Interop.Word.Range> , в который вы хотите добавить <xref:Microsoft.Office.Tools.Word.Bookmark>.

     Следующий пример кода добавляет новый <xref:Microsoft.Office.Tools.Word.Bookmark> в начало активного документа. Чтобы использовать этот пример, запустите его из обработчика событий `ThisAddIn_Startup` в проекте надстройки VSTO Word.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet4":::

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Добавление элемента управления Bookmark, основанного на собственном элементе управления Bookmark

1. Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> и передайте ему существующий объект <xref:Microsoft.Office.Interop.Word.Bookmark> , который будет использоваться в качестве основы для нового <xref:Microsoft.Office.Tools.Word.Bookmark>.

     В следующем примере кода создается новый объект <xref:Microsoft.Office.Tools.Word.Bookmark> , основанный на первом объекте <xref:Microsoft.Office.Interop.Word.Bookmark> в активном документе. Чтобы использовать этот пример, запустите его из обработчика событий `ThisAddIn_Startup` в проекте надстройки VSTO Word.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet5":::

## <a name="see-also"></a>См. также статью
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)
- [Как изменить размер элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)
