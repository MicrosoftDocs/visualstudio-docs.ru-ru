---
title: Пошаговое руководство. Автоматизация приложения с помощью настраиваемой области задач
description: Создание настраиваемой области задач, которая автоматизирует Microsoft PowerPoint путем вставки дат в слайд, когда пользователь щелкает элемент управления MonthCalendar в пользовательской области задач.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f57ad0c858abb5f151e1b425224b5af34d464c0f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824670"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Пошаговое руководство. Автоматизация приложения с помощью настраиваемой области задач
  В этом пошаговом руководстве рассматриваются способы создания настраиваемой области задач, которая автоматизирует PowerPoint. Настраиваемая область задач вставляет даты в слайд, когда пользователь нажимает элемент управления <xref:System.Windows.Forms.MonthCalendar> в ней.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Хотя в этом пошаговом руководстве используется PowerPoint, рассмотренная процедура применима к любым перечисленным выше приложениям.

 В этом пошаговом руководстве описаны следующие задачи:

- проектирование пользовательского интерфейса настраиваемой области задач;

- автоматизация PowerPoint в настраиваемой области задач;

- отображение настраиваемой области задач в PowerPoint.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft PowerPoint 2010 или [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].

## <a name="create-the-add-in-project"></a>Создание проекта надстройки
 Первым шагом является создание проекта надстройки VSTO для PowerPoint.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект надстройки VSTO для PowerPoint с именем **MyAddIn**, используя шаблон проекта надстройки PowerPoint. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл кода **ThisAddIn. CS** или **ThisAddIn. vb** и добавляет проект **MyAddIn** в **Обозреватель решений**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Проектирование пользовательского интерфейса настраиваемой области задач
 Визуальный конструктор для настраиваемых областей задач не предусмотрен, но вы можете разработать собственный элемент управления с желаемой структурой. Далее в этом пошаговом руководстве вы добавите этот пользовательский элемент управления в настраиваемую область задач.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Проектирование пользовательского интерфейса настраиваемой области задач

1. В меню **Проект** выберите команду **Добавить пользовательский элемент управления**.

2. В диалоговом окне **Добавление нового элемента** измените имя пользовательского элемента управления на **MyUserControl** и нажмите кнопку **Добавить**.

     Пользовательский элемент управления откроется в конструкторе.

3. Перетащите элемент управления **MonthCalendar** со вкладки **Стандартные элементы управления** на **панели элементов** в пользовательский элемент управления.

     Если элемент управления **MonthCalendar** больше поверхности конструктора пользовательского элемента управления, измените размер пользовательского элемента управления в соответствии с размерами элемента управления **MonthCalendar** .

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Автоматизация PowerPoint с помощью настраиваемой области задач
 Задача надстройки VSTO состоит в том, чтобы разместить выбранную дату на первом слайде активной презентации. Используйте событие <xref:System.Windows.Forms.MonthCalendar.DateChanged> элемента управления, чтобы добавить выбранную дату при ее изменении.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Автоматизация PowerPoint в настраиваемой области задач

1. В конструкторе дважды щелкните элемент управления <xref:System.Windows.Forms.MonthCalendar> .

     Откроется файл **MyUserControl.cs** или **MyUserControl.vb** , и будет создан обработчик событий <xref:System.Windows.Forms.MonthCalendar.DateChanged> .

2. Добавьте следующий код в начало файла. Этот код создает псевдонимы для <xref:Microsoft.Office.Core> пространств имен и в [PowerPoint](/previous-versions/office/developer/office-2010/ff763170%28v%3doffice.14%29) .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet1":::

3. Добавьте в класс `MyUserControl` приведенный далее код. Этот код объявляет объект [Shape](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) в качестве члена `MyUserControl` . На следующем шаге эта [фигура](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) будет использоваться для добавления текстового поля к слайду в активной презентации.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet2":::

4. Замените обработчик событий `monthCalendar1_DateChanged` следующим кодом. Этот код добавляет текстовое поле на первый слайд активной презентации, а затем вставляет в это поле выбранную дату. Код использует объект `Globals.ThisAddIn` для получения доступа к объектной модели PowerPoint.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet3":::

5. В **обозревателе решений** щелкните проект **MyAddIn** правой кнопкой мыши и выберите пункт **Сборка**. Убедитесь, что сборка проекта выполняется без ошибок.

## <a name="display-the-custom-task-pane"></a>Отображение настраиваемой области задач
 Для отображения настраиваемой области задач при запуске надстройки VSTO добавьте пользовательский элемент управления в область задач в обработчике событий <xref:Microsoft.Office.Tools.AddIn.Startup> надстройки VSTO.

### <a name="to-display-the-custom-task-pane"></a>Отображение настраиваемой области задач

1. В **обозревателе решений** разверните **PowerPoint**.

2. Щелкните правой кнопкой мыши файл **ThisAddIn.cs** или **ThisAddIn.vb** и выберите пункт **Просмотреть код**.

3. Добавьте в класс `ThisAddIn` приведенный далее код. Этот код объявляет экземпляры `MyUserControl` и <xref:Microsoft.Office.Tools.CustomTaskPane> как члены класса `ThisAddIn` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs" id="Snippet4":::

4. Замените обработчик событий `ThisAddIn_Startup` следующим кодом. Этот код создает новый объект <xref:Microsoft.Office.Tools.CustomTaskPane> , добавляя  объект `MyUserControl` в коллекцию `CustomTaskPanes` . Код также отображает область задач.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs" id="Snippet5":::

## <a name="test-the-add-in"></a>Тестирование надстройки
 При запуске проекта открывается приложение PowerPoint и надстройка отображает настраиваемую область задач. Чтобы протестировать код, щелкните элемент управления <xref:System.Windows.Forms.MonthCalendar> .

### <a name="to-test-your-vsto-add-in"></a>Для тестирования надстройки VSTO выполните следующие действия.

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Убедитесь в том, что настраиваемая область задач видна.

3. Щелкните дату в элементе управления <xref:System.Windows.Forms.MonthCalendar> в области задач.

     Дата вставляется на первом слайде активной презентации.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения о создании настраиваемых областей задач см. в следующих разделах:

- Создание настраиваемой области задач в надстройке VSTO для другого приложения. Дополнительные сведения о приложениях, поддерживающих настраиваемые области задач, см. в разделе [настраиваемые области задач](../vsto/custom-task-panes.md).

- Создание кнопки ленты, которая может использоваться для скрытия или отображения настраиваемой области задач. Дополнительные сведения см. в разделе [Пошаговое руководство. Синхронизация настраиваемой области задач с помощью кнопки на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

- Создание настраиваемой области задач для каждого сообщения электронной почты, открываемого в Outlook. Дополнительные сведения см. [в разделе Пошаговое руководство. Отображение настраиваемых областей задач с сообщениями электронной почты в Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>См. также статью
- [Настраиваемые области задач](../vsto/custom-task-panes.md)
- [Как добавить настраиваемую область задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Пошаговое руководство. Синхронизация настраиваемой области задач с помощью кнопки на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Пошаговое руководство. Отображение настраиваемых областей задач с сообщениями электронной почты в Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
