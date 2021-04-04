---
title: Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter
description: Получить прямой доступ к базе данных с помощью TableAdapter, используя такие методы, как INSERT, Update и DELETE, для обработки данных непосредственно в базе данных.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 30248632eacde07cfcc94213aeeb75ecac8dcf70
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215920"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter

В дополнение к классам `InsertCommand` , `UpdateCommand` и `DeleteCommand` адаптеры таблиц создаются с помощью методов, которые могут выполняться непосредственно в базе данных. Эти методы ( `TableAdapter.Insert` , `TableAdapter.Update` и) можно вызывать `TableAdapter.Delete` для управления данными непосредственно в базе данных.

Если вы не хотите создавать эти прямые методы, задайте для свойства TableAdapter значение `GenerateDbDirectMethods` `false` в окне **Свойства** . Если какие-либо запросы добавляются в TableAdapter в дополнение к основному запросу TableAdapter, они являются автономными запросами, которые не создают эти `DbDirect` методы.

## <a name="send-commands-directly-to-a-database"></a>Отправка команд непосредственно в базу данных

Вызовите `DbDirect` метод TableAdapter, который выполняет задачу, которую вы пытаетесь выполнить.

### <a name="to-insert-new-records-directly-into-a-database"></a>Вставка новых записей непосредственно в базу данных

- Вызовите метод TableAdapter `Insert` , передав значения для каждого столбца в качестве параметров. В следующей процедуре в `Region` качестве примера используется таблица в базе данных Northwind.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

### <a name="to-update-records-directly-in-a-database"></a>Обновление записей непосредственно в базе данных

- Вызовите метод TableAdapter `Update` , передав новые и исходные значения для каждого столбца в качестве параметров.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet18":::

### <a name="to-delete-records-directly-from-a-database"></a>Удаление записей непосредственно из базы данных

- Вызовите метод TableAdapter `Delete` , передав значения для каждого столбца в качестве параметров `Delete` метода. В следующей процедуре в `Region` качестве примера используется таблица в базе данных Northwind.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet21":::

## <a name="see-also"></a>См. также раздел

- [Заполнение наборов данных с помощью адаптеров таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)
