---
title: Наборы данных запросов
description: Общие сведения о наборах данных запросов. Сведения о чувствительности к регистру наборов данных. Поиск определенной строки в таблице данных, поиск строк по значениям столбцов и доступ к связанным записям.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c5f085cae185a48f3d41c6fa4bca5cad7afb46b3
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215803"
---
# <a name="query-datasets"></a>Наборы данных запросов
Для поиска конкретных записей в наборе данных используйте `FindBy` метод в объекте DataTable, напишите собственную инструкцию foreach для циклической обработки коллекции строк таблицы или используйте [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Чувствительность к регистру наборов данных
В наборе данных имена таблиц и столбцов по умолчанию не учитывают регистр, то есть таблица в наборе данных с именем "Customers" также может называться "Customers". Это соответствует соглашениям об именовании во многих базах данных, включая SQL Server. В SQL Server поведение по умолчанию заключается в том, что имена элементов данных не могут отличаться только регистром.

> [!NOTE]
> В отличие от наборов данных, XML-документы чувствительны к регистру, поэтому имена элементов, определенных в схемах, учитывают регистр. Например, протокол схемы позволяет схеме определить таблицу с именем Customers и другую таблицу с именем Customers. Это может привести к конфликтам имен, если для создания класса набора данных используется схема, содержащая элементы, отличающиеся только регистром.

Однако чувствительность к регистру может быть фактором, определяющим способ интерпретации данных в наборе данных. Например, при фильтрации данных в таблице набора данных условия поиска могут возвращать различные результаты в зависимости от того, учитывается ли регистр при сравнении. Можно контролировать чувствительность к регистру при фильтрации, поиске и сортировке, устанавливая свойство набора данных <xref:System.Data.DataSet.CaseSensitive%2A> . Все таблицы в наборе данных по умолчанию наследуют значение этого свойства. (Это свойство можно переопределить для каждой отдельной таблицы, задав <xref:System.Data.DataTable.CaseSensitive%2A> свойство таблицы.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Нахождение определенной строки в таблице данных

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Поиск строки в типизированном наборе данных со значением первичного ключа

- Чтобы указать строку, вызовите строго типизированный `FindBy` метод, который использует первичный ключ таблицы.

     В следующем примере `CustomerID` столбец является первичным ключом `Customers` таблицы. Это означает, что созданный `FindBy` метод имеет значение `FindByCustomerID` . В примере показано, как назначить конкретное значение <xref:System.Data.DataRow> переменной с помощью созданного `FindBy` метода.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet18":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet18":::

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Поиск строки в нетипизированном наборе данных со значением первичного ключа

- Вызовите <xref:System.Data.DataRowCollection.Find%2A> метод <xref:System.Data.DataRowCollection> коллекции, передав первичный ключ в качестве параметра.

     В следующем примере показано, как объявить новую строку с именем `foundRow` и присвоить ей возвращаемое значение <xref:System.Data.DataRowCollection.Find%2A> метода. Если первичный ключ найден, содержимое столбца с индексом 1 отображается в окне сообщения.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet19":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet19":::

## <a name="find-rows-by-column-values"></a>Поиск строк по значениям столбцов

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Поиск строк на основе значений в любом столбце

- Таблицы данных создаются с помощью <xref:System.Data.DataTable.Select%2A> метода, который возвращает массив <xref:System.Data.DataRow> s на основе выражения, переданного <xref:System.Data.DataTable.Select%2A> методу. Дополнительные сведения о создании допустимых выражений см. в разделе "синтаксис выражений" на странице со сведениями о <xref:System.Data.DataColumn.Expression%2A> свойстве.

     В следующем примере показано, как использовать <xref:System.Data.DataTable.Select%2A> метод объекта <xref:System.Data.DataTable> для размещения конкретных строк.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet20":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet20":::

## <a name="access-related-records"></a>Доступ к связанным записям
Если таблицы в наборе данных связаны, <xref:System.Data.DataRelation> объект может сделать связанные записи доступными в другой таблице. Например, можно сделать доступным набор данных, содержащий `Customers` `Orders` таблицы и.

Объект можно использовать <xref:System.Data.DataRelation> для нахождение связанных записей путем вызова <xref:System.Data.DataRow.GetChildRows%2A> метода <xref:System.Data.DataRow> в родительской таблице. Этот метод возвращает массив связанных дочерних записей. Или можно вызвать <xref:System.Data.DataRow.GetParentRow%2A> метод объекта <xref:System.Data.DataRow> в дочерней таблице. Этот метод возвращает один объект <xref:System.Data.DataRow> из родительской таблицы.

На этой странице приведены примеры использования типизированных наборов данных. Дополнительные сведения о переходе по связям в нетипизированных наборах данных см. в разделе [Навигация по связям DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Если вы работаете в Windows Forms приложении и используете функции привязки данных для вывода данных, форма, созданная конструктором, может предоставить достаточно функциональных возможностей для вашего приложения. Дополнительные сведения см. [в разделе Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). В частности, см. раздел [связи в наборах данных](relationships-in-datasets.md).

В следующих примерах кода показано, как перемещаться по связям вверх и вниз в типизированных наборах данных. В примерах кода используются типизированные <xref:System.Data.DataRow> s ( `NorthwindDataSet.OrdersRow` ) и созданные методы финдби *PrimaryKey* ( `FindByCustomerID` ) для определения местоположения нужной строки и возврата связанных записей. Примеры компилируются и выполняются правильно, только если у вас есть:

- Экземпляр набора данных `NorthwindDataSet` с именем и `Customers` таблицей.

- `Orders`Таблица.

- Связь `FK_Orders_Customers` , связанная с двумя таблицами.

Кроме того, обе таблицы должны быть заполнены данными для любых возвращаемых записей.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Получение дочерних записей выбранной родительской записи

- Вызовите <xref:System.Data.DataRow.GetChildRows%2A> метод определенной `Customers` строки данных и возвратите массив строк из `Orders` таблицы:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet6":::

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Возврат родительской записи выбранной дочерней записи

- Вызовите <xref:System.Data.DataRow.GetParentRow%2A> метод определенной `Orders` строки данных и возвратите одну строку из `Customers` таблицы:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>См. также раздел

- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
