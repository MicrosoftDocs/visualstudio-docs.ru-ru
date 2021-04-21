---
title: Руководство. Управление макетом элементов управления на панелях действий
description: Узнайте, как управлять разметкой элементов управления на панелях действий путем написания кода для правильной работы элементов управления пользователя.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 182dee248f161f3dde721c50ee996d6f621dd9af
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827453"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Руководство. Управление макетом элементов управления на панелях действий
  По умолчанию панель действий закреплена справа от документа или листа; Однако его можно прикрепить к левому, верхнему или нижнему краю. Если вы используете несколько пользовательских элементов управления, можно написать код для правильного размещения пользовательских элементов управления на панели действия. Дополнительные сведения см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Порядок расположения элементов управления зависит от того, закреплена ли панель действий по вертикали или по горизонтали.

> [!NOTE]
> Если пользователь изменяет размеры панели действий во время выполнения, можно настроить элементы управления для изменения размера с помощью панели действий. Вы можете использовать свойство <xref:System.Windows.Forms.Control.Anchor%2A> элемента управления Windows Forms, чтобы закрепить элементы управления на панели действий. Дополнительные сведения см. в разделе [руководство. Привязка элементов управления к Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Задание порядка расположения элементов управления панели действий

1. Откройте проект уровня документа для Microsoft Office слово, которое содержит панель действий с несколькими пользовательскими элементами управления или вложенными элементами управления панели действий. Дополнительные сведения см. в разделе [руководство. Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

2. Щелкните правой кнопкой мыши **ThisDocument. CS** или **ThisDocument. vb** в **Обозреватель решений** и выберите пункт **Просмотреть код**.

3. В <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> обработчике событий панели действия проверьте, является ли ориентация панели действий горизонтальной.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet30":::

4. Если ориентация горизонтальна, выровнять элементы управления панели действий слева. в противном случае поверх остальных столбцов.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet31":::

5. В C# необходимо добавить обработчик событий для `ActionsPane` <xref:Microsoft.Office.Tools.Word.Document.Startup> обработчика событий. Дополнительные сведения о создании обработчиков событий см. в разделе [как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet32":::

6. Запустите проект и убедитесь, что элементы управления панели действий расположены слева направо, если панель действий закреплена в верхней части документа, а элементы управления расположены сверху вниз, когда панель действий закреплена в правой части документа.

## <a name="example"></a>Пример
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet29":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet29":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Проект уровня документа Word с панелью действий, которая содержит несколько пользовательских элементов управления или вложенные элементы управления панели действий.

## <a name="see-also"></a>См. также статью
- [Обзор панели действий](../vsto/actions-pane-overview.md)
- [Как добавить панель действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Как добавить панель действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
