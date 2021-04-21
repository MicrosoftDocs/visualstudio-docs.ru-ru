---
title: Обзор панели действий
description: Сведения об настраиваемой области задач "действия документа", прикрепленной к конкретному Microsoft Office документу Word или книге Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 61e7ab9f00db6036d3bc8e41b9a2f19cf51f5511
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828154"
---
# <a name="actions-pane-overview"></a>Обзор панели действий
  Панель действий — это настраиваемая область задач « **действия с документом** », прикрепленная к конкретному Microsoft Office документу Word или Microsoft Office книге Excel. Панель действий размещается внутри области задач Office вместе с другими встроенными областями задач, такими как область задач **Источник XML** в Excel или область задач **стили и форматирование** в Word. Для разработки пользовательского интерфейса панели действий можно использовать элементы управления Windows Forms или элементы управления WPF.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Панель действий можно создать только в настройке на уровне документа Word или Excel. Невозможно создать панель действий в надстройке VSTO. Дополнительные сведения см. в разделе [доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Панель действий отличается от настраиваемых областей задач. Настраиваемые области задач связаны с приложением, а не с конкретным документом. Вы можете создавать настраиваемые области задач в надстройках VSTO для некоторых приложений Microsoft Office. Дополнительные сведения см. в разделе [настраиваемые области задач](../vsto/custom-task-panes.md).

## <a name="display-the-actions-pane"></a>Отображение панели «действия»
 Панель действий представлена классом <xref:Microsoft.Office.Tools.ActionsPane>. При создании проекта на уровне документа экземпляр данного класса доступен в коде с помощью поля `ActionsPane` класса `ThisWorkbook` (для Excel) или `ThisDocument` (для Word) в проекте. Чтобы отобразить панель действий, добавьте элемент управления Windows Forms в свойство <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> поля `ActionsPane`. Следующий пример кода добавляет элемент управления с именем `actions` на панель действий.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet7":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet7":::

 Панель действий становится видимой во время выполнения, как только вы явно добавляете на нее элемент управления. После отображения панели действий вы можете динамически добавлять или удалять элементы управления в ответ на действия пользователя. Как правило, вы добавляете код, чтобы показать панель действий, в обработчик событий `Startup` для `ThisDocument` или `ThisWorkbook`, чтобы панель действий отображалась при первом открытии документа. Однако вам может потребоваться отобразить панель действий только в ответ на действия пользователя в документе. Например, можно добавить код в событие `Click` элемента управления в документе.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Добавление нескольких элементов управления на панель «действия»
 При добавлении нескольких элементов управления на панель действий следует сгруппировать элементы управления в пользовательский элемент управления, а затем добавить пользовательский элемент управления к <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> свойству. Этот процесс состоит из следующих шагов.

1. Создайте пользовательский интерфейс панели действий, добавив элемент **управления панели действий** или элемент **пользовательского элемента управления** в проект. Оба эти элемента включают пользовательский класс <xref:System.Windows.Forms.UserControl> Windows Forms. **Элемент управления панели действий** и элементы **пользовательского элемента управления** эквивалентны; Единственное отличие заключается в их имени.

2. Добавление элементов управления Windows Forms в <xref:System.Windows.Forms.UserControl> с помощью конструктора или кода.

   > [!NOTE]
   > Можно также добавить элементы управления WPF на панель действий, добавив WPF <xref:System.Windows.Controls.UserControl> в <xref:System.Windows.Forms.UserControl> Windows Forms. Дополнительные сведения см. [в статье Использование элементов управления WPF в решениях Office](../vsto/using-wpf-controls-in-office-solutions.md).

3. Добавьте экземпляр настраиваемого пользовательского элемента управления к элементам управления, которые содержатся в поле `ActionsPane` класса `ThisWorkbook` (для Excel) или `ThisDocument` (для Word) в проекте.

   Примеры, демонстрирующие этот процесс более подробно, см. в разделе [руководство. Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

## <a name="hide-the-actions-pane"></a>Скрыть панель действий
 Хотя класс <xref:Microsoft.Office.Tools.ActionsPane> содержит метод <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> и свойство <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, панель действий невозможно удалить из пользовательского интерфейса с помощью членов класса <xref:Microsoft.Office.Tools.ActionsPane>. Вызов <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> метода или присвоение <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> свойству значения **false** скрывает только элементы управления на панели действий; она не скрывает область задач.

 Существует несколько способов скрыть область задач в решении.

- Для Word установите <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> свойство <xref:Microsoft.Office.Interop.Word.TaskPane> объекта, представляющего область задач «действия с документом», в **значение false**. Код в следующем примере должен выполняться из класса `ThisDocument` в проекте.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet34":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet34":::

- Для Excel присвойте <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> свойству объекта значение <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> **false**. Код в следующем примере должен выполняться из класса `ThisWorkbook` в проекте.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet11":::

- Для Word или Excel можно также задать <xref:Microsoft.Office.Core.CommandBar.Visible%2A> для свойства панели команд, представляющей область задач, **значение false**. Код в следующем примере должен выполняться из класса `ThisDocument` или `ThisWorkbook` в проекте.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet9":::

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Очистить панель действий при открытии документа
 Когда пользователь сохраняет документ, когда отображается область действий, панель действий отображается каждый раз при открытии документа, независимо от того, содержит ли панель действий элементы управления. Если вы хотите управлять отображением панели действий, вызовите метод <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> поля `ActionsPane` в обработчике событий `Startup` для `ThisDocument` или `ThisWorkbook`, чтобы убедиться, что панель действий невидима при открытии документа.

### <a name="determine-when-the-actions-pane-is-closed"></a>Определение того, когда панель действий закрыта
 При закрытии панели действий события не инициируются. Хотя класс <xref:Microsoft.Office.Tools.ActionsPane> содержит событие <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, оно не возникает, когда пользователь закрывает панель действий. Вместо этого событие возникает при скрытии элементов управления на панели действий путем вызова <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> метода или присвоения <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> свойству значения **false**.

 Когда пользователь закрывает панель действий, пользователь может снова отобразить его, выполнив одну из следующих процедур в пользовательском интерфейсе приложения.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Отображение панели действий с помощью пользовательского интерфейса Word или Excel

1. На ленте перейдите на вкладку **вид** .

2. В группе **Показать/скрыть** щелкните переключатель действия с **документом** .

## <a name="program-actions-pane-events"></a>События панели действий программы
 Вы можете добавить несколько элементов управления на панель действий и затем написать код для реагирования на события в документе, отображая и скрывая пользовательские элементы управления. Если сопоставить элементы схемы XML с вашим документом, вы сможете показывать определенные пользовательские элементы управления в панели действий всякий раз, когда курсор находится внутри одного из XML-элементов. Дополнительные сведения см. в разделе [как сопоставлять схемы с документами Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) и [как сопоставлять схемы с листами в Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 Можно также написать код, чтобы реагировать на события любого объекта, включая ведущий элемент управления, приложение и документ. Дополнительные сведения см. в разделе [Пошаговое руководство. Программирование для событий элемента управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Привязка данных к элементам управления на панели «действия»
 Возможности привязки данных элементов управления на панели действий аналогичны возможностям элементов управления в формах Windows Forms. Элементы управления можно привязать к источникам данных, таким как наборы данных, типизированные наборы данных и XML-код. Дополнительные сведения см. в разделе [Привязка данных и Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Вы можете привязать элементы управления на панели действий и элементы управления в документе к одному набору данных. Например, можно создать иерархическое отношение между элементами управления на панели действий и элементами управления на листе. Дополнительные сведения см. [в разделе Пошаговое руководство. Привязка данных к элементам управления на панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

## <a name="validate-data-in-actions-pane-controls"></a>Проверка данных в элементах управления панели действий
 Если вы показываете окно сообщения в обработчике событий <xref:System.Windows.Forms.Control.Validating> элемента управления на панели действий, это событие может быть вызвано во второй раз при перемещении фокуса с элемента управления на окно сообщения. Чтобы предотвратить это, используйте элемент управления <xref:System.Windows.Forms.ErrorProvider> для отображения сообщений об ошибке проверки.

## <a name="user-control-stacking-order"></a>Порядок размещения элементов управления пользователя
 Если вы применяете несколько пользовательских элементов управления, можно написать код, чтобы правильно размещать их в панели действий в зависимости от того, закреплена ли она вертикально или горизонтально. Можно задать порядок расположения пользовательских элементов управления на панели действий с помощью перечисления <xref:Microsoft.Office.Tools.StackStyle> свойства <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>. Дополнительные сведения см. в разделе [руководство. Управление макетом элементов управления на панелях действий](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 Свойство <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> может принимать следующие значения перечисления <xref:Microsoft.Office.Tools.StackStyle>.

|Стиль расположения|Определение|
|--------------------|----------------|
|фромботтом|Размещение от нижней части панели действий.|
|фромлефт|Размещение от левой части панели действий.|
|фромригхт|Размещение от правой части панели действий.|
|фромтоп|Размещение от верхней части панели действий.|
|Нет|Порядок расположения не определен, он определяется разработчиком.|

 Следующий код задает свойство <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> так, чтобы располагать пользовательские элементы управления в верхней части панели действий.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet10":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet10":::

## <a name="anchor-controls"></a>Элементы управления привязки
 Если пользователь изменяет размер панели действий во время выполнения, размеры элементов управления могут изменяться вместе с ней. Вы можете использовать свойство <xref:System.Windows.Forms.Control.Anchor%2A> элемента управления Windows Forms, чтобы закрепить элементы управления на панели действий. Таким же образом можно закрепить элементы управления Windows Forms на пользовательском элементе управления. Дополнительные сведения см. в разделе [руководство. Привязка элементов управления к Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Изменение размера панели действий
 Невозможно напрямую изменить размер <xref:Microsoft.Office.Tools.ActionsPane>, так как <xref:Microsoft.Office.Tools.ActionsPane> внедряется в область задач. Однако можно программно изменить ширину области задач, задав свойство <xref:Microsoft.Office.Core.CommandBar.Width%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач. Вы можете изменить высоту области задач, если она закреплена горизонтально или является перемещаемой.

 Программное изменение размера области задач не рекомендуется, так как пользователь должен иметь возможность выбрать размер области задач, который наилучшим образом соответствует своим потребностям. Однако, если вам необходимо изменить ширину области задач, для этого можно использовать следующий код.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet102":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet102":::

## <a name="reposition-the-actions-pane"></a>Изменить расположение панели действий
 Невозможно изменить положение <xref:Microsoft.Office.Tools.ActionsPane> напрямую, так как он внедрен в область задач. Тем не менее можно программно переместить область задач, задав свойство <xref:Microsoft.Office.Core.CommandBar.Position%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач.

 Программное изменение расположения области задач не рекомендуется, так как пользователь должен иметь возможность выбрать расположение области задач на экране, которое лучше подходит для своих нужд. Однако, если вам все-таки необходимо переместить область задач, для этого можно использовать следующий код.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet100":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet100":::

> [!NOTE]
> Пользователи могут в любое время переместить область задач вручную. Нельзя гарантировать, что область задач останется закрепленной в положении, заданном программными средствами. Однако можно проверить изменение ориентации и убедиться, что элементы управления на панели действий располагаются в правильном направлении. Дополнительные сведения см. в разделе [руководство. Управление макетом элементов управления на панелях действий](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 Установка <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> свойств и <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> для объекта <xref:Microsoft.Office.Tools.ActionsPane> не изменяет его расположение, так как <xref:Microsoft.Office.Tools.ActionsPane> объект внедряется в область задач.

 Если область задач не закреплена, можно установить свойства <xref:Microsoft.Office.Core.CommandBar.Top%2A> и <xref:Microsoft.Office.Core.CommandBar.Left%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач. Следующий код перемещает панель задач в верхний левый угол документа.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet101":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet101":::

## <a name="see-also"></a>См. также статью
- [Использование элементов управления WPF в решениях Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Как добавить панель действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Пошаговое руководство. Привязка данных к элементам управления в области действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Пошаговое руководство. Привязка данных к элементам управления в области действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Руководство. Управление макетом элементов управления на панелях действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
