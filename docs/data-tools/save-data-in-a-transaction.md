---
title: Пошаговое руководство. Сохранение данных в транзакции
description: В этом пошаговом руководстве показано, как сохранить данные в транзакции с помощью пространства имен System. Transactions в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a5933a8713a1d4b371672be83a56d0323f5043b9
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216089"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Пошаговое руководство. Сохранение данных в транзакции

В этом пошаговом руководстве показано, как сохранить данные в транзакции с помощью <xref:System.Transactions> пространства имен. В этом пошаговом руководстве вы создадите приложение Windows Forms. Мастер настройки источника данных используется для создания набора данных для двух таблиц в образце базы данных Northwind. Вы добавите элементы управления с привязкой к данным в форму Windows Forms, и измените код для кнопки "Сохранить" BindingNavigator, чтобы обновить базу данных в TransactionScope.

## <a name="prerequisites"></a>Предварительные требования

В этом пошаговом руководстве используется SQL Server Express LocalDB и образец базы данных Northwind.

1. Если у вас нет SQL Server Express LocalDB, установите его на [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)или с помощью **Visual Studio Installer**. В Visual Studio Installer SQL Server Express LocalDB можно установить как часть рабочей нагрузки **разработки классических приложений .NET** или как отдельный компонент.

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

4. Назовите проект **савингдатаинатрансактионвалксраугх** и нажмите кнопку **ОК**.

     Создается проект **SavingDataInATransactionWalkthrough**, который добавляется в **Обозреватель решений**.

## <a name="create-a-database-data-source"></a>Создание источника данных базы данных

На этом шаге **Мастер настройки источника данных** используется для создания источника данных на основе `Customers` `Orders` таблиц и в образце базы данных Northwind.

1. Чтобы открыть окно **Источники данных** , в меню **данные** выберите команду **отобразить источники данных**.

2. В окне **Источники данных** выберите **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

3. На экране **Выбор типа источника данных** выберите **база данных**, а затем нажмите кнопку **Далее**.

4. На экране **Выбор подключения к данным** выполните одно из следующих действий.

    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

         -или-

    - Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение** и создайте подключение к базе данных "Борей".

5. Если базе данных требуется пароль, выберите параметр, чтобы включить конфиденциальные данные, а затем нажмите кнопку **Далее**.

6. На экране **сохранить строку подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

7. На экране **Выбор объектов базы данных** разверните узел **таблицы** .

8. Выберите `Customers` таблицы и и `Orders` нажмите кнопку **Готово**.

     Объект **NorthwindDataSet** добавляется в проект, и таблицы `Customers` и `Orders` отображаются в окне **Источники данных**.

## <a name="add-controls-to-the-form"></a>Добавление элементов управления на форму

Вы можете создавать элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.

1. В окне **Источники данных** разверните узел **Клиенты** .

2. Перетащите главный узел **Customers** из окна **Источники данных** на форму **Form1**.

   На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. [](../data-tools/dataset-tools-in-visual-studio.md) `CustomersTableAdapter` <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> В области компонентов появятся NorthwindDataSet,, и.

3. Перетащите связанный узел **Orders** (не главный узел **заказы** , а связанный узел дочерней таблицы ниже столбца **факса** ) в форму под элементом **кустомерсдатагридвиев**.

   На форме появляется <xref:System.Windows.Forms.DataGridView>. `OrdersTableAdapter`И <xref:System.Windows.Forms.BindingSource> появятся в области компонентов.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Добавление ссылки на сборку System. Transactions

Транзакции используют пространство имен <xref:System.Transactions>. Ссылка проекта на сборку system.transactions не добавляется по умолчанию, поэтому вам нужно добавить ее вручную.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Порядок добавления ссылки на DLL-файл System.Transactions

1. В меню **Проект** выберите пункт **Добавить ссылку**.

2. Выберите **System. Transactions** (на вкладке **.NET** ) и нажмите кнопку **ОК**.

     Ссылка на **System.Transactions** добавляется в проект.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Изменение кода в кнопке Савеитем BindingNavigator

Для первой таблицы, помещенной в форму, код добавляется по умолчанию в `click` событие кнопки сохранить в <xref:System.Windows.Forms.BindingNavigator> . Для обновления дополнительных таблиц вам необходимо добавить такой код вручную. В этом пошаговом руководстве мы выполним рефакторинг существующего кода для сохранения из обработчика событий нажатия кнопки Save. Кроме того, мы создадим еще несколько методов для предоставления конкретных функций обновления в зависимости от того, нужно ли добавить или удалить строку.

### <a name="to-modify-the-auto-generated-save-code"></a>Изменение автоматически сформированного кода сохранения

1. Нажмите кнопку **Save (сохранить** ) на **CustomersBindingNavigator** (кнопка с значком гибкого диска).

2. Замените метод `CustomersBindingNavigatorSaveItem_Click` следующим кодом:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet4":::

При согласовании изменений связанных данных применяется следующий порядок.

- Удаляет дочерние записи. (В этом случае удалите записи из `Orders` таблицы.)

- Удаление родительских записей. (В этом случае удалите записи из `Customers` таблицы.)

- Вставка родительских записей. (В этом случае вставьте записи в `Customers` таблицу.)

- Вставка дочерних записей. (В этом случае вставьте записи в `Orders` таблицу.)

### <a name="to-delete-existing-orders"></a>Удаление существующих заказов

- Добавьте следующий метод `DeleteOrders` в **Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet5":::

### <a name="to-delete-existing-customers"></a>Удаление существующих клиентов

- Добавьте следующий метод `DeleteCustomers` в **Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet6":::

### <a name="to-add-new-customers"></a>Добавление новых клиентов

- Добавьте следующий метод `AddNewCustomers` в **Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet7":::

### <a name="to-add-new-orders"></a>Добавление новых заказов

- Добавьте следующий метод `AddNewOrders` в **Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet8":::

## <a name="run-the-application"></a>Выполнение приложения

Нажмите клавишу **F5** для запуска приложения.

## <a name="see-also"></a>См. также раздел

- [Практическое руководство. Сохранение данных с помощью транзакции](../data-tools/save-data-by-using-a-transaction.md)
- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
