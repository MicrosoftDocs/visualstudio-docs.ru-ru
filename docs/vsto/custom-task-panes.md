---
title: Настраиваемые области задач
description: Сведения о том, как создавать собственную область задач и предоставлять пользователям знакомый интерфейс для доступа к функциям вашего решения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6c35d963b426fe24a43bef24617f79c042c272e9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828167"
---
# <a name="custom-task-panes"></a>Настраиваемые области задач
  Области задач — это панели пользовательского интерфейса, которые обычно прикрепляются к одной стороне окна в приложении Microsoft Office. Настраиваемые области задач позволяют создать собственную область задач и предоставлять пользователям знакомый интерфейс для доступа к возможностям вашего решения. Например, интерфейс может содержать элементы управления, которые выполняют код для изменения документов или отображения данных из источника данных.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Настраиваемая область задач отличается от панели действий. Панель действий является частью настроек на уровне документа для Microsoft Office Word и Microsoft Office Excel. Дополнительные сведения см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md).

## <a name="benefits-of-custom-task-panes"></a>Преимущества настраиваемых областей задач
 Настраиваемые области задач позволяют интегрировать ваши возможности в знакомый пользовательский интерфейс. Для быстрого создания настраиваемой области задач можно использовать инструменты Visual Studio.

### <a name="familiar-user-interface"></a>Привычный пользовательский интерфейс
 Пользователи приложений в Microsoft Officeной системе уже знакомы с использованием областей задач, таких как **стили и** область задач Форматирование в Word. Настраиваемые области задач работают точно так же, как и другие области задач в системе Microsoft Office. Пользователи могут закреплять настраиваемые области задач с разных сторон окна приложения, или их можно перетаскивать в любое место в окне. Можно создать надстройку VSTO, которая одновременно отображает несколько настраиваемых областей задач, а пользователи могут управлять каждой областью задач по-отдельности.

### <a name="windows-forms-support"></a>Поддержка Windows Forms
 Пользовательский интерфейс настраиваемой области задач, создаваемой с помощью средств разработки Office в Visual Studio, основан на элементах управления Windows Forms. В целях разработки пользовательского интерфейса для настраиваемой области задач можно использовать знакомый конструктор Windows Forms. Для привязки источника данных к элементам управления в области задач также можно использовать поддержку привязки данных в Windows Forms.

## <a name="create-a-custom-task-pane"></a>Создание настраиваемой области задач
 Для создания простой настраиваемой области задач можно использовать следующую процедуру.

1. Создайте пользовательский интерфейс для своей настраиваемой области задач путем добавления элементов управления Windows Forms в объект <xref:System.Windows.Forms.UserControl>.

2. Создайте экземпляр настраиваемой области задач путем передачи пользовательского элемента управления в объект <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> в надстройке VSTO. Эта коллекция возвращает новый объект <xref:Microsoft.Office.Tools.CustomTaskPane>, который можно использовать для изменения внешнего вида области задач и реагирования на инициируемые пользователем события.

   Дополнительные сведения см. в разделе [инструкции. Добавление настраиваемой области задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="create-the-user-interface"></a>Создание пользовательского интерфейса
 Все настраиваемые области задач, созданные с помощью средств разработки Office в Visual Studio, содержат объект <xref:System.Windows.Forms.UserControl>. Этот пользовательский элемент управления предоставляет пользовательский интерфейс настраиваемой области задач. Пользовательский элемент управления можно создать во время разработки или во время выполнения. При создании пользовательского элемента управления во время разработки можно использовать конструктор Windows Forms для создания пользовательского интерфейса своей области задач.

### <a name="instantiate-the-custom-task-pane"></a>Создание экземпляра настраиваемой области задач
 После создания пользовательского элемента управления, содержащего пользовательский интерфейс настраиваемой области задач, необходимо создать экземпляр <xref:Microsoft.Office.Tools.CustomTaskPane>. Для этого необходимо передать пользовательский элемент управления в <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> в надстройке VSTO путем вызова одного из методов <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>. Эта коллекция предоставляется как поле `CustomTaskPanes` класса `ThisAddIn`. Код в следующем примере должен выполняться из класса `ThisAddIn`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

 Методы <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> возвращают новый объект <xref:Microsoft.Office.Tools.CustomTaskPane>. Этот объект можно использовать для изменения внешнего вида области задач и реагирования на инициируемые пользователем события.

### <a name="control-the-task-pane-in-multiple-windows"></a>Управление областью задач в нескольких окнах
 Настраиваемые области задач связаны с окном фрейма документа, в котором пользователю отображается представление документа или элемента. Область задач отображается только в том случае, когда отображается соответствующее окно.

 Чтобы определить, какое из окон отображает настраиваемую область задач, используйте соответствующую перегрузку метода <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> при создании области задач:

- Чтобы связать область задач с активным окном, используйте метод <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>.

- Чтобы связать область задач с документом, который размещается заданным окном, используйте метод <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>.

  Для некоторых приложений Office требуются явные инструкции о том, когда нужно создавать или отображать область задач, если открыты несколько окон. Поэтому важно учитывать место создания экземпляра настраиваемой области задач в своем коде, чтобы гарантировать, что данная область отображается с соответствующими документами или элементами в приложении. Дополнительные сведения см. [в разделе Управление настраиваемыми областями задач в окнах приложений](#Managing).

## <a name="access-the-application-from-the-task-pane"></a>Доступ к приложению из области задач
 Если требуется автоматизация приложения из пользовательского элемента управления, к объектной модели можно непосредственно обращаться с помощью `Globals.ThisAddIn.Application` в своем коде. Доступ к объекту `ThisAddIn` обеспечивает статический класс `Globals`. Поле `Application` данного объекта является точкой входа в объектную модель приложения.

 Дополнительные сведения о `Application` поле `ThisAddIn` объекта см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Пошаговое руководство по автоматизации приложения из настраиваемой области задач см. в разделе [Пошаговое руководство. Автоматическое приложение из настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Дополнительные сведения о `Globals` классе см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="manage-the-user-interface-of-the-task-pane"></a>Управление пользовательским интерфейсом области задач
 После создания области задач можно использовать свойства и события объекта <xref:Microsoft.Office.Tools.CustomTaskPane> для управления пользовательским интерфейсом области задач и реагирования на изменение пользователем области задач.

### <a name="make-the-custom-task-pane-visible"></a>Сделать настраиваемую область задач видимой
 По умолчанию область задач не отображается. Чтобы сделать область задач видимой, необходимо присвоить <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> свойству значение **true**.

 Пользователи могут закрыть область задач в любое время, нажав кнопку **Закрыть** (X) в углу области задач. Тем не менее у пользователей нет стандартного способа, чтобы снова открыть настраиваемую область задач. Если пользователь закрывает настраиваемую область задач, он сможет снова ее увидеть только в том случае, если вы предоставите ему такую возможность.

 При создании настраиваемой области задач в своей надстройке VSTO также следует создать элемент пользовательского интерфейса, например кнопку, которую пользователи могут нажать, чтобы отобразить или скрыть эту область. При создании настраиваемой области задач в приложении Microsoft Office, поддерживающем настройку ленты, на ленте можно добавить группу элементов управления с кнопкой, при нажатии которой эта область будет отображаться или закрываться. Пошаговое руководство, в котором показано, как это сделать, см. в разделе [Пошаговое руководство. Синхронизация настраиваемой области задач с помощью кнопки на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

 При создании настраиваемой области задач в приложении Microsoft Office, не поддерживающем настройку ленты, можно добавить кнопку <xref:Microsoft.Office.Core.CommandBarButton>, при нажатии которой данная область будет отображаться или закрываться.

### <a name="modify-the-appearance-of-the-task-pane"></a>Изменение внешнего вида области задач
 Для управления размером и расположением настраиваемой области задач можно использовать свойства объекта <xref:Microsoft.Office.Tools.CustomTaskPane>. Для внесения других изменений во внешний вид настраиваемой области задач можно использовать свойства объекта <xref:System.Windows.Forms.UserControl>, который содержится в настраиваемой области задач. Например, чтобы указать фоновое изображение для настраиваемой области задач, можно использовать свойство <xref:System.Windows.Forms.Control.BackgroundImage%2A> пользовательского элемента управления.

 В следующей таблице перечислены изменения, которые можно выполнять в настраиваемой области задач с помощью свойств <xref:Microsoft.Office.Tools.CustomTaskPane>.

|Задача|Свойство|
|----------|--------------|
|Изменение размера области задач|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|
|Изменение расположения области задач|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|
|Скрытие области задач или ее отображение|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|
|Запрет для пользователя на изменение расположения области задач|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|

### <a name="program-custom-task-pane-events"></a>События настраиваемой области задач программы
 Надстройку VSTO можно настроить таким образом, чтобы она реагировала на изменения пользователем настраиваемой области задач. Например, если пользователь изменяет ориентацию области с вертикальной на горизонтальную, то может потребоваться перемещение элементов управления.

 В следующей таблице перечислены события, которые можно обрабатывать для реагирования на изменения, вносимые пользователем в настраиваемой области задач.

|Задача|Событие|
|----------|-----------|
|Реагирование на изменение пользователем расположения области задач.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|Реагирование в случае, когда пользователь скрывает область задач или делает ее видимой.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>Очистка ресурсов, используемых областью задач
 После создания настраиваемой области задач объект <xref:Microsoft.Office.Tools.CustomTaskPane> остается в памяти до тех пор, пока ваша надстройка VSTO работает. Объект остается в памяти даже после нажатия пользователем кнопки **закрытия** (X) в углу области задач.

 Чтобы освободить ресурсы, используемые областью задач, пока надстройка VSTO продолжает работать, используйте методы <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> или <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A>. Эти методы позволяют удалить указанный объект <xref:Microsoft.Office.Tools.CustomTaskPane> из коллекции `CustomTaskPanes` и вызывают метод `Dispose` объекта.

 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] автоматически освобождает ресурсы, используемые настраиваемой областью задач, при выгрузке надстройки VSTO. Не вызывайте <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> методы или <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> в `ThisAddIn_Shutdown` обработчике событий в проекте. Эти методы создадут исключение <xref:System.ObjectDisposedException>, так как [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] освобождает ресурсы, используемые объектом <xref:Microsoft.Office.Tools.CustomTaskPane> перед вызовом `ThisAddIn_Shutdown`. Дополнительные сведения о см `ThisAddIn_Shutdown` . [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

## <a name="manage-custom-task-panes-in-multiple-application-windows"></a><a name="Managing"></a> Управление настраиваемыми областями задач в нескольких окнах приложений
 При создании настраиваемой области задач в приложении, которое использует несколько окон для отображения документов и других элементов, необходимо выполнить дополнительные шаги, чтобы гарантировать, что область задач отображается в нужное для пользователя время.

 Настраиваемые области задач во всех приложениях связаны с окном фрейма документа, в котором пользователю отображается представление документа или элемента. Область задач отображается только в том случае, когда отображается соответствующее окно. Однако приложения используют окна фрейма документа по-разному.

 Следующие группы приложений имеют различные требования по разработке.

- [Outlook](#Outlook)

- [Word, InfoPath и PowerPoint](#WordAndInfoPath)

## <a name="outlook"></a><a name="Outlook"></a> Невозможно
 При создании настраиваемой области задач для Outlook для данной области устанавливается связь с конкретным окном проводника или инспектора. Обозреватели — это окна, в которых отображается содержимое папки, а инспекторы — окна, в которых отображается элемент, например сообщение электронной почты или задача.

 Если необходимо отобразить настраиваемую область задач с несколькими окнами проводника или инспектора, то при открытии окна проводника или инспектора нужно создать новый экземпляр данной области. Для этого обработайте событие, возникающее при создании окна проводника или инспектора, а затем создайте область задач в обработчике событий. Также можно обрабатывать события проводника или инспектора, чтобы скрывать или отображать области задач в зависимости от того, какое окно является видимым.

 Чтобы связать область задач с конкретным обозревателем или инспектором, используйте <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> метод для создания области задач и передайте <xref:Microsoft.Office.Interop.Outlook.Explorer> <xref:Microsoft.Office.Interop.Outlook.Inspector> объект или в параметр *Window* . Дополнительные сведения о создании настраиваемых областей задач см. в разделе [Общие сведения о настраиваемых панелях задач](../vsto/custom-task-panes.md).

- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>

  Для отслеживания состояния окон инспектора можно обрабатывать следующие события, связанные с инспектором.

- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Запрет нескольких экземпляров настраиваемой области задач в Outlook
 Чтобы предотвратить отображение нескольких экземпляров настраиваемой области задач в окнах Outlook, удалите явным образом настраиваемую область задач из коллекции `CustomTaskPanes` класса `ThisAddIn` при закрытии каждого окна. Вызовите метод <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> в событии, которое возникает при закрытии окна, например <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> или <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.

 Если настраиваемая область задач не будет удалена явным образом, в окнах Outlook могут отображаться несколько экземпляров данной области. Outlook иногда перезапускает окна. А такие окна сохраняют ссылки на все присоединенные к ним настраиваемые области задач.

## <a name="word-infopath-and-powerpoint"></a><a name="WordAndInfoPath"></a> Word, InfoPath и PowerPoint
 Word, InfoPath и PowerPoint отображают каждый документ в отдельном окне фрейма документа. При создании настраиваемой области задач для этих приложений данная область связывается только с конкретным документом. Если пользователь открывает другой документ, настраиваемая область задач будет скрыта до тех пор, пока более ранний документ не станет снова видимым.

 Если необходимо отобразить настраиваемую область задач с несколькими документами, создайте новый экземпляр этой области, когда пользователь создает новый документ или открывает существующий документ. Для этого обработайте события, возникающие при создании или открытии документа, а затем создайте область задач в обработчиках событий. Также можно обрабатывать события документа для скрытия или отображения областей задач, в зависимости от документа, который является видимым.

 Чтобы связать область задач с конкретным окном документа, используйте <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> метод, чтобы создать область задач, и передайте <xref:Microsoft.Office.Interop.Word.Window> (для Word),  <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (для InfoPath) или [документвиндов](/previous-versions/office/developer/office-2010/ff762047(v=office.14)) (для PowerPoint) в параметр *Window* .

### <a name="word-events"></a>События Word
 Для отслеживания состояния окон документов в Word можно обрабатывать следующие события.

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>

### <a name="infopath-events"></a>События InfoPath
 Для отслеживания состояния окон документов в InfoPath можно обрабатывать следующие события.

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>

### <a name="powerpoint-events"></a>События PowerPoint
 Для отслеживания состояния окон документов в PowerPoint можно обрабатывать следующие события.

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. Афтерневпресентатион](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. Афтерпресентатионопен](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. Невпресентатион](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. Пресентатионопен](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. Виндовактивате](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. Виндовдеактивате](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>См. также статью
- [Как добавить настраиваемую область задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Пошаговое руководство. Автоматизация приложения с помощью настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Пошаговое руководство. Синхронизация настраиваемой области задач с помощью кнопки на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Пошаговое руководство. Отображение настраиваемых областей задач с сообщениями электронной почты в Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
