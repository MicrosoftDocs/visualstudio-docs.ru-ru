---
title: Привязка данных пользовательские объекты
description: Привязка объектов в качестве источников данных в Visual Studio. Используйте средства времени разработки для работы с пользовательскими объектами в качестве источника данных в приложении.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 140700615759404f02109c4506f4c27d083a74b1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215543"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Привязка объектов в качестве источников данных в Visual Studio

Visual Studio предоставляет средства времени разработки для работы с пользовательскими объектами в качестве источника данных в приложении. Если требуется хранить данные из базы данных в объекте, привязанном к элементам управления пользовательского интерфейса, рекомендуется использовать Entity Framework для создания класса или классов. Entity Framework автоматически создает весь стандартный код отслеживания изменений, что означает, что любые изменения локальных объектов автоматически сохраняются в базе данных при вызове метода AcceptChanges для объекта DbSet. Дополнительные сведения см. в [документации по Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Подходы к привязке объектов в этой статье следует рассматривать, только если приложение уже основано на наборах данных. Эти подходы также можно использовать, если вы уже знакомы с наборами данных, и данные, которые вы будете обрабатывать, являются табличными и слишком сложными или слишком большими. Еще более простой пример, включающий загрузку данных непосредственно в объекты с помощью DataReader и ручное обновление пользовательского интерфейса без привязки данных, см. в разделе [Создание простого приложения для данных с помощью ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Требования к объектам

Единственным требованием для пользовательских объектов, работающих с инструментами проектирования данных в Visual Studio, является то, что объекту требуется по крайней мере одно общее свойство.

Как правило, пользовательские объекты не нуждаются в каких-либо конкретных интерфейсах, конструкторах или атрибутах, которые могут служить источником данных для приложения. Однако, если нужно перетащить объект из окна **Источники данных** в область конструктора для создания элемента управления с привязкой к данным, а если объект реализует <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> интерфейс или, то объект должен иметь конструктор по умолчанию. В противном случае Visual Studio не сможет создать экземпляр объекта источника данных и выведет сообщение об ошибке при перетаскивании элемента в область конструктора.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Примеры использования пользовательских объектов в качестве источников данных

Хотя существует бесчисленные способы реализации логики приложения при работе с объектами в качестве источника данных, для баз данных SQL существует несколько стандартных операций, которые можно упростить с помощью созданных в Visual Studio объектов TableAdapter. На этой странице объясняется, как реализовать эти стандартные процессы с помощью адаптеров таблиц TableAdapter. Он не предназначен для создания пользовательских объектов. Например, вы обычно выполняете следующие стандартные операции независимо от конкретной реализации объектов или логики приложения:

- Загрузка данных в объекты (обычно из базы данных).

- Создание типизированной коллекции объектов.

- Добавление объектов в коллекцию и удаление объектов из коллекции.

- Отображение данных объекта для пользователей в форме.

- Изменение или изменение данных в объекте.

- Сохранение данных из объектов обратно в базу данных.

### <a name="load-data-into-objects"></a>Загрузка данных в объекты

В этом примере данные загружаются в объекты с помощью адаптеров таблиц TableAdapter. По умолчанию адаптеры таблиц создаются с двумя видами методов, которые извлекать данные из базы данных и заполняют таблицы данных.

- `TableAdapter.Fill`Метод заполняет существующую таблицу данных возвращаемыми данными.

- `TableAdapter.GetData`Метод возвращает новую таблицу данных, заполненную данными.

Самым простым способом загрузки пользовательских объектов с данными является вызов `TableAdapter.GetData` метода, перебор коллекции строк в возвращенной таблице данных и заполнение каждого объекта значениями в каждой строке. Можно создать `GetData` метод, возвращающий заполненную таблицу данных для любого запроса, добавленного в TableAdapter.

> [!NOTE]
> Visual Studio называет запросы TableAdapter `Fill` и по `GetData` умолчанию, но эти имена можно изменить на любое допустимое имя метода.

В следующем примере показано, как выполнить перебор строк в таблице данных и заполнить объект данными:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb" id="Snippet4":::

### <a name="create-a-typed-collection-of-objects"></a>Создание типизированной коллекции объектов

Можно создавать классы коллекций для объектов или использовать типизированные коллекции, которые автоматически предоставляются [компонентом BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

При создании пользовательского класса коллекции для объектов мы рекомендуем наследовать от <xref:System.ComponentModel.BindingList%601> . Этот универсальный класс предоставляет функциональные возможности для администрирования коллекции, а также возможность создавать события, отправляющие уведомления в инфраструктуру привязки данных в Windows Forms.

Автоматически созданная коллекция в коллекции <xref:System.Windows.Forms.BindingSource> использует <xref:System.ComponentModel.BindingList%601> для своей типизированной коллекции. Если приложению не требуются дополнительные функции, вы можете поддерживать коллекцию в <xref:System.Windows.Forms.BindingSource> . Дополнительные сведения см. в описании <xref:System.Windows.Forms.BindingSource.List%2A> свойства <xref:System.Windows.Forms.BindingSource> класса.

> [!NOTE]
> Если для вашей коллекции требуются функции, не предоставляемые базовой реализацией <xref:System.ComponentModel.BindingList%601> , следует создать пользовательскую коллекцию, чтобы при необходимости можно было добавить в класс.

В следующем коде показано, как создать класс для строго типизированной коллекции `Order` объектов:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet8":::

### <a name="add-objects-to-a-collection"></a>Добавление объектов в коллекцию

Объекты добавляются в коллекцию путем вызова `Add` метода пользовательского класса коллекции или <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> `Add`Метод предоставляется автоматически для пользовательской коллекции при наследовании от <xref:System.ComponentModel.BindingList%601> .

В следующем коде показано, как добавить объекты в типизированную коллекцию в <xref:System.Windows.Forms.BindingSource> :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet5":::

В следующем коде показано, как добавить объекты в типизированную коллекцию, наследующую от <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> В этом примере `Orders` коллекция является свойством `Customer` объекта.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet6":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet6":::

### <a name="remove-objects-from-a-collection"></a>Удаление объектов из коллекции

Объекты из коллекции удаляются путем вызова `Remove` `RemoveAt` метода или пользовательского класса коллекции или <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> `Remove`Методы и `RemoveAt` автоматически предоставляются для пользовательской коллекции при наследовании от <xref:System.ComponentModel.BindingList%601> .

В следующем коде показано, как выполнять обнаружение и удаление объектов из типизированной коллекции в <xref:System.Windows.Forms.BindingSource> с помощью <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> метода:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet7":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet7":::

### <a name="display-object-data-to-users"></a>Отображение данных объекта для пользователей

Чтобы отобразить данные в объектах для пользователей, создайте источник данных объекта с помощью мастера **настройки источника данных** , а затем перетащите весь объект или отдельные свойства в форму из окна **Источники данных** .

### <a name="modify-the-data-in-objects"></a>Изменение данных в объектах

Чтобы изменить данные в пользовательских объектах, привязанных к Windows Forms элементам управления, просто измените данные в связанном элементе управления (или непосредственно в свойствах объекта). Архитектура привязки данных обновляет данные в объекте.

Если приложение требует отслеживания изменений и отката предложенных изменений их исходных значений, необходимо реализовать эту функциональность в объектной модели. Примеры того, как таблицы данных отслеживают предлагаемые изменения, см <xref:System.Data.DataRowState> . в статьях, <xref:System.Data.DataSet.HasChanges%2A> и <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="save-data-in-objects-back-to-the-database"></a>Сохранение данных в объектах обратно в базу данных

Сохраните данные обратно в базу данных, передав значения из объекта в методы DBDirect адаптера таблицы.

Visual Studio создает методы DBDirect, которые могут выполняться непосредственно в базе данных. Для этих методов не требуется набор данных или объекты DataTable.

|Метод TableAdapter DBDirect|Описание|
| - |-----------------|
|`TableAdapter.Insert`|Добавляет новые записи в базу данных, позволяя передавать отдельные значения столбцов в качестве параметров метода.|
|`TableAdapter.Update`|Обновляет существующие записи в базе данных. Метод Update принимает исходные и новые значения столбцов в качестве параметров метода. Исходные значения используются для нахождение исходной записи, а для обновления этой записи используются новые значения.<br /><br /> `TableAdapter.Update`Метод также используется для согласования изменений в наборе данных с базой данных с помощью <xref:System.Data.DataSet> массива,, <xref:System.Data.DataTable> <xref:System.Data.DataRow> или из <xref:System.Data.DataRow> s в качестве параметров метода.|
|`TableAdapter.Delete`|Удаляет существующие записи из базы данных на основе значений исходных столбцов, переданных в качестве параметров метода.|

Чтобы сохранить данные из коллекции объектов, пройдите по коллекции объектов (например, с помощью цикла For-Next). Отправьте значения для каждого объекта в базу данных с помощью методов DBDirect адаптера таблицы.

В следующем примере показано, как использовать `TableAdapter.Insert` метод DBDirect для добавления нового клиента непосредственно в базу данных:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="see-also"></a>См. также раздел

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
