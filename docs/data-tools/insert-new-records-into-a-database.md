---
title: Вставка новых записей в базу данных
description: Вставка новых записей в базу данных с помощью метода TableAdapter. Update, одного из методов DBDirect TableAdapter или командных объектов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 6e1046dfd114e4cad69445b8f4e1432c03aac0e5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216466"
---
# <a name="insert-new-records-into-a-database"></a>Вставка новых записей в базу данных

Чтобы вставить новые записи в базу данных, можно использовать `TableAdapter.Update` метод или один из методов DBDirect адаптера таблицы (в частности, `TableAdapter.Insert` метод). Дополнительные сведения см. в разделе [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Если приложение не использует адаптеры таблиц, можно использовать объекты команд (например,  <xref:System.Data.SqlClient.SqlCommand> ) для вставки новых записей в базу данных.

Если приложение использует наборы данных для хранения, используйте `TableAdapter.Update` метод. `Update`Метод отправляет все изменения (обновления, вставки и удаления) в базу данных.

Если приложение использует объекты для хранения данных или требуется более точный контроль над созданием новых записей в базе данных, используйте `TableAdapter.Insert` метод.

Если в TableAdapter нет `Insert` метода, это означает, что адаптер таблицы настроен для использования хранимых процедур или его `GenerateDBDirectMethods` свойство имеет значение `false` . Попробуйте задать `GenerateDBDirectMethods` для свойства TableAdapter значение `true` from в **Конструктор наборов данных**, а затем сохраните набор данных. Это приведет к повторному формированию TableAdapter. Если TableAdapter по-прежнему не имеет `Insert` метода, таблица, вероятно, не предоставляет достаточно сведений о схеме для различения отдельных строк (например, в таблице может отсутствовать первичный ключ).

## <a name="insert-new-records-by-using-tableadapters"></a>Вставка новых записей с помощью адаптеров таблиц

Адаптеры таблиц предоставляют различные способы вставки новых записей в базу данных в зависимости от требований приложения.

Если приложение использует наборы данных для хранения, можно просто добавить новые записи в нужный <xref:System.Data.DataTable> набор данных, а затем вызвать `TableAdapter.Update` метод. `TableAdapter.Update`Метод отправляет любые изменения в <xref:System.Data.DataTable> базу данных (включая измененные и удаленные записи).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Вставка новых записей в базу данных с помощью метода TableAdapter. Update

1. Добавьте новые записи в нужное расположение <xref:System.Data.DataTable> , создав новый объект <xref:System.Data.DataRow> и добавив его в <xref:System.Data.DataTable.Rows%2A> коллекцию.

2. После добавления новых строк в <xref:System.Data.DataTable> вызовите `TableAdapter.Update` метод. Можно управлять объемом обновляемых данных, передавая целое число <xref:System.Data.DataSet> , а <xref:System.Data.DataTable> , массив из <xref:System.Data.DataRow> s или один <xref:System.Data.DataRow> .

   В следующем коде показано, как добавить новую запись в, <xref:System.Data.DataTable> а затем вызвать метод, `TableAdapter.Update` чтобы сохранить новую строку в базе данных. (В этом примере используется `Region` Таблица в базе данных Northwind.)

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb" id="Snippet14":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs" id="Snippet14":::

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Вставка новых записей в базу данных с помощью метода TableAdapter. INSERT

Если приложение использует объекты для хранения данных, можно использовать `TableAdapter.Insert` метод для создания новых строк непосредственно в базе данных. `Insert`Метод принимает отдельные значения для каждого столбца в качестве параметров. При вызове метода в базу данных вставляется новая запись с передаваемыми значениями параметров.

- Вызовите метод TableAdapter `Insert` , передав значения для каждого столбца в качестве параметров.

В следующей процедуре показано использование `TableAdapter.Insert` метода для вставки строк. В этом примере данные вставляются в `Region` таблицу базы данных Northwind.

> [!NOTE]
> Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

## <a name="insert-new-records-by-using-command-objects"></a>Вставка новых записей с помощью командных объектов

Новые записи можно вставлять непосредственно в базу данных с помощью командных объектов.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Вставка новых записей в базу данных с помощью командных объектов

- Создайте новый объект Command и задайте его `Connection` `CommandType` свойства, и `CommandText` .

В следующем примере демонстрируется вставка записей в базу данных с помощью командного объекта. Данные вставляются в `Region` таблицу базы данных Northwind.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet16":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet16":::

## <a name="net-security"></a>Безопасность в .NET

Необходимо иметь доступ к базе данных, к которой вы пытаетесь подключиться, а также разрешение на выполнение вставки в нужную таблицу.

## <a name="see-also"></a>См. также раздел

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
