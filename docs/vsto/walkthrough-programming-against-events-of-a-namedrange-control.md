---
title: Пошаговое руководство. Программирование событий элемента управления NamedRange
description: Узнайте, как можно добавить элемент управления NamedRange в лист Microsoft Excel и программировать его события с помощью средств разработки Office в Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec1c670867fae277a3c3c8290cd34d0d4be7ddf3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824969"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Пошаговое руководство. Программирование событий элемента управления NamedRange
  В этом пошаговом руководстве показано, как добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления в Microsoft Office лист Excel и программировать его события с помощью средств разработки Office в Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие процедуры.

- Добавление <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления на лист.

- Программа по отношению к <xref:Microsoft.Office.Tools.Excel.NamedRange> событиям управления.

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

1. Создайте проект книги Excel с именем **Мои события именованного диапазона**. Убедитесь, что выбрано **Создание нового документа** . Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новую книгу Excel в конструкторе и добавит проект " **Мои события именованного диапазона** " в **Обозреватель решений**.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Добавление в лист текста и именованных диапазонов
 Так как элементы управления ведущего приложения являются расширенными объектами Office, их можно добавить в документ так же, как при добавлении собственного объекта. Например, можно добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления Excel на лист, открыв меню **Вставка** , указав **имя** и выбрав команду **определить**. Можно также добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления, перетащив его с **панели элементов** на лист.

 На этом шаге вы добавите на лист два элемента управления именованным диапазоном с помощью **панели элементов**, а затем добавите текст на лист.

### <a name="to-add-a-range-to-your-worksheet"></a>Добавление диапазона на лист

1. Убедитесь, что в конструкторе Visual Studio открыта книга " *Мой именованный диапазон Events.xlsx* " с `Sheet1` отображением.

2. С вкладки **элементы управления Excel** панели элементов перетащите <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления в ячейку **a1** в `Sheet1` .

     Откроется диалоговое окно **Добавление элемента управления NamedRange** .

3. Убедитесь, что в редактируемом текстовом поле отображается **$A $1** и выбрана ячейка **a1** . Если это не так, щелкните ячейку **a1** , чтобы выбрать ее.

4. Нажмите кнопку **ОК**.

     Ячейка **a1** преобразуется в диапазон с именем `namedRange1` . На листе нет видимых индикаторов, но оно `namedRange1` отображается в поле **имя** (расположено прямо над листом слева), если выбрана ячейка **a1** .

5. Добавьте еще один <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления в ячейку **B3**.

6. Убедитесь, что в редактируемом текстовом поле отображается **$B $3** и выбрана ячейка **B3** . Если это не так, щелкните ячейку **B3** , чтобы выбрать ее.

7. Нажмите кнопку **ОК**.

     Ячейка **B3** преобразуется в диапазон с именем `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Добавление текста на лист

1. В ячейке **a1** введите следующий текст:

    **Это пример элемента управления NamedRange.**

2. В ячейке **a3** (слева от `namedRange2` ) введите следующий текст:

    **Событиях**

   В следующих разделах будет написан код, который вставляет текст в `namedRange2` и изменяет свойства `namedRange2` элемента управления в ответ на <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> события, и <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Добавление кода для реагирования на событие Бефоредаублекликк

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Вставка текста в NamedRange2 на основе события Бефоредаублекликк

1. В **Обозреватель решений** щелкните правой кнопкой мыши **Лист1. vb** или **Sheet1. CS** и выберите **Просмотреть код**.

2. Добавьте код, чтобы `namedRange1_BeforeDoubleClick` обработчик событий выглядел следующим образом:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet24":::

3. В C# необходимо добавить обработчики событий для именованного диапазона, как показано в приведенном <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> ниже событии. Сведения о создании обработчиков событий см. в разделе [инструкции. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet25":::

## <a name="add-code-to-respond-to-the-change-event"></a>Добавление кода для реагирования на событие изменения

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Вставка текста в namedRange2 на основе события Change

1. Добавьте код, чтобы `NamedRange1_Change` обработчик событий выглядел следующим образом:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet26":::

    > [!NOTE]
    > Поскольку двойной щелчок по ячейке в диапазоне Excel переходит в режим правки, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> событие возникает при перемещении выделения за пределы диапазона, даже если текст не изменяется.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Добавление кода для реагирования на Событие SelectionChange

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Вставка текста в namedRange2 на основе события SelectionChange

1. Добавьте код, чтобы обработчик событий **NamedRange1_SelectionChange** выглядел следующим образом:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet27":::

    > [!NOTE]
    > Поскольку двойной щелчок по ячейке в диапазоне Excel приводит к перемещению выделения в диапазон, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> событие возникает до <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> возникновения события.

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать книгу, чтобы убедиться, что текст, описывающий события <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления, вставляется в другой именованный диапазон при возникновении событий.

### <a name="to-test-your-document"></a>Проверка документа

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Поместите курсор в `namedRange1` и убедитесь, что текст, относящийся к <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> событию, вставлен и комментарий вставлен в лист.

3. Дважды щелкните внутри `namedRange1` и убедитесь, что текст, относящийся <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> к событиям, вставлен с помощью красного курсивного текста в `namedRange2` .

4. Щелкните за пределами `namedRange1` и обратите внимание, что событие Change возникает при выходе из режима редактирования, даже если в тексте не было внесено никаких изменений.

5. Измените текст в `namedRange1` .

6. Щелкните вне `namedRange1` и убедитесь, что текст, относящийся к <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> событию, вставлен синим текстом в `namedRange2` .

## <a name="next-steps"></a>Дальнейшие действия
 В этом пошаговом руководстве показаны основы программирования для событий <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления. Ниже приведена задача, которая может быть следующей:

- Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>См. также статью
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Как изменить размер элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Как добавить элементы управления NamedRange в листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
