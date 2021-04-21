---
title: Изменение форматирования документа с помощью элементов управления CheckBox
description: Узнайте, как использовать элементы управления Windows Forms в настройке уровня документа для Microsoft Word, чтобы изменить форматирование текста.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3f6fbb91c37fd8956860eed8e4d39f8b0a8c1a0e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824423"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Пошаговое руководство. изменение форматирования документа с помощью элементов управления CheckBox
  В этом пошаговом руководстве демонстрируется использование элементов управления Windows Forms в настройке уровня документа для Microsoft Office Word для изменения форматирования текста.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- Добавление текста и элемента управления в документ в проекте уровня документа во время разработки.

- Форматирование текста при выборе параметра.

  Чтобы увидеть результат как завершенный пример, см. Примеры элементов управления Word в примерах [разработки Office и пошаговых руководствах](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание документа Word.

### <a name="create-a-new-project"></a>Создание нового проекта

1. Создайте проект документа Word с именем **Форматирование My Word**. В мастере выберите **создать новый документ**.

     Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новый документ Word в конструкторе и добавит проект **форматирования Word** в **Обозреватель решений**.

## <a name="add-text-and-controls-to-the-word-document"></a>Добавление текста и элементов управления в документ Word
 Для этого пошагового руководства добавьте в документ Word три флажка и некоторый текст в <xref:Microsoft.Office.Tools.Word.Bookmark> элементе управления. Флажки будут представлять пользователю параметры форматирования текста.

### <a name="add-three-check-boxes"></a>Добавить три флажка

1. Убедитесь, что документ открыт в конструкторе Visual Studio.

2. Из вкладки **Общие элементы управления** **панели элементов** перетащите первый <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> элемент управления в документ.

3. В окне **Свойства** измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**апплиболдфонт**|
    |**Text**|**Полужирный**|

4. Нажмите клавишу **Ввод** , чтобы переместить точку вставки под первый флажок.

5. Добавьте еще один флажок в документ под `ApplyBoldFont` флажком и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**апплиталикфонт**|
    |**Text**|**Наклонный**|

6. Нажмите клавишу **Ввод** , чтобы переместить точку вставки под вторым флажком.

7. Добавьте третий флажок в документ под `ApplyItalicFont` флажком и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**апплюндерлинефонт**|
    |**Text**|**Начертан**|

### <a name="add-text-and-a-bookmark-control"></a>Добавление текста и элемента управления Bookmark

1. Переместите точку вставки под элементами управления "флажок" и введите следующий текст:

    **Установите флажок, чтобы изменить форматирование этого текста.**

2. Перетащите элемент управления из вкладки **элементы управления Word** **панели элементов** в <xref:Microsoft.Office.Tools.Word.Bookmark> документ.

    Откроется диалоговое окно **Добавление элемента управления Bookmark** .

3. Выберите текст, добавленный в документ, и нажмите кнопку **ОК**.

    <xref:Microsoft.Office.Tools.Word.Bookmark>Элемент управления с именем **Bookmark1** добавляется к выделенному тексту в документе.

4. В окне **Свойства** измените значение свойства **(Name)** на **фонттекст.**

   Затем напишите код для форматирования текста при установленном или снятом флажке.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Форматирование текста при установке или снятии флажка
 Когда пользователь выбирает параметр форматирования, измените формат текста в документе.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Изменить форматирование, если установлен флажок

1. Щелкните правой кнопкой `ThisDocument` мыши **Обозреватель решений**, а затем в контекстном меню выберите пункт **Просмотреть код** .

2. Только для C# добавьте следующие константы в класс **ThisDocument** .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet2":::

3. Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyBoldFont` флажка.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet3":::

4. Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyItalicFont` флажка.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet4":::

5. Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyUnderlineFont` флажка.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet5":::

6. В C# необходимо добавить обработчики событий для текстовых полей в <xref:Microsoft.Office.Tools.Word.Document.Startup> событие. Дополнительные сведения о создании обработчиков событий см. в разделе [как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать документ, чтобы убедиться, что текст отформатирован правильно при установке или снятии флажка.

### <a name="test-your-document"></a>Тестирование документа

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Установка или снятие флажка.

3. Убедитесь, что текст отформатирован правильно.

## <a name="next-steps"></a>Дальнейшие действия
 В этом пошаговом руководстве показаны основные принципы использования флажков и программного изменения форматирования текста в документах Word. Ниже приводятся некоторые из возможных последующих задач.

- Используйте кнопку для заполнения текстового поля. Дополнительные сведения см. [в разделе Пошаговое руководство. Отображение текста в текстовом поле документа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Использование переключателей для выбора стилей диаграмм. Дополнительные сведения см. в разделе [Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>См. также статью
- [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Ограничения элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
