---
title: Пошаговое руководство. получение данных с помощью формы Windows
description: Откройте форму Windows Forms из настроек уровня документа для Microsoft Excel, собирайте сведения от пользователя и запишите их в ячейку листа.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 62a49919522c5d4a88b6f4b6876b567c8d275dec
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826425"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>Пошаговое руководство. получение данных с помощью формы Windows
  В этом пошаговом руководстве показано, как открывается форма Windows Forms из настройки уровня документа для Microsoft Office Excel, выполняется сбор сведений от пользователя и запись этих сведений в ячейку листа.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Хотя в этом пошаговом руководстве используется проект уровня документа для Excel, рассмотренная процедура также применима и к другим проектам Office.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Создание нового проекта
 Первым шагом является создание проекта книги Excel.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект книги Excel с именем **WinFormInput** и выберите в мастере **Создать новый документ** . Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio открывает новую книгу Excel в конструкторе и добавляет проект **WinFormInput** в **обозреватель решений**.

## <a name="add-a-namedrange-control-to-the-worksheet"></a>Добавление элемента управления NamedRange на лист

### <a name="to-add-a-named-range-to-sheet1"></a>Добавление именованного диапазона в Sheet1

1. Выберите ячейку **A1** в `Sheet1`.

2. В поле **Имя** введите **formInput**.

     Поле **Имя** находится слева от строки формул над столбцом **A** листа.

3. Нажмите клавишу **ВВОД**.

     Элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> добавляется в ячейку **A1**. Видимые изменения на листе отсутствуют, но значение **formInput** появляется в поле **Имя** (над листом слева) и в окне **Свойства** при выборе ячейки **A1** .

## <a name="add-a-windows-form-to-the-project"></a>Добавление формы Windows Forms в проект
 Создайте форму Windows Form, чтобы запрашивать сведения у пользователя.

### <a name="to-add-a-windows-form"></a>Добавление формы Windows Forms

1. Выберите проект **WinFormInput** в **обозревателе решений**.

2. В меню **Проект** выберите пункт **Добавить форму Windows**.

3. Дайте этой форме имя **GetInputString.vb** или **GetInputString.cs**, а затем нажмите кнопку **Добавить**.

    Новая форма откроется в конструкторе.

4. Добавьте в форму <xref:System.Windows.Forms.TextBox> и <xref:System.Windows.Forms.Button> .

5. Выберите кнопку, найдите свойство **Текст** в окне **Свойства** и измените текст на **ОК**.

   Затем добавьте в `ThisWorkbook.vb` или `ThisWorkbook.cs` код для сбора информации от пользователя.

## <a name="display-the-windows-form-and-collecting-information"></a>Отображение Windows Form и сбор сведений
 Создайте экземпляр формы Windows `GetInputString` и отобразите его, а затем запишите информацию от пользователя в ячейку листа.

#### <a name="to-display-the-form-and-collect-information"></a>Отображение формы и сбор информации

1. Щелкните правой кнопкой мыши файл **ThisWorkbook.vb** или **ThisWorkbook.cs** в **обозревателе решений**, а затем нажмите кнопку **Просмотр кода**.

2. В обработчике событий <xref:Microsoft.Office.Tools.Excel.Workbook.Open>`ThisWorkbook`добавьте следующий код для объявления переменной формы `GetInputString` , а затем отобразите эту форму.

   > [!NOTE]
   > В C# необходимо добавить обработчик событий, как показано в событии <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> ниже. Дополнительные сведения о создании обработчиков событий см. в разделе [как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

    :::code language="csharp" source="../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb" id="Snippet1":::

3. Создайте метод с именем `WriteStringToCell` , который записывает текст в именованный диапазон. Этот метод вызывается из формы, и ввод пользователя передается в элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> , `formInput`, в ячейку **A1**.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb" id="Snippet2":::

   Далее добавьте в форму код для обработки события нажатия кнопки.

## <a name="send-information-to-the-worksheet"></a>Отправка сведений на лист

### <a name="to-send-information-to-the-worksheet"></a>Отправка информации в лист

1. Щелкните правой кнопкой мыши В **GetInputString** в **обозревателе решений** и выберите **Конструктор представлений**.

2. Дважды щелкните кнопку, чтобы открыть файл кода с добавленным обработчиком событий <xref:System.Windows.Forms.Control.Click> кнопки.

3. Добавьте код в обработчик событий для приема входных данных из текстового поля, передачи их в функцию `WriteStringToCell`, а затем закрытия формы.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb" id="Snippet3":::

## <a name="test"></a>Проверка
 Теперь можно запустить проект. Появляется форма Windows Forms, и введенные данные отображаются в листе.

### <a name="to-test-your-workbook"></a>Проверка книги

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Убедитесь, что форма Windows Forms появилась.

3. Введите **Hello World** в текстовом поле и нажмите кнопку **ОК**.

4. Убедитесь, что сообщение **Hello World** появилось в ячейке **A1** листа.

## <a name="next-steps"></a>Дальнейшие действия
 В этом пошаговом руководстве описываются основные принципы отображения формы Windows Forms и передачи данных в лист. Вам может потребоваться выполнить другие задачи, приведенные ниже.

- Использование элементов управления Windows Forms в книге Excel или документе Word. Дополнительные сведения см. [в разделе Windows Forms элементы управления в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Изменение пользовательского интерфейса Microsoft Office приложения из настройки на уровне документа или надстройки VSTO. Дополнительные сведения см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>См. также статью
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)
- [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)
- [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)
