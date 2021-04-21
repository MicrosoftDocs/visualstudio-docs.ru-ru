---
title: Пошаговое руководство. Привязка данных к элементам управления в области действий Word
description: Привязка данных к элементам управления на панели действий в Microsoft Word. Элементы управления показывают отношение «Основной/подробности» между таблицами в базе данных SQL Server.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d94891520695117c7a395f81feda81e52f909fe6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824501"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Пошаговое руководство. Привязка данных к элементам управления в области действий Word
  В этом пошаговом руководстве демонстрируется привязка данных к элементам управления на панели действий в Word. Элементы управления показывают отношение «Основной/подробности» между таблицами в базе данных SQL Server.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- Создание панели действий с элементами управления Windows Forms, привязанными к данным.

- Использование связи "основной/подробности" для отображения данных в элементах управления.

- Отображение области действий при открытии приложения.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Доступ к серверу с помощью образца базы данных Northwind SQL Server.

- Разрешения на чтение и запись в базу данных SQL Server.

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание документа Word.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект документа Word с именем **Моя панель действий Word**. В мастере выберите **создать новый документ**.

     Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новый документ Word в конструкторе и добавит в **Обозреватель решений** проект **панели действий My Word** .

## <a name="add-controls-to-the-actions-pane"></a>Добавление элементов управления на панель «действия»
 Для этого пошагового руководства необходим элемент управления панели действий, содержащий элементы управления Windows Forms с привязкой к данным. Добавьте в проект источник данных, а затем перетащите элементы управления из окна **Источники данных** в элемент управления панель действий.

### <a name="to-add-an-actions-pane-control"></a>Добавление элемента управления панели действий

1. Выберите проект **области действий "мои слова** " в **Обозреватель решений**.

2. В меню **Проект** выберите **Добавить новый элемент**.

3. В диалоговом окне **Добавление нового элемента** выберите **элемент Панель действий**, назовите его **актионсконтрол** и нажмите кнопку **Добавить**.

### <a name="to-add-a-data-source-to-the-project"></a>Добавление источника данных в проект

1. Если окно **Источники данных** не отображается, отобразите его с помощью команды **Просмотреть**  >  **другие**  >  **Источники данных** Windows в строке меню.

   > [!NOTE]
   > Если пункт **Показывать источники данных** недоступен, щелкните документ Word, а затем снова проверьте.

2. Щелкните **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

3. Выберите **база данных** и нажмите кнопку **Далее**.

4. Выберите подключение данных к образцу базы данных Northwind SQL Server или добавьте новое соединение с помощью кнопки **создать подключение** .

5. Щелкните **Далее**.

6. Снимите флажок сохранить соединение, если он установлен, а затем нажмите кнопку **Далее**.

7. Разверните узел **таблицы** в окне **объекты базы данных** .

8. Установите флажок рядом с таблицами **поставщики** и **продукты** .

9. Нажмите кнопку **Готово**.

   Мастер добавит таблицу **поставщики** и таблицу **Products** в окно **Источники данных** . Он также добавляет в проект типизированный набор данных, видимый в **Обозреватель решений**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Добавление привязанных к данным Windows Forms элементов управления в элемент управления панели действий

1. В окне **Источники данных** разверните таблицу **поставщики** .

2. Щелкните стрелку раскрывающегося списка в узле **название компании** и выберите **ComboBox**.

3. Перетащите **CompanyName** из окна **Источники данных** в элемент управления панель действий.

     Элемент <xref:System.Windows.Forms.ComboBox> управления создается на панели действий. В то же время в <xref:System.Windows.Forms.BindingSource> `SuppliersBindingSource` <xref:System.Data.DataSet> проект в области компонентов добавляются именованный, адаптер таблицы и объект.

4. Выберите `SuppliersBindingNavigator` в области **компонентов** и нажмите клавишу **Delete**. Вы не будете использовать `SuppliersBindingNavigator` в этом пошаговом руководстве.

    > [!NOTE]
    > При удалении не `SuppliersBindingNavigator` удаляется весь созданный для него код. Этот код можно удалить.

5. Переместите поле со списком, чтобы оно было под меткой, и измените значение свойства **Размер** на **171, 21**.

6. В окне **Источники данных** разверните таблицу **Products** , которая является дочерней по отношению к таблице **поставщики** .

7. Щелкните стрелку раскрывающегося списка на узле **ProductName** и выберите ListBox ( **Список**).

8. Перетащите поле **ProductName** в элемент управления панель действий.

     Элемент <xref:System.Windows.Forms.ListBox> управления создается на панели действий. В то же время в <xref:System.Windows.Forms.BindingSource> `ProductBindingSource` проект в области компонентов добавляются имя и адаптер таблицы.

9. Переместите список, чтобы он наводится под меткой, и измените значение свойства **size** на **171, 95**.

10. Перетащите объект <xref:System.Windows.Forms.Button> из области **элементов** в элемент управления панель действий и поместите его под списком.

11. Щелкните правой кнопкой мыши <xref:System.Windows.Forms.Button> , выберите пункт **свойства** в контекстном меню и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**Вставить**|
    |**Text**|**Вставить**|

12. Измените размер пользовательского элемента управления в соответствии с элементами управления.

## <a name="set-up-the-data-source"></a>Настройка источника данных.
 Чтобы настроить источник данных, добавьте код в <xref:System.Windows.Forms.UserControl.Load> событие элемента управления панели действий, чтобы заполнить элемент управления данными из и <xref:System.Data.DataTable> задать <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> Свойства и для каждого элемента управления.

### <a name="to-load-the-control-with-data"></a>Загрузка элемента управления с данными

1. В <xref:System.Windows.Forms.UserControl.Load> обработчике событий `ActionsControl` класса добавьте следующий код.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet1":::

2. В C# необходимо присоединить обработчик событий к <xref:System.Windows.Forms.UserControl.Load> событию. Этот код можно поместить в `ActionsControl` конструктор после вызова метода `InitializeComponent` . Дополнительные сведения о создании обработчиков событий см. в разделе [инструкции. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet33":::

### <a name="to-set-data-binding-properties-of-the-controls"></a>Задание свойств привязки данных элементов управления

1. Выберите элемент управления `CompanyNameComboBox`.

2. В окне **Свойства** нажмите кнопку справа от свойства **DataSource** и выберите **супплиерсбиндингсаурце**.

3. Нажмите кнопку справа от свойства **DisplayMember** и выберите **CompanyName**.

4. Разверните свойство **databindingss** , нажмите кнопку справа от свойства **Text** и выберите **нет**.

5. Выберите элемент управления `ProductNameListBox`.

6. В окне **Свойства** нажмите кнопку справа от свойства **DataSource** и выберите **продуктсбиндингсаурце**.

7. Нажмите кнопку справа от свойства **DisplayMember** и выберите **ProductName**.

8. Разверните свойство **databindingss** , нажмите кнопку справа от свойства **SelectedValue** и выберите **нет**.

## <a name="add-a-method-to-insert-data-into-a-table"></a>Добавление метода для вставки данных в таблицу
 Следующая задача — чтение данных из связанных элементов управления и заполнение таблицы в документе Word. Сначала создайте процедуру для форматирования заголовков в таблице, а затем добавьте `AddData` метод для создания и форматирования таблицы Word.

### <a name="to-format-the-table-headings"></a>Форматирование заголовков таблицы

1. В `ActionsControl` классе создайте метод для форматирования заголовков таблицы.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet2":::

### <a name="to-create-the-table"></a>Создание таблицы

1. В `ActionsControl` классе напишите метод, который создаст таблицу, если она еще не существует, и добавить данные из панели действия в таблицу.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet3":::

### <a name="to-insert-text-into-a-word-table"></a>Вставка текста в таблицу Word

1. Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий кнопки **вставки** .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet4":::

2. В C# необходимо создать обработчик событий для <xref:System.Windows.Forms.Control.Click> события кнопки.  Этот код можно поместить в <xref:System.Windows.Forms.UserControl.Load> обработчик событий `ActionsControl` класса.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet5":::

## <a name="show-the-actions-pane"></a>Отображение панели "действия"
 Панель действий отображается после добавления к ней элементов управления.

### <a name="to-show-the-actions-pane"></a>Отображение панели «действия»

1. В **Обозреватель решений** щелкните правой кнопкой мыши **ThisDocument. vb** или **ThisDocument. CS** и выберите в контекстном меню пункт **Просмотреть код** .

2. Создайте новый экземпляр элемента управления в верхней части `ThisDocument` класса, чтобы он выглядел так, как показано в следующем примере.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet6":::

3. Добавьте код в <xref:Microsoft.Office.Tools.Word.Document.Startup> обработчик событий класса, `ThisDocument` чтобы он выглядел как в следующем примере.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet7":::

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать документ, чтобы убедиться, что панель действий отображается при открытии документа. Проверьте отношение "основной/подробности" в элементах управления на панели "действия" и убедитесь, что данные заполнены в таблице Word при нажатии кнопки " **Вставить** ".

### <a name="to-test-your-document"></a>Проверка документа

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Убедитесь, что панель действия видна.

3. Выберите компанию в поле со списком и убедитесь, что элементы в списке **продукты** изменяются.

4. Выберите продукт, нажмите кнопку **Вставить** на панели действия и убедитесь, что сведения о продукте добавлены в таблицу в Word.

5. Вставка дополнительных продуктов из различных компаний.

## <a name="next-steps"></a>Дальнейшие действия
 В этом пошаговом руководстве показаны основные сведения о привязке данных к элементам управления на панели действий в Word. Ниже приводятся некоторые из возможных последующих задач.

- Привязка данных к элементам управления в Excel. Дополнительные сведения см. [в разделе Пошаговое руководство. Привязка данных к элементам управления на панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

- Развертывание проекта. Дополнительные сведения см. в статье [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>См. также статью
- [Обзор панели действий](../vsto/actions-pane-overview.md)
- [Как добавить панель действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
