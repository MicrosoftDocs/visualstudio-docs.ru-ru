---
title: Сохранение данных с помощью методов DBDirect адаптера таблицы TableAdapter
description: В этом пошаговом руководстве инструкции SQL выполняются непосредственно в базе данных с помощью методов DBDirect адаптера таблицы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4539d269f27cd09f96c8633d0efd603708f1f2e1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215777"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Сохранение данных с помощью методов DBDirect адаптера таблицы TableAdapter

В этом пошаговом руководстве содержатся подробные инструкции по выполнению инструкций SQL непосредственно в базе данных с помощью методов DBDirect адаптера таблицы. Методы DBDirect адаптера таблицы обеспечивают точный контроль над обновлениями базы данных. Их можно использовать для выполнения определенных инструкций SQL и хранимых процедур, вызывая отдельные `Insert` `Update` методы, и в `Delete` соответствии с требованиями приложения (в отличие от перегруженного `Update` метода, который ВЫПОЛНЯЕТ инструкции UPDATE, INSERT и DELETE в одном вызове).

В этом пошаговом руководстве описаны следующие процедуры.

- Создайте новое **приложение Windows Forms**.

- Создание и настройка набора данных с помощью [мастера настройки источника данных](../data-tools/media/data-source-configuration-wizard.png).

- Выбор элемента управления, создаваемого на форме при перетаскивании элементов из окна **Источники данных**. Дополнительные сведения см. в разделе [Установка элемента управления, создаваемого при перетаскивании из окна Источники данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Создание формы с привязкой к данным посредством перетаскивания элементов из окна **Источники данных** на форму.

- Добавьте методы для прямого доступа к базе данных и выполнения операций вставки, обновления и удаления.

## <a name="prerequisites"></a>Предварительные требования

В этом пошаговом руководстве используется SQL Server Express LocalDB и образец базы данных Northwind.

1. Если у вас нет SQL Server Express LocalDB, установите его на [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)или с помощью **Visual Studio Installer**. В **Visual Studio Installer** можно установить SQL Server Express LocalDB как часть рабочей нагрузки **хранения и обработки данных** или как отдельный компонент.

2. Установите учебную базу данных Northwind, выполнив следующие действия.

    1. В Visual Studio откройте окно **Обозреватель объектов SQL Server** . (Обозреватель объектов SQL Server устанавливается как часть рабочей нагрузки **хранения и обработки данных** в Visual Studio Installer.) Разверните узел **SQL Server** . Щелкните правой кнопкой мыши экземпляр LocalDB и выберите **создать запрос**.

       Откроется окно редактора запросов.

    2. Скопируйте [скрипт Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных Northwind с нуля и заполняет ее данными.

    3. Вставьте скрипт T-SQL в редактор запросов, а затем нажмите кнопку **выполнить** .

       По истечении короткого времени выполнение запроса завершается и создается база данных Northwind.

## <a name="create-a-windows-forms-application"></a>Создание приложения Windows Forms

Первым шагом является создание **приложения Windows Forms**.

1. В Visual Studio в меню **Файл** выберите пункты **Создать** > **Проект**.

2. В левой области разверните элемент **Visual C#** или **Visual Basic** , а затем выберите пункт **Windows Desktop**.

3. В средней области выберите тип проекта **приложения Windows Forms** .

4. Назовите проект **таблеадаптердбдиректмесодсвалксраугх** и нажмите кнопку **ОК**.

     Создается проект **TableAdapterDbDirectMethodsWalkthrough**, который добавляется в **Обозреватель решений**.

## <a name="create-a-data-source-from-your-database"></a>Создание источника данных из базы данных

В этом шаге **Мастер настройки источника данных** используется для создания источника данных на основе таблицы `Region` в учебной базе данных "Борей". Для создания подключения необходимо иметь доступ к учебной базе данных "Борей". Сведения о настройке образца базы данных Northwind см. в разделе [как установить образцы баз](../data-tools/installing-database-systems-tools-and-samples.md)данных.

### <a name="to-create-the-data-source"></a>Создание источника данных

1. В меню **Данные** выберите пункт **Показать источники данных**.

   Открывается окно **Источники данных**.

2. В окне **Источники данных** выберите **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

3. На экране **Выбор типа источника данных** выберите **база данных**, а затем нажмите кнопку **Далее**.

4. На экране **Выбор подключения к данным** выполните одно из следующих действий.

    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

         -или-

    - Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение**.

5. Если базе данных требуется пароль, выберите параметр, чтобы включить конфиденциальные данные, а затем нажмите кнопку **Далее**.

6. На экране **сохранить строку подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

7. На экране **Выбор объектов базы данных** разверните узел **таблицы** .

8. Выберите `Region` таблицу и нажмите кнопку **Готово**.

     Объект **NorthwindDataSet** добавляется в проект, и таблица `Region` отображается в окне **Источники данных**.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Добавление элементов управления в форму для вывода данных

Создайте элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.

Чтобы создать элементы управления с привязкой к данным в форме Windows Forms, перетащите узел основной **области** из окна **Источники данных** на форму.

На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. [](../data-tools/dataset-tools-in-visual-studio.md) `RegionTableAdapter` <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> В области компонентов появятся NorthwindDataSet,, и.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Порядок добавления кнопок, вызывающих отдельные методы DbDirect адаптера таблицы

1. Перетащите три элемента управления <xref:System.Windows.Forms.Button> из **области элементов** на **Form1** (под **RegionDataGridView**).

2. Задайте следующие свойства **Имя** и **Текст** для каждой из кнопок.

    |Имя|текст|
    |----------|----------|
    |`InsertButton`|**Вставить**|
    |`UpdateButton`|**Обновление**|
    |`DeleteButton`|**Удалить**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Добавление кода для вставки новых записей в базу данных

1. Выберите **инсертбуттон** , чтобы создать обработчик событий для события Click и открыть форму в редакторе кода.

2. Замените обработчик событий `InsertButton_Click` следующим кодом:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet1":::

### <a name="to-add-code-to-update-records-in-the-database"></a>Добавление кода для обновления записей в базе данных

1. Дважды щелкните **UpdateButton**, чтобы создать обработчик событий для события щелчка кнопкой мыши и открыть форму в редакторе кода.

2. Замените обработчик событий `UpdateButton_Click` следующим кодом:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet2":::

### <a name="to-add-code-to-delete-records-from-the-database"></a>Добавление кода для удаления записей из базы данных

1. Выберите **делетебуттон** , чтобы создать обработчик событий для события Click и открыть форму в редакторе кода.

2. Замените обработчик событий `DeleteButton_Click` следующим кодом:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet3":::

## <a name="run-the-application"></a>Выполнение приложения

- Нажмите **клавишу F5** , чтобы запустить приложение.

- Нажмите кнопку **Вставить** и убедитесь, что новая запись появилась в сетке.

- Нажмите кнопку **Обновить** и убедитесь, что запись обновлена в сетке.

- Нажмите кнопку **Удалить** и убедитесь, что запись удалена из сетки.

## <a name="next-steps"></a>Дальнейшие действия

В зависимости от требований приложения существует несколько шагов, которые, возможно, потребуется выполнить после создания формы с привязкой к данным. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.

- Добавление функциональности поиска в форму.

- Добавление дополнительных таблиц в набор данных посредством выбора элемента **Настроить набор данных с помощью мастера** в окне **Источники данных**. Вы можете добавить элементы управления, отображающие связанные данные, перетащив связанные узлы на форму. Дополнительные сведения см. [в разделе связи в наборах данных](relationships-in-datasets.md).

## <a name="see-also"></a>См. также раздел

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
