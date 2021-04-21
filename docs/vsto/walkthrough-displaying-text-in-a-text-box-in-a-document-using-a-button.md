---
title: Отображение текста в текстовом поле в документе с помощью кнопки
description: Узнайте, как можно использовать кнопки и текстовые поля в настройке уровня документа для Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 716d0ed0b203d55932fef4d6e3e22eabf1137ded
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824202"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Пошаговое руководство. Отображение текста в текстовом поле документа с помощью кнопки
  В этом пошаговом руководстве демонстрируется использование кнопок и текстовых полей в настройке уровня документа для Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- добавление элементов управления в документ Word в проекте на уровне документа во время разработки;

- заполнение текстового поля при нажатии кнопки.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание документа Word.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект документа Word с именем **Моя кнопка Word**. В мастере выберите **создать новый документ**.

     Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новый документ Word в конструкторе и добавит для **Обозреватель решений** проект **кнопки Word** .

## <a name="add-controls-to-the-word-document"></a>Добавление элементов управления в документ Word
 Элементы управления пользовательского интерфейса в документе Word состоят из кнопки и текстового поля.

### <a name="to-add-a-button-and-a-text-box"></a>Добавление кнопки и текстового поля

1. Убедитесь, что документ открыт в конструкторе Visual Studio.

2. Из вкладки **Общие элементы управления** **панели элементов** перетащите <xref:Microsoft.Office.Tools.Word.Controls.TextBox> элемент управления в документ.

   > [!NOTE]
   > В Word элементы управления по умолчанию сбрасываются в один уровень с текстом. Способ вставки элементов управления и объектов фигур можно изменить, изменив значение по умолчанию на вкладке **Правка** диалогового окна **Параметры** в Word.

3. В меню **Просмотр** выберите пункт **Окно свойств**.

4. Найдите поле **textBox1** в раскрывающемся списке окно **свойств** и измените свойство **Name** текстового поля на **DisplayText**.

5. Перетащите элемент управления **Button** в документ и измените следующие свойства.

   |Свойство|Значение|
   |--------------|-----------|
   |**Имя**|**insertText**|
   |**Text**|**Вставить текст**|

   Теперь можно написать код, который будет выполняться при нажатии кнопки.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Заполнение текстового поля при нажатии кнопки
 Каждый раз, когда пользователь нажимает кнопку, **Hello World!** добавляется в текстовое поле.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Запись в текстовое поле при нажатии кнопки

1. В **Обозреватель решений** щелкните правой кнопкой мыши **ThisDocument** и выберите в контекстном меню пункт **Просмотреть код** .

2. Добавьте следующий код в обработчик событий <xref:System.Windows.Forms.Control.Click> кнопки.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet7":::

3. В C# необходимо добавить обработчик события кнопки в событие <xref:Microsoft.Office.Tools.Word.Document.Startup>. Дополнительные сведения о создании обработчиков событий см. в разделе [как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet8":::

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать документ, чтобы убедиться, что сообщение **Hello World!** отображается в текстовом поле при нажатии кнопки.

### <a name="to-test-your-document"></a>Проверка документа

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Нажмите кнопку.

3. Убедитесь, что **Hello World!** отображается в текстовом поле.

## <a name="next-steps"></a>Дальнейшие действия
 В этом пошаговом руководстве описываются основные принципы использования кнопок и текстовых полей в документах Word. Ниже приводятся некоторые из возможных последующих задач.

- Использование поля со списком для изменения форматирования. Дополнительные сведения см. в разделе [Пошаговое руководство. изменение форматирования документа с помощью элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Использование переключателей для выбора стилей диаграмм. Дополнительные сведения см. в разделе [Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>См. также статью
- [Общие сведения об элементах управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Добавление Windows Forms элементов управления в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
