---
title: Руководство. Добавление элементов управления Windows Forms в документы Office
description: Узнайте, как добавлять Windows Forms элементы управления в Microsoft Office Excel и Microsoft Office документы Word во время разработки в проектах уровня документа.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e5a196c54a513376edef5c837a429bece6dd7b16
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824839"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Добавление Windows Forms элементов управления в документы Office
  Вы можете добавить элементы управления Windows Forms в документы Microsoft Office Word и Microsoft Office Excel во время разработки в проектах уровня документа. Во время выполнения можно добавлять элементы управления в настройки уровня документа и в надстройки VSTO. Например, можно добавить <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> элемент управления на лист, чтобы пользователи могли выбирать из списка параметров.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 В этом разделе описываются следующие задачи.

- [Добавление элементов управления во время разработки](#designtime)

- [Добавление элементов управления во время выполнения в проектах уровня документа](#runtimedoclevel)

- [Добавление элементов управления во время выполнения в надстройках VSTO](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> Добавление элементов управления во время разработки
 Вы можете добавить элементы управления Windows Forms в документ в проекте на уровне документа во время разработки несколькими способами.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Перетаскивание элемента управления Windows Forms в документ

1. Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. На вкладке **Общие элементы управления** **области элементов** щелкните элемент управления, который требуется добавить, и перетащите его в документ.

    > [!NOTE]
    > При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Рисование элемента управления Windows Forms в документе

1. Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. На вкладке **Общие элементы управления** **области элементов** щелкните элемент управления, который требуется добавить.

3. Щелкните нужное место в документе, где будет находиться верхний левый угол элемента управления, и перетащите указатель к нужному правому нижнему углу элемента управления.

     Элемент управления добавляется в документ с указанным местоположением и размером.

    > [!NOTE]
    > При выборе элемента управления в Excel вы увидите **= Embed ("WinForms. Control. Host", "")**  в **строке формул**. Этот текст обязательный, его не следует удалять.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Добавление элемента управления Windows Forms в документ двойным щелчком элемента управления

1. Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. На вкладке **Общие элементы управления** **панели элементов** щелкните элемент управления, который требуется добавить.

3. Щелкните место, где требуется добавить элемент управления, в документе.

     Элемент управления добавляется в документ с размером по умолчанию.

    > [!NOTE]
    > При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Добавление элемента управления Windows Forms в документ двойным щелчком элемента управления

1. Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. На вкладке **Общие элементы управления** **панели элементов** дважды щелкните элемент управления, который требуется добавить.

     Элемент управления добавляется в центр документа или активной области документа.

    > [!NOTE]
    > При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Добавление элемента управления Windows Forms в документ путем нажатия клавиши ВВОД

1. Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. На вкладке **Общие элементы управления** **панели элементов** щелкните элемент управления, который требуется добавить, и нажмите клавишу **Ввод** .

     Элемент управления добавляется в центр документа или активной области документа.

    > [!NOTE]
    > При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> Добавление элементов управления во время выполнения в проектах уровня документа
 Вы можете программно добавить элементы управления Windows Forms в документ во время выполнения. В Word используйте методы свойства <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> класса `ThisDocument`. В Excel используйте методы <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> свойства `Sheet` класса *n* . У каждого метода есть несколько перегрузок, которые позволяют указать расположение элемента управления разными способами.

 При добавлении элемента управления Windows Forms в документ во время выполнения он не сохраняется в документе при закрытии документа. Элемент управления можно восстановить при следующем открытии документа. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Добавление элемента управления Windows Forms во время выполнения

1. Используйте метод с именем Add \<*control class*> ( *класс Control class* — это имя класса элемента управления Windows Forms, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

     В следующем примере кода показано, как добавить в <xref:Microsoft.Office.Tools.Excel.Controls.Button> ячейку **C5** `Sheet1` в проекте уровня документа для Excel.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet4":::

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a> Добавление элементов управления во время выполнения в надстройках VSTO
 Вы можете добавить элементы управления Windows Forms программным способом в любой открытый документ во время выполнения. Сначала создайте ведущий элемент, основанный на открытом документе или листе. Затем в Word используйте методы свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> нового ведущего элемента. В Excel используйте методы свойства <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> нового ведущего элемента. У каждого метода есть несколько перегрузок, которые позволяют указать расположение элемента управления разными способами.

 При добавлении элемента управления Windows Forms в документ во время выполнения он не сохраняется в документе при закрытии документа. Элемент управления можно восстановить при следующем открытии документа. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Дополнительные сведения о создании ведущих элементов в проектах надстроек VSTO см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Добавление элемента управления Windows Forms во время выполнения

1. Используйте метод с именем Add \<*control class*> ( *класс Control class* — это имя класса элемента управления Windows Forms, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

    > [!NOTE]
    > В проектах надстроек VSTO, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо добавить ссылку на *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* или *Microsoft.Office.Tools.Word.v4.0.Utilities.dllную* сборку, прежде чем можно будет получить доступ к \<*control class*> методам Add.

     В следующем примере кода показано, как добавить <xref:Microsoft.Office.Tools.Word.Controls.Button> в первый абзац активного документа с помощью надстройки VSTO для Word.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet7":::

## <a name="see-also"></a>См. также статью
- [Общие сведения об элементах управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Руководство. изменение размеров элементов управления в ячейках листа](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
