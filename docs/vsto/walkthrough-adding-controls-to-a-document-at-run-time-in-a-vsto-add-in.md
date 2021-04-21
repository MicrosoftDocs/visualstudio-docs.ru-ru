---
title: Добавление элементов управления в документ во время выполнения в надстройке VSTO
description: Узнайте, как использовать ленту, чтобы разрешить пользователям добавлять в документ класс Button или интерфейс RichTextContentControl.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c2088a4d2ca81418ca16b51b53b0af38595d75b2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825398"
---
# <a name="walkthrough-add-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>Пошаговое руководство. Добавление элементов управления в документ во время выполнения в надстройке VSTO
  Вы можете добавлять элементы управления в любой документ Word, Открытый Microsoft Office, с помощью надстройки VSTO. В этом пошаговом руководстве показано, как использовать ленту, чтобы разрешить пользователям добавлять в <xref:Microsoft.Office.Tools.Word.Controls.Button> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> документ или.

 **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для Word 2010. Для получения дополнительной информации см. [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

 В этом пошаговом руководстве описаны следующие задачи:

- Создание нового проекта надстройки VSTO для Word.

- Предоставление пользовательского интерфейса для добавления элементов управления в документ.

- Добавление элементов управления в документ во время выполнения.

- Удаление элементов управления из документа.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-word-add-in-project"></a>Создание нового проекта надстройки Word
 Начнем с создания проекта надстройки VSTO для Word

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Создание нового проекта надстройки VSTO для Word

1. Создайте проект надстройки VSTO для Word с именем **ворддинамикконтролс**. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Добавьте ссылку на сборку **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** . Эта ссылка потребуется для программного добавления элемента управления Windows Forms в документ далее в этом пошаговом руководстве.

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Предоставление пользовательского интерфейса для добавления элементов управления в документ
 Добавьте настраиваемую вкладку на ленту Word. Пользователи могут устанавливать флажки на вкладке, чтобы добавлять элементы управления в документ.

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Предоставление пользовательского интерфейса для добавления элементов управления в документ

1. В меню **Проект** выберите **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите элемент **Лента (визуальный конструктор)**.

3. Измените имя новой ленты на **MyRibbon** и нажмите кнопку **Добавить**.

    В конструкторе лент откроется файл **MyRibbon.cs** или **MyRibbon.vb** ; отобразятся вкладка и группа, используемые по умолчанию.

4. В конструкторе ленты щелкните группу **group1** .

5. В окне **Свойства** измените свойство **Метка** для **group1** на **Добавить элементы управления**.

6. Перетащите элемент управления **CheckBox** с вкладки **Элементы управления ленты Office****панели элементов** в группу **group1**.

7. Щелкните **CheckBox1** , чтобы выбрать его.

8. В окне **Свойства** измените следующие свойства.

   | Свойство | Значение |
   |-----------|-----------------------|
   | **Имя** | **addButtonCheckBox** |
   | **Label** | **Кнопка "Добавить"** |

9. Добавьте второй флажок в **group1**, а затем измените следующие свойства.

   | Свойство | Значение |
   |-----------|---------------------------|
   | **Имя** | **addRichTextCheckBox** |
   | **Label** | **Добавление элемента управления форматированием текста** |

10. В конструкторе лент дважды щелкните элемент **Добавить кнопку**.

     Обработчик событий <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> флажка **Добавить кнопку** откроется в редакторе кода.

11. Вернитесь в конструктор ленты и дважды щелкните элемент **Добавить элемент управления форматированием текста**.

     Обработчик событий <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> флажка **Добавить элемент управления форматированием текста** откроется в редакторе кода.

    Далее в этом пошаговом руководстве вы добавите код в эти обработчики событий для добавления и удаления элементов управления в активном документе.

## <a name="add-and-remove-controls-on-the-active-document"></a>Добавление и удаление элементов управления в активном документе
 В коде надстройки VSTO необходимо преобразовать активный документ в <xref:Microsoft.Office.Tools.Word.Document>*T:Microsoft.Office.Tools.Word.Document* , прежде чем можно будет добавить элемент управления. В решениях Office управляемые элементы управления можно добавлять только в ведущие элементы, которые действуют как контейнеры для элементов управления. В проектах надстроек VSTO ведущие элементы можно создавать во время выполнения с помощью `GetVstoObject` метода.

 Добавьте в класс `ThisAddIn` методы, которые могут вызываться для добавления или удаления <xref:Microsoft.Office.Tools.Word.Controls.Button> или <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в активном документе. Далее в этом пошаговом руководстве вы будете вызывать эти методы из обработчиков событий <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> флажков на ленте.

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Добавление и удаление элементов управления в активном документе

1. В **Обозреватель решений** дважды щелкните *ThisAddIn. CS* или *ThisAddIn. vb* , чтобы открыть файл в редакторе кода.

2. Добавьте в класс `ThisAddIn` приведенный далее код. Этот код объявляет объекты <xref:Microsoft.Office.Tools.Word.Controls.Button> и <xref:Microsoft.Office.Tools.Word.RichTextContentControl> , представляющие элементы управления, которые будут добавлены в документ.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet1":::

3. Добавьте следующий метод в класс `ThisAddIn`. Когда пользователь щелкает флажок **Добавить кнопку** на ленте, этот метод добавляет <xref:Microsoft.Office.Tools.Word.Controls.Button> в выделенный фрагмент документа, если флажок устанавливается, или удаляет <xref:Microsoft.Office.Tools.Word.Controls.Button> , если флажок снимается.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet2":::

4. Добавьте следующий метод в класс `ThisAddIn`. Когда пользователь щелкает флажок **Добавить элемент управления форматированием текста** на ленте, этот метод добавляет <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в выделенный фрагмент документа, если флажок устанавливается, или удаляет <xref:Microsoft.Office.Tools.Word.RichTextContentControl> , если флажок снимается.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet3":::

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Удалить элемент управления "Кнопка" при сохранении документа
 Элементы управления Windows Forms не сохраняются, когда документ сохраняется, а затем закрывается. Однако оболочка ActiveX для каждого элемента управления остается в документе, и границу этой оболочки конечные пользователи могут видеть при повторном открытии документа. Существует несколько способов очистки динамически создаваемых Windows Forms элементов управления в надстройках VSTO. В этом пошаговом руководстве вы программно удаляете <xref:Microsoft.Office.Tools.Word.Controls.Button> элемент управления при сохранении документа.

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Удаление элемента управления "Кнопка" при сохранении документа

1. В файле кода *ThisAddIn. CS* или *ThisAddIn. vb* добавьте в класс следующий метод `ThisAddIn` . Этот метод является обработчиком событий для события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . Если у сохраненного документа есть связанный с ним ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> , обработчик событий получает этот ведущий элемент и удаляет элемент управления <xref:Microsoft.Office.Tools.Word.Controls.Button> , если он существует.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet4":::

2. В C# добавьте в обработчик событий `ThisAddIn_Startup` следующий код. Этот код требуется в C# для подключения обработчика событий `Application_DocumentBeforeSave` к событию <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet5":::

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Добавлять и удалять элементы управления, когда пользователь щелкает флажки на ленте
 Наконец, измените <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> обработчики событий флажков, добавленных на ленту для добавления или удаления элементов управления в документе.

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Добавление или удаление элементов управления при нажатии пользователем флажков на ленте

1. В файле кода *MyRibbon. CS* или *MyRibbon. vb* Замените созданные `addButtonCheckBox_Click` `addRichTextCheckBox_Click` обработчики событий и следующим кодом. Этот код переопределяет данные обработчики событий, задавая вызов методов `ToggleButtonOnDocument` и `ToggleRichTextControlOnDocument` , которые вы добавили в класс `ThisAddIn` ранее в этом пошаговом руководстве.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs" id="Snippet6":::

## <a name="test-the-solution"></a>Тестирование решения
 Добавьте элементы управления в документ, выбрав их в настраиваемой вкладке на ленте. При сохранении документа элемент управления <xref:Microsoft.Office.Tools.Word.Controls.Button> удаляется.

### <a name="to-test-the-solution"></a>Тестирование решения

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. В активном документе нажмите клавишу **Ввод** несколько раз, чтобы добавить в документ новые пустые абзацы.

3. Выделите первый абзац.

4. Перейдите на вкладку **Надстройки** .

5. В группе **Добавить элементы управления** щелкните **Добавить кнопку**.

     В первом абзаце появляется кнопка.

6. Выделите последний абзац.

7. В группе **Добавить элементы управления** щелкните **Добавить элемент управления форматированием текста**.

     В последний абзац добавляется элемент управления форматированием текста.

8. Сохраните документ.

     Кнопка удаляется из документа.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения об элементах управления в надстройках VSTO см. в следующих статьях.

- Пример, демонстрирующий Добавление многих других типов элементов управления в документ во время выполнения и повторное создание элементов управления при повторном открытии документа, см. в образце Word Add-In Dynamic Controls в примерах [разработки Office и пошаговых руководствах](../vsto/office-development-samples-and-walkthroughs.md).

- Пошаговое руководство, в котором показано, как добавлять элементы управления на лист с помощью надстройки VSTO для Excel, см. [в разделе Пошаговое руководство. Добавление элементов управления в лист во время выполнения в проекте надстройки VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).

## <a name="see-also"></a>См. также статью
- [Решения Word](../vsto/word-solutions.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Сохранение динамических элементов управления в документах Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Добавление Windows Forms элементов управления в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Как добавить элементы управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
