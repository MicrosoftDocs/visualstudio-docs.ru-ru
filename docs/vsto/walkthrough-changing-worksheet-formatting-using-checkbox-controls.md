---
title: Изменение форматирования листа с помощью элементов управления CheckBox
description: Узнайте, как можно использовать средства разработки Office в Visual Studio для создания и добавления кода в проект.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6f649fad99b8d94cc650ecda57e10b423b14194e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826438"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Пошаговое руководство. изменение форматирования листа с помощью элементов управления CheckBox
  В этом пошаговом руководстве показаны основные принципы использования флажков на листе Excel Microsoft Office для изменения форматирования. Вы будете использовать средства разработки Office в Visual Studio для создания и добавления кода в проект. Чтобы увидеть результат как завершенный пример, см. Пример элементов управления Excel в разделе [примеры разработки Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие процедуры.

- Добавление текста и элементов управления на лист.

- Форматирование текста при выборе параметра.

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

1. Создайте проект книги Excel с именем **мое форматирование Excel**. Убедитесь, что выбрано **Создание нового документа** . Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новую книгу Excel в конструкторе и добавит проект **форматирования Excel** в **Обозреватель решений**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Добавление текста и элементов управления на лист
 В этом пошаговом руководстве вам понадобятся три элемента <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> управления и некоторый текст в <xref:Microsoft.Office.Tools.Excel.NamedRange> элементе управления.

### <a name="to-add-three-check-boxes"></a>Добавление трех флажков

1. Убедитесь, что книга открыта в конструкторе Visual Studio и `Sheet1` открыта.

2. С вкладки **Общие элементы управления** **панели элементов** перетащите <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> элемент управления в ячейку **B2** в **Лист1** или рядом с ней.

3. В меню **вид** выберите пункт окно **свойств** .

4. Убедитесь, что **CheckBox1** отображается в списке имя объекта в окне **свойств** , и измените следующие свойства:

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**апплиболдфонт**|
    |**Text**|**Полужирный**|

5. Перетащите второй флажок в ячейку **B4** или рядом с ней и измените следующие свойства:

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**апплиталикфонт**|
    |**Text**|**Наклонный**|

6. Перетащите третий флажок в ячейку **B6** или рядом с ней и измените следующие свойства:

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**апплюндерлинефонт**|
    |**Text**|**Начертан**|

7. Установите все три элемента управления флажками, удерживая нажатой клавишу **CTRL** .

8. В группе упорядочение на вкладке Формат в Excel нажмите кнопку **Выровнять**, а затем выберите **Выровнять по левому краю**.

     Три элемента управления флажками вычисляются слева, в позиции первого выбранного элемента управления.

     Затем перетащите <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления на лист.

    > [!NOTE]
    > Можно также добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления, введя **текстфонт** в поле **имя** .

#### <a name="to-add-text-to-a-namedrange-control"></a>Добавление текста в элемент управления NamedRange

1. С вкладки **элементы управления Excel** панели элементов перетащите <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления в ячейку **B9**.

2. Убедитесь, что в редактируемом текстовом поле отображается **$B $9** и выбрана ячейка **B9** . Если это не так, щелкните ячейку **B9** , чтобы выбрать ее.

3. Нажмите кнопку **ОК**.

4. Ячейка **B9** преобразуется в диапазон с именем `NamedRange1` .

    На листе нет видимых индикаторов, но оно `NamedRange1` отображается в **поле имя** (прямо над листом слева), когда выбрана ячейка **B9** .

5. Убедитесь, что в списке имя объекта окна **свойств** отображается расширение **NamedRange1** , и измените следующие свойства.

   |Свойство|Значение|
   |--------------|-----------|
   |**Имя**|**текстфонт**|
   |**Value2**|**Установите флажок, чтобы изменить форматирование этого текста.**|

   Затем напишите код для форматирования текста при выборе параметра.

## <a name="format-the-text-when-an-option-is-selected"></a>Форматирование текста при выборе параметра
 В этом разделе вы напишете код, чтобы при выборе пользователем параметра форматирования формат текста на листе изменился.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Изменение форматирования при выборе флажка

1. Щелкните правой кнопкой мыши элемент **Sheet1** и выберите пункт **Просмотреть код** в контекстном меню.

2. Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyBoldFont` флажка:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet7":::

3. Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyItalicFont` флажка:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet8":::

4. Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyUnderlineFont` флажка:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet9":::

5. В C# необходимо добавить обработчики событий для флажков к <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> событию, как показано ниже. Сведения о создании обработчиков событий см. в разделе [инструкции. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать книгу, чтобы убедиться в том, что текст отформатирован правильно, если установить или снять флажок.

### <a name="to-test-your-workbook"></a>Проверка книги

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Установка или снятие флажка.

3. Убедитесь, что текст отформатирован правильно.

## <a name="next-steps"></a>Дальнейшие действия
 В этом пошаговом руководстве показаны основные принципы использования флажков и форматирования текста на листах Excel. Ниже приводятся некоторые из возможных последующих задач.

- Развертывание проекта. Дополнительные сведения см. в статье [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Использование кнопки для заполнения текстового поля. Дополнительные сведения см. [в разделе Пошаговое руководство. Отображение текста в текстовом поле листа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>См. также статью
- [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Ограничения элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
