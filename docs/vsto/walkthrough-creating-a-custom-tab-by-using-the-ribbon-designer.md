---
title: Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент
description: Сведения о создании настраиваемой вкладки, а также добавлении и размещении элементов управления с помощью конструктора лент.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3886e20d45834f98f36b8d7e48f3b11c9ef7d5dd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824826"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент
  Конструктор лент позволяет создать настраиваемую вкладку, а затем добавить и расположить на ней элементы управления.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- [Создание панелей действий](#BKMK_CreateActionsPanes).

- [Создайте настраиваемую вкладку](#BKMK_CreateCustomTab).

- [Скрыть и показать панели действий можно с помощью кнопок на пользовательской вкладке](#BKMK_HideShowActionsPane).

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Создание проекта книги Excel
 Этапы использования конструктора лент практически идентичны для всех приложений Office. В этом примере используется книга Excel.

### <a name="to-create-an-excel-workbook-project"></a>Создание проекта книги Excel

- Создайте проект книги Excel с именем **мексцелриббон**. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новую книгу в конструкторе и добавит проект **мексцелриббон** в **Обозреватель решений**.

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> Создание панелей действий
 Добавьте в проект две настраиваемые панели действий. Позже на настраиваемой вкладке будут добавлены кнопки для скрытия и отображения этих панелей действий.

### <a name="to-create-actions-panes"></a>Создание панелей действий

1. В меню **Проект** выберите пункт **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите **актионспанеконтрол** и нажмите кнопку **добавить**.

     В конструкторе откроется файл **ActionsPaneControl1. CS** или **ActionsPaneControl1. vb** .

3. На вкладке **Общие элементы управления** **панели элементов** добавьте метку к области конструктора.

4. В окне **Свойства** задайте для свойства **Text** элемента label1 **панель действий 1**.

5. Повторите этапы 1–5, чтобы создать вторую панель действий и метку. Задайте для свойства **Text** второй метки значение **панель действий 2**.

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> Создание настраиваемой вкладки
 Один из принципов проектирования приложений Office состоит в том, что пользователь всегда должен иметь возможность распоряжаться пользовательским интерфейсом приложения Office. Чтобы обеспечить такую возможность для панелей действий, можно добавить на настраиваемую вкладку ленты кнопки, скрывающие и отображающие каждую панель. Чтобы создать настраиваемую вкладку, добавьте в проект элемент **Лента (визуальный конструктор)** . Конструктор помогает добавлять и размещать элементы управления, задавать их свойства и обрабатывать связанные с ними события.

### <a name="to-create-a-custom-tab"></a>Создание настраиваемой вкладки

1. В меню **Проект** выберите пункт **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите элемент **Лента (визуальный конструктор)**.

3. Измените имя новой ленты на **MyRibbon** и нажмите кнопку **Добавить**.

     В конструкторе лент откроется файл **MyRibbon.cs** или **MyRibbon.vb** ; отобразятся вкладка и группа, используемые по умолчанию.

4. В конструкторе лент перейдите на вкладку по умолчанию.

5. В окне **Свойства** разверните свойство **ControlID** и задайте для свойства **контролидтипе** значение **Custom**.

6. Задайте для свойства **Метка** значение **Моя пользовательская вкладка**.

7. В конструкторе лент выберите **group1**.

8. В окне **Свойства** задайте для параметра **Метка** значение **Диспетчер панели действий**.

9. С вкладки **элементы управления ленты Office** **панели элементов** перетащите кнопку на группу **group1**.

10. Выберите **Button1**.

11. В окне **Свойства** задайте для **метки** значение **Показывать панель действий 1**.

12. Добавьте вторую кнопку в группу **group1** и задайте для свойства **Метка** значение **Показывать панель действий 2**.

13. Перетащите элемент управления **ToggleButton** с вкладки **элементы управления ленты Office** на **панели элементов** в группу **group1**.

14. Задайте свойство **Метка** , чтобы **Скрыть панель действий**.

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> Скрытие и отображение панелей действий с помощью кнопок на пользовательской вкладке
 Последним этапом является добавление кода, который взаимодействует с пользователем. Добавьте обработчики событий для событий <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> обеих кнопок и события <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> выключателя. Добавьте в эти обработчики событий код для скрытия и отображения панелей действий.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Скрытие и отображение панелей действий при помощи кнопок настраиваемой вкладки

1. В **Обозреватель решений** откройте контекстное меню для *MyRibbon. CS* или *MyRibbon. vb* и выберите пункт **Просмотреть код**.

2. Добавьте следующий код в начало класса `MyRibbon`. Данный код создает два объекта панелей действий.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet1":::

3. Замените метод `MyRibbon_Load` приведенным ниже кодом. Данный код добавляет объекты панелей действий в коллекцию панелей действий <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> и скрывает объекты. Кроме того, код Visual C# присоединяет делегаты к нескольким событиям элементов управления ленты.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet2":::

4. Добавьте следующие три метода обработчиков событий в класс `MyRibbon`. Эти методы обрабатывают события <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> обеих кнопок и события <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> выключателя. Обработчики событий button1 и button2 отображают соответствующие панели действий. Обработчик событий toggleButton1 отображает и скрывает активную панель действий.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet3":::

## <a name="test-the-custom-tab"></a>Тестирование настраиваемой вкладки
 При запуске проекта запускается Excel, а на ленте отображается вкладка **Мои пользовательские вкладки** . Для отображения и скрытия панелей действий выберите кнопки на **пользовательской вкладке** .

### <a name="to-test-the-custom-tab"></a>Тестирование настраиваемой вкладки

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Перейдите на вкладку **Моя пользовательская** вкладка.

3. В группе **Диспетчер панели пользовательских действий** выберите пункт **отобразить панель действий 1**.

     Откроется панель действия, на которой отображается **Панель действия метки 1**.

4. Выберите пункт **отобразить панель действий 2**.

     Откроется панель действия, на которой отображается **Панель действия метки 2**.

5. Выберите **Скрыть панель действий**.

     Панели действий будут скрыты.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения о настройке пользовательского интерфейса Office см. в следующих разделах:

- Добавление пользовательского интерфейса на основе контекста к настройкам уровня документа. Дополнительные сведения см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md).

- Расширение стандартной или пользовательской формы Microsoft Office Outlook. Дополнительные сведения см. в разделе [Пошаговое руководство. Проектирование области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>См. также статью
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Как приступить к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Как изменить позицию вкладки на ленте](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Как настроить встроенную вкладку](../vsto/how-to-customize-a-built-in-tab.md)
- [Как добавить элементы управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Общие сведения об объектной модели ленты](../vsto/ribbon-object-model-overview.md)
