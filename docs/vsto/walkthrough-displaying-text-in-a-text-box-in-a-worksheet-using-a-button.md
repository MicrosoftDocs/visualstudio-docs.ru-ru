---
title: Отображение текста в текстовом поле на листе с помощью кнопки
description: Изучите основы использования кнопок и текстовых полей на листах Microsoft Excel. Также создавайте проекты Excel с помощью средств разработки Office в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1209bf903f5a5b9c0005d9ba4ba6a891752aedd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827790"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Пошаговое руководство. Отображение текста в текстовом поле листа с помощью кнопки
  В этом пошаговом руководстве показаны основные сведения об использовании кнопок и текстовых полей на Microsoft Office листах Excel и о создании проектов Excel с помощью средств разработки Office в Visual Studio. Чтобы увидеть результат как завершенный пример, см. Пример элементов управления Excel в разделе [примеры разработки Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие процедуры.

- Добавление элементов управления на лист.

- Заполнение текстового поля при нажатии кнопки.

- Протестируйте проект.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Создание проекта
 На этом шаге вы создадите проект книги Excel с помощью Visual Studio.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект книги Excel с именем **кнопка My Excel**. Убедитесь, что выбрано **Создание нового документа** . Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новую книгу Excel в конструкторе и добавит проект **кнопки "мой Excel"** в **Обозреватель решений**.

## <a name="add-controls-to-the-worksheet"></a>Добавление элементов управления на лист
 Для этого пошагового руководства на первом листе потребуется кнопка и текстовое поле.

### <a name="to-add-a-button-and-a-text-box"></a>Добавление кнопки и текстового поля

1. Убедитесь, что книга **My Excel Button.xlsx** открыта в конструкторе Visual Studio и `Sheet1` отображается.

2. С вкладки **Общие элементы управления** панели элементов перетащите элемент a <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> в `Sheet1` .

3. В меню **вид** выберите пункт **окно свойств**.

4. Убедитесь, что **textBox1** отображается в раскрывающемся списке окно **свойств** , и измените свойство **Name** текстового поля на **DisplayText**.

5. Перетащите элемент управления **Button** на страницу `Sheet1` и измените следующие свойства:

   |Свойство|Значение|
   |--------------|-----------|
   |**Имя**|**insertText**|
   |**Text**|**Вставить текст**|

   Теперь напишите код, который будет выполняться при нажатии кнопки.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Заполнение текстового поля при нажатии кнопки
 Каждый раз, когда пользователь нажимает кнопку, **Hello World!** добавляется к текстовому полю.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Запись в текстовое поле при нажатии кнопки

1. В **Обозреватель решений** щелкните правой кнопкой мыши **Лист1** и выберите в контекстном меню пункт **Просмотреть код** .

2. Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий кнопки:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet11":::

3. В C# необходимо добавить обработчик событий в <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> событие, как показано ниже. Сведения о создании обработчиков событий см. в разделе [инструкции. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet12":::

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать книгу, чтобы убедиться, что сообщение **Hello World!** отображается в текстовом поле при нажатии кнопки.

### <a name="to-test-your-workbook"></a>Проверка книги

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Нажмите кнопку.

3. Убедитесь, что **Hello World!** отображается в текстовом поле.

## <a name="next-steps"></a>Дальнейшие действия
 В этом пошаговом руководстве показаны основные принципы использования кнопок и текстовых полей на листах Excel. Ниже приводятся некоторые из возможных последующих задач.

- Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).

- Использование флажков для изменения форматирования. Дополнительные сведения см. в разделе [Пошаговое руководство. изменение форматирования листа с помощью элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>См. также статью
- [Добавление Windows Forms элементов управления в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)
- [Ограничения элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
