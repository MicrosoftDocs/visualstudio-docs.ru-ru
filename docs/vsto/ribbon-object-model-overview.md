---
title: Общие сведения об объектной модели ленты
description: Сведения о том, как Инструменты Visual Studio для среды выполнения Office предоставляет строго типизированную объектную модель, которую можно использовать для получения и задания свойств элементов управления ленты во время выполнения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f053e87f8cdfd2bdf87bbdf4b7d115f6d9bbec26
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823994"
---
# <a name="ribbon-object-model-overview"></a>Общие сведения об объектной модели ленты
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Предоставляет объектную модель со строгой типизацией, которую можно использовать для получения и задания свойств элементов управления ленты во время выполнения. Например, можно динамически заполнять элементы управления меню или отображать или скрывать элементы управления в зависимости от контекста. На ленту можно также добавить вкладки, группы и элементы управления, но только перед загрузкой ленты приложением Office. Дополнительные сведения см. в разделе [Задание свойств, которые становятся доступны только для чтения](#SettingReadOnlyProperties).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Эта объектная модель ленты состоит главным образом от [класса ленты](#RibbonClass), [событий ленты](#RibbonEvents)и [классов элементов управления ленты](#RibbonControlClasses).

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Класс ленты
 При добавлении в проект нового элемента **"Лента (визуальный конструктор)"** Visual Studio добавляет в проект класс **ленты** . Класс **Ribbon** наследует от <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> класса.

 Этот класс отображается как разделяемый класс, который разбивается между файлом кода ленты и файлом кода конструктора ленты.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> События ленты
 Класс **Ribbon** содержит следующие три события:

|Событие|Описание|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Возникает, когда приложение Office загружает настройку ленты. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>Обработчик событий автоматически добавляется в файл кода ленты. Этот обработчик событий используется для запуска пользовательского кода при загрузке ленты.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Позволяет кэшировать изображения в настройке ленты при загрузке ленты. При написании кода для кэширования образов ленты в этом обработчике событий можно получить небольшое увеличение производительности. Для получения дополнительной информации см. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Возникает при закрытии экземпляра ленты.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Элементы управления ленты
 <xref:Microsoft.Office.Tools.Ribbon>Пространство имен содержит тип для каждого элемента управления, отображаемого в группе **элементов** **управления ленты Office** .

 В следующей таблице показаны типы для каждого `Ribbon` элемента управления. Описание каждого элемента управления см. в разделе [Общие сведения о ленте](../vsto/ribbon-overview.md).

|Имя элемента управления|Имя класса|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Кнопка**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Крывающихся**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**Поле**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Галерея**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Группа**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Меню**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**TAB**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 <xref:Microsoft.Office.Tools.Ribbon>Пространство имен использует префикс "Ribbon" для этих типов, чтобы избежать конфликта имен с именами классов элементов управления в <xref:System.Windows.Forms> пространстве имен.

 При добавлении элемента управления в конструктор ленты конструктор ленты объявляет класс для этого элемента управления как поле в файле кода конструктора ленты.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Общие задачи с использованием свойств элементов управления ленты
 Каждый `Ribbon` элемент управления содержит свойства, которые можно использовать для выполнения различных задач, таких как назначение метки элементу управления или скрытие и отображение элементов управления.

 В некоторых случаях свойства становятся доступны только для чтения после загрузки ленты или после добавления элемента управления в динамическое меню. Дополнительные сведения см. в разделе [Задание свойств, которые становятся доступны только для чтения](#SettingReadOnlyProperties).

 В следующей таблице описаны некоторые задачи, которые можно выполнить с помощью `Ribbon` свойств элемента управления.

|Для выполнения этой задачи|Процедура|
|--------------------|--------------|
|Скрытие или отображение элемента управления.|Используйте свойство Visible.|
|Включение или отключение элемента управления.|Используйте свойство Enabled.|
|Задает размер элемента управления.|Используйте свойство Контролсизе.|
|Получение изображения, отображаемого на элементе управления.|Используйте свойство Image.|
|Изменение метки элемента управления.|Используйте свойство Label.|
|Добавление определяемых пользователем данных в элемент управления.|Используйте свойство Tag.|
|Получение элементов в,, <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> или<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> элемента.|Используйте свойство Items.|
|Добавление элементов в <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> элемент управления, или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Используйте свойство Items.|
|Добавьте элементы управления в <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> .|Используйте свойство Items.<br /><br /> Чтобы добавить элементы управления в <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> приложение Office после загрузки ленты, необходимо установить <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> свойство в **значение true** перед загрузкой ленты в приложение Office. Дополнительные сведения см. в разделе [Задание свойств, которые становятся доступны только для чтения](#SettingReadOnlyProperties).|
|Получение выбранного элемента <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> ,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Используйте свойство SelectedItem. Для <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> Используйте <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> свойство.|
|Получите группы в <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> .|Используйте свойство <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|
|Укажите число строк и столбцов, отображаемых в <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Используйте <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> Свойства и <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> .|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Задание свойств, которые становятся доступны только для чтения
 Некоторые свойства можно задать только до загрузки ленты. Задать эти свойства можно тремя способами:

- В окне **Свойства** Visual Studio.

- В конструкторе класса **Ribbon** .

- В `CreateRibbonExtensibilityObject` методе `ThisAddin` `ThisWorkbook` класса, или `ThisDocument` проекта.

  Динамические меню предоставляют некоторые исключения. Можно создавать новые элементы управления, задавать их свойства, а затем добавлять их в динамическое меню во время выполнения даже после загрузки ленты, содержащей меню.

  Свойства элементов управления, добавляемых в динамическое меню, можно задать в любое время.

  Дополнительные сведения см. в разделе [свойства, которые становятся доступны только для чтения](#ReadOnlyProperties).

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Задание свойств в конструкторе ленты
 Свойства `Ribbon` элемента управления можно задать в конструкторе класса **Ribbon** . Этот код должен появиться после вызова `InitializeComponent` метода. В следующем примере в группу добавляется новая кнопка, если текущее время составляет 17:00 по тихоокеанскому времени (UTC-8) или более поздней версии.

 Добавьте следующий код.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb" id="Snippet1":::

 В проектах Visual C#, обновленных с Visual Studio 2008, конструктор отображается в файле кода ленты.

 В проектах Visual Basic или в проектах Visual C#, созданных в [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , конструктор отображается в файле кода конструктора лент. Этот файл называется *йоурриббонитем*. Designer. cs или *йоурриббонитем*. Designer. vb. Чтобы просмотреть этот файл в Visual Basic проектах, необходимо сначала нажать кнопку " **Показать все файлы** " в Обозреватель решений.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Задание свойств в методе Креатериббонекстенсибилитйобжект
 Свойства `Ribbon` элемента управления можно задать при переопределении `CreateRibbonExtensibilityObject` метода в `ThisAddin` `ThisWorkbook` классе, или `ThisDocument` проекта. Дополнительные сведения о `CreateRibbonExtensibilityObject` методе см. в разделе [Лента Overview](../vsto/ribbon-overview.md).

 В следующем примере задаются свойства ленты в `CreateRibbonExtensibilityObject` методе `ThisWorkbook` класса проекта книги Excel.

 Добавьте следующий код.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs" id="Snippet2":::

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Свойства, которые становятся доступны только для чтения
 В следующей таблице показаны свойства, которые можно задать только до загрузки ленты.

> [!NOTE]
> Свойства элементов управления в динамических меню можно задать в любое время. Эта таблица не применяется в этом случае.

|Свойство|Класс элемента управления Ribbon|
|--------------|--------------------------|
|**боксстиле**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Число**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**диалоглаунчер**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**динамически;**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Глобальный**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Группы**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**итемсизе**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Имя**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Позиция**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Количества**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**шовитемимаже**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**шовитемлабел**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**шовитемселектион**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**сизестринг**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**стартфромскратч**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Вкладки**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Title**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Задание свойств для лент, отображаемых в инспекторах Outlook
 Новый экземпляр ленты создается каждый раз, когда пользователь открывает инспектор, в котором отображается лента. Однако свойства, перечисленные в таблице выше, можно задать только до создания первого экземпляра ленты. После создания первого экземпляра эти свойства становятся доступны только для чтения, поскольку первый экземпляр определяет XML-файл, используемый Outlook для загрузки ленты.

 Если имеется условная логика, которая задает для любого из этих свойств другое значение при создании других экземпляров ленты, этот код не будет оказывать никакого влияния.

> [!NOTE]
> Убедитесь, что для каждого элемента управления, добавляемого на ленту Outlook, задано свойство **Name** . Если элемент управления добавляется на ленту Outlook во время выполнения, необходимо задать это свойство в коде. При добавлении элемента управления на ленту Outlook во время разработки свойство Name устанавливается автоматически.

## <a name="ribbon-control-events"></a>События элемента управления ленты
 Каждый класс элемента управления содержит одно или несколько событий. Эти события описаны в следующей таблице.

|Событие|Описание|
|-----------|-----------------|
|Щелкните|Происходит при щелчке элемента управления.|
|TextChanged|Происходит при изменении текста поля ввода или поля со списком.|
|итемслоадинг|Происходит, когда коллекция Items элемента управления запрашивается в Office. Office кэширует коллекцию Items до тех пор, пока код не изменит свойства элемента управления или не вызовите <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> метод.|
|ButtonClick|Происходит при нажатии кнопки в <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> или <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> .|
|SelectionChanged|Происходит при изменении выбора в <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|
|диалоглаунчеркликк|Происходит при щелчке значка запуска диалогового окна в правом нижнем углу группы.|

 Обработчики событий для этих событий имеют два следующих параметра.

|Параметр|Описание|
|---------------|-----------------|
|*отправителя*|Объект <xref:System.Object>, представляющий элемент управления, который вызвал событие.|
|*e*|Объект <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>, содержащий свойство <xref:Microsoft.Office.Core.IRibbonControl>. Этот элемент управления используется для доступа к любому свойству, недоступному в объектной модели ленты, предоставляемой [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|

## <a name="see-also"></a>См. также статью
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Как приступить к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство. Обновление элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Как настроить встроенную вкладку](../vsto/how-to-customize-a-built-in-tab.md)
- [Как добавить элементы управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Как экспортировать ленту из конструктора лент в XML-ленту](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Пошаговое руководство. Отображение ошибок пользовательского интерфейса надстройки](../vsto/how-to-show-add-in-user-interface-errors.md)
