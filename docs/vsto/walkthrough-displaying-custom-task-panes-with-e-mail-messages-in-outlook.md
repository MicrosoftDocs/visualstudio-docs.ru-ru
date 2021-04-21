---
title: Отображение настраиваемых областей задач с сообщениями электронной почты в Outlook
description: Узнайте, как отобразить уникальный экземпляр настраиваемой области задач с каждым сообщением электронной почты в созданном или открытом приложении Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bb1aed5ef110b726dae6e51337b0934ae0a8e69d
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824215"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Пошаговое руководство. Отображение настраиваемых областей задач с сообщениями электронной почты в Outlook
  В этом пошаговом руководстве показано, как отобразить уникальный экземпляр настраиваемой области задач для каждого созданного или открытого сообщения электронной почты. Пользователи могут отображать или скрывать настраиваемую область задач с помощью кнопки на ленте каждого сообщения электронной почты.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Чтобы отображать настраиваемую область задач с несколькими окнами проводника или инспектора, необходимо создать новый экземпляр настраиваемой области задач для каждого открытого окна. Дополнительные сведения о поведении настраиваемых областей задач в окнах Outlook см. в разделе [настраиваемые области задач](../vsto/custom-task-panes.md).

> [!NOTE]
> В этом пошаговом руководстве код надстройки VSTO представлен небольшими частями для облегчения обсуждения логики кода.

 В этом пошаговом руководстве описаны следующие задачи:

- Конструирование пользовательского интерфейса настраиваемой области задач.

- Создание пользовательского интерфейса настраиваемой ленты.

- Отображение пользовательского пользовательского интерфейса ленты с сообщениями электронной почты.

- Создание класса для управления окнами инспектора и настраиваемыми областями задач.

- Инициализация и освобождение ресурсов, используемых надстройкой VSTO.

- Синхронизация выключателя на ленте с настраиваемой областью задач.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] или Microsoft Outlook 2010.

## <a name="create-the-project"></a>Создание проекта
 Настраиваемые области задач реализуются в надстройках VSTO. Начните с создания проекта надстройки VSTO для Outlook.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект **надстройки Outlook** с именем **OutlookMailItemTaskPane**. Используйте шаблон проекта **Надстройка Outlook** . Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл кода *ThisAddIn. CS* или *ThisAddIn. vb* и добавляет проект **OutlookMailItemTaskPane** в **Обозреватель решений**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Проектирование пользовательского интерфейса настраиваемой области задач
 Визуальный конструктор для настраиваемых областей задач не предусмотрен, но можно создать пользовательский элемент управления с нужным пользовательским интерфейсом. Настраиваемая область задач в этой надстройке VSTO имеет простой пользовательский интерфейс, содержащий элемент управления <xref:System.Windows.Forms.TextBox> . Далее в этом пошаговом руководстве вы добавите этот пользовательский элемент управления в настраиваемую область задач.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Проектирование пользовательского интерфейса настраиваемой области задач

1. В **обозревателе решений**, щелкните проект **OutlookMailItemTaskPane** .

2. В меню **Проект** выберите команду **Добавить пользовательский элемент управления**.

3. В диалоговом окне **Добавление нового элемента** измените имя нового пользовательского элемента управления на **TaskPaneControl**, а затем нажмите кнопку **Добавить**.

     Пользовательский элемент управления откроется в конструкторе.

4. Перетащите элемент управления **TextBox** со вкладки **Стандартные элементы управления** на **панели элементов** в пользовательский элемент управления.

## <a name="design-the-user-interface-of-the-ribbon"></a>Проектирование пользовательского интерфейса ленты
 Одной из целей этой надстройки VSTO является предоставление пользователям возможности скрывать или отображать настраиваемую область задач с ленты каждого сообщения электронной почты. Чтобы обеспечить пользовательский интерфейс, создайте пользовательский интерфейс настраиваемой ленты, отображающий выключатель, который пользователь может щелкнуть, чтобы отобразить или скрыть настраиваемую область задач.

### <a name="to-create-a-custom-ribbon-ui"></a>Создание пользовательского интерфейса настраиваемой ленты

1. В меню **Проект** выберите **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите элемент **Лента (визуальный конструктор)**.

3. Измените имя новой ленты на **ManageTaskPaneRibbon** и нажмите кнопку **Добавить**.

     В конструкторе ленты откроется файл *ManageTaskPaneRibbon.cs* или *ManageTaskPaneRibbon.vb* и отобразятся вкладка и группа, используемые по умолчанию.

4. В конструкторе ленты щелкните группу **group1**.

5. В окне **Свойства** задайте для свойства **Label** значение **Диспетчер области задач**.

6. Перетащите элемент управления ToggleButton со вкладки **Элементы управления ленты Office** на **панели элементов** в группу **Диспетчер области задач** .

7. Нажмите **toggleButton1**.

8. В окне **Свойства** задайте для свойства **Label** значение **Показать область задач**.

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Отображение пользовательского интерфейса пользовательской ленты с сообщениями электронной почты
 Настраиваемая область задач, которую вы создаете в этом пошаговом руководстве, должна появляться только с окнами инспектора, содержащими сообщения электронной почты. Поэтому задайте свойства таким образом, чтобы ваш пользовательский интерфейс настраиваемой ленты отображался только с этими окнами.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Отображение пользовательского пользовательского интерфейса ленты с сообщениями электронной почты

1. В конструкторе лент щелкните ленту **ManageTaskPaneRibbon** .

2. В окне **Свойства** щелкните раскрывающийся список рядом со свойством **RibbonType**, и выберите **Microsoft.Outlook.Mail.Compose** и **Microsoft.Outlook.Mail.Read**.

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Создание класса для управления окнами инспектора и настраиваемыми областями задач
 Существует несколько случаев, в которых Надстройка VSTO должна указывать, какая настраиваемая область задач связана с конкретным сообщением электронной почты. Это следующие случаи.

- Когда пользователь закрывает сообщение электронной почты. В этом случае надстройка VSTO должна удалить соответствующую настраиваемую область задач, чтобы ресурсы, используемые этой надстройкой VSTO, были правильно освобождены.

- Когда пользователь закрывает настраиваемую область задач. В этом случае надстройка VSTO должна обновить состояние выключателя на ленте сообщения электронной почты.

- Когда пользователь нажимает выключатель на ленте. В этом случае надстройка VSTO должна скрыть или отобразить соответствующую область задач.

  Чтобы включить надстройку VSTO для наблюдения за тем, какая настраиваемая область задач связана с каждым открытым сообщением электронной почты, создайте пользовательский класс, который заключает в оболочку пары <xref:Microsoft.Office.Interop.Outlook.Inspector> <xref:Microsoft.Office.Tools.CustomTaskPane> объектов и. Этот класс создает новый объект настраиваемой области задач для каждого сообщения электронной почты и удаляет настраиваемую область задач при закрытии соответствующего сообщения электронной почты.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Создание класса для управления окнами инспектора и настраиваемыми областями задач

1. В **обозревателе решений** щелкните правой кнопкой мыши файл *ThisAddIn.cs* или *ThisAddIn.vb* и выберите в контекстном меню команду **Просмотреть код**.

2. Добавьте следующие инструкции в начало файла.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet2":::

3. Добавьте следующий код в файл *ThisAddIn.cs* или *ThisAddIn.vb* за пределами класса `ThisAddIn` (для Visual C# добавьте этот код в пространство имен `OutlookMailItemTaskPane` ). Класс `InspectorWrapper` управляет парой объектов <xref:Microsoft.Office.Interop.Outlook.Inspector> и <xref:Microsoft.Office.Tools.CustomTaskPane> . Вы завершите определение этого класса в следующих шагах.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet3":::

4. Добавьте следующий конструктор после кода, добавленного на предыдущем шаге. Этот конструктор создает и инициализирует новую настраиваемую область задач, связанную с переданным объектом <xref:Microsoft.Office.Interop.Outlook.Inspector> . В C# этот конструктор также присоединяет обработчики событий к событию <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> объекта <xref:Microsoft.Office.Interop.Outlook.Inspector> и к событию <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> объекта <xref:Microsoft.Office.Tools.CustomTaskPane> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet4":::

5. Добавьте следующий метод после кода, добавленного на предыдущем шаге. Этот метод является обработчиком событий для события <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> объекта <xref:Microsoft.Office.Tools.CustomTaskPane> , содержащегося в классе `InspectorWrapper` . Этот код обновляет состояние выключателя всякий раз, когда пользователь открывает или закрывает настраиваемую область задач.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet5":::

6. Добавьте следующий метод после кода, добавленного на предыдущем шаге. Этот метод является обработчиком событий для <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> события <xref:Microsoft.Office.Interop.Outlook.Inspector> объекта, содержащего текущее сообщение электронной почты. Обработчик событий освобождает ресурсы при закрытии сообщения электронной почты. Он также удаляет текущую область задач из коллекции `CustomTaskPanes` . Это помогает предотвратить несколько экземпляров настраиваемой области задач при открытии следующего сообщения электронной почты.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet6":::

7. Добавьте следующий код после кода, добавленного на предыдущем шаге. Далее в этом пошаговом руководстве вы будете вызывать это свойство из метода в пользовательском интерфейсе настраиваемой ленты, чтобы отобразить или скрыть настраиваемую область задач.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet7":::

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Инициализация и очистка ресурсов, используемых надстройкой
 Добавьте код в класс `ThisAddIn` для инициализации надстройки VSTO при ее загрузке, а также для освобождения ресурсов, используемых этой надстройкой VSTO, при ее выгрузке. Надстройка VSTO инициализируется путем настройки обработчика событий для <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> события и передачи всех существующих сообщений электронной почты этому обработчику событий. Когда надстройка VSTO выгружается, отсоедините этот обработчик событий и освободите объекты, используемые надстройкой VSTO.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Инициализация и освобождение ресурсов, используемых надстройкой VSTO

1. В файле *ThisAddIn.cs* или *ThisAddIn.vb* найдите определение класса `ThisAddIn` .

2. Добавьте в класс `ThisAddIn` следующие объявления.

   - Поле `inspectorWrappersValue` содержит все объекты <xref:Microsoft.Office.Interop.Outlook.Inspector> и `InspectorWrapper` , которыми управляет надстройка VSTO.

   - Поле `inspectors` содержит ссылку на коллекцию окон инспектора в текущем экземпляре Outlook. Эта ссылка не позволит сборщику мусора освободить память, содержащую обработчик событий для события <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> , который вы объявите на следующем шаге.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet8":::

3. Замените метод `ThisAddIn_Startup` приведенным ниже кодом. Этот код присоединяет обработчик событий к событию <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> и передает каждый существующий объект <xref:Microsoft.Office.Interop.Outlook.Inspector> в данный обработчик событий. Если пользователь загружает надстройку VSTO после того, как Outlook уже запущен, Надстройка VSTO использует эти сведения для создания настраиваемых областей задач для всех уже открытых сообщений электронной почты.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet9":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet9":::

4. Замените метод `ThisAddIn_ShutDown` приведенным ниже кодом. Этот код отсоединяет обработчик событий <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> и освобождает объекты, используемые надстройкой VSTO.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet10":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet10":::

5. Добавьте следующий обработчик событий <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> в класс `ThisAddIn` . Если новый <xref:Microsoft.Office.Interop.Outlook.Inspector> содержит сообщение электронной почты, метод создает экземпляр нового `InspectorWrapper` объекта для управления связью между сообщением электронной почты и соответствующей областью задач.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet11":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet11":::

6. Добавьте в класс `ThisAddIn` указанное ниже свойство. Это свойство предоставляет закрытое поле `inspectorWrappersValue` коду за пределами класса `ThisAddIn` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet12":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet12":::

## <a name="checkpoint"></a>Контрольная точка
 Постройте проект, чтобы убедиться, что компиляция выполняется без ошибок.

### <a name="to-build-your-project"></a>Построение проекта

1. В **обозревателе решений** щелкните проект **OutlookMailItemTaskPane** правой кнопкой мыши и выберите пункт **Сборка**. Убедитесь, что проект компилируется без ошибок.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Синхронизация выключателя на ленте с настраиваемой областью задач
 Выключатель будет выглядеть как нажатый, когда область задач отображена, и как не нажатый, когда область задач скрыта. Чтобы синхронизировать состояние этой кнопки с настраиваемой областью задач, измените обработчик событий <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> этого выключателя.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Синхронизация настраиваемой области задач с выключателем

1. В конструкторе ленты дважды щелкните выключатель **Показать область задач** .

     Visual Studio автоматически создает обработчик событий с именем `toggleButton1_Click`, который обрабатывает событие <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> выключателя. Visual Studio также открывает файл *ManageTaskPaneRibbon.cs* или *ManageTaskPaneRibbon.vb* в редакторе кода.

2. Добавьте следующие инструкции в начале файла *ManageTaskPaneRibbon.cs* или *ManageTaskPaneRibbon.vb* .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet14":::

3. Замените обработчик событий `toggleButton1_Click` следующим кодом. Когда пользователь нажимает выключатель, этот метод отображает или скрывает настраиваемую область задач, связанную с текущим окном инспектора.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet15":::

## <a name="test-the-project"></a>Тестирование проекта
 Когда вы запускаете отладку проекта, открывается Outlook и загружается надстройка VSTO. Надстройка VSTO Отображает уникальный экземпляр настраиваемой области задач с каждым открытым сообщением электронной почты. Создайте несколько новых сообщений электронной почты, чтобы протестировать код.

### <a name="to-test-the-vsto-add-in"></a>Тестирование надстройки VSTO

1. Нажмите клавишу **F5**.

2. В Outlook нажмите кнопку **создать** , чтобы создать новое сообщение электронной почты.

3. На ленте сообщения электронной почты перейдите на вкладку **надстройки** и нажмите кнопку **Показывать область задач** .

    Убедитесь, что с сообщением электронной почты отображается область задач с заголовком **Моя панель задач** .

4. В этой области задач введите в текстовом поле **Первая область задач** .

5. Закройте область задач.

    Убедитесь, что состояние кнопки **Показать область задач** изменилось, и она больше не выглядит нажатой.

6. Снова нажмите кнопку **Показать область задач** .

    Убедитесь, что область задач открывается и текстовое поле по-прежнему содержит строку **Первая область задач**.

7. В Outlook щелкните **создать** , чтобы создать второе сообщение электронной почты.

8. На ленте сообщения электронной почты перейдите на вкладку **надстройки** и нажмите кнопку **Показывать область задач** .

    Убедитесь, что с сообщением электронной почты отображается область задач с заголовком **Моя панель задач** , а текстовое поле в этой области задач пустое.

9. В этой области задач введите в текстовом поле **Вторая область задач** .

10. Изменение фокуса на первое сообщение электронной почты.

     Убедитесь, что область задач, связанная с этим сообщением электронной почты, по-прежнему отображает **первую область задач** в текстовом поле.

    Эта надстройка VSTO также обрабатывает более сложные сценарии, которые вы можете попробовать. Например, можно проверить поведение при просмотре сообщений электронной почты с помощью кнопок « **следующий элемент** » и « **предыдущий элемент** ». Вы также можете проверить поведение при выгрузке надстройки VSTO, открыть несколько сообщений электронной почты, а затем перезагрузить надстройку VSTO.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения о создании настраиваемых областей задач см. в следующих разделах:

- Создание настраиваемой области задач в надстройке VSTO для другого приложения. Дополнительные сведения о приложениях, поддерживающих настраиваемые области задач, см. в разделе [настраиваемые области задач](../vsto/custom-task-panes.md).

- Автоматизация приложения Microsoft Office с помощью настраиваемой области задач. Дополнительные сведения см. в разделе [Пошаговое руководство. Автоматизация приложения из настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Создание в Excel кнопки ленты, которая может использоваться для скрытия или отображения настраиваемой области задач. Дополнительные сведения см. в разделе [Пошаговое руководство. Синхронизация настраиваемой области задач с помощью кнопки на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

## <a name="see-also"></a>См. также статью
- [Настраиваемые области задач](../vsto/custom-task-panes.md)
- [Как добавить настраиваемую область задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Пошаговое руководство. Автоматизация приложения с помощью настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Пошаговое руководство. Синхронизация настраиваемой области задач с помощью кнопки на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
