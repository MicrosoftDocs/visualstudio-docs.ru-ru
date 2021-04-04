---
title: Проверка данных в наборах данных
description: Узнайте, как проверить данные в наборах данных. Проверка данных подразумевает подтверждение того, что значения, вводимые в объекты данных, соответствуют ограничениям в схеме набора данных.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 82cfcf1ce030cfe597c3ae7bfe85c528184c548a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215673"
---
# <a name="validate-data-in-datasets"></a>Проверка данных в наборах данных
Проверка данных — это процесс подтверждения того, что значения, вводимые в объекты данных, соответствуют ограничениям в схеме набора данных. Процесс проверки также подтверждает, что эти значения относятся к правилам, установленным для приложения. Перед отправкой обновлений в основную базу данных рекомендуется проверять данные. Это сокращает число ошибок, а также потенциальное количество циклов обработки между приложением и базой данных.

Вы можете убедиться, что данные, записываемые в набор данных, являются допустимыми, создавая проверки в самом наборе данных. Набор данных может проверять данные независимо от того, как выполняется обновление — непосредственно с помощью элементов управления в форме, внутри компонента или каким-либо другим способом. Поскольку набор данных является частью приложения (в отличие от серверной части базы данных), это логическое место для создания проверки, зависящей от приложения.

Лучшим местом для добавления проверки в приложение является файл разделяемого класса набора данных. В [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] откройте **Конструктор наборов данных** и дважды щелкните столбец или таблицу, для которых необходимо создать проверку. Это действие автоматически создает <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> обработчик событий или.

## <a name="validate-data"></a>Проверка данных
Проверка в наборе данных выполняется следующим образом.

- Путем создания собственной проверки для конкретного приложения, которая может проверять значения в отдельном столбце данных во время внесения изменений. Дополнительные сведения см. [в разделе инструкции. Проверка данных при изменении столбцов](validate-data-in-datasets.md).

- Путем создания собственной проверки для конкретного приложения, которая может проверять данные на значения во время изменения всей строки данных. Дополнительные сведения см. [в разделе как проверить данные при изменении строк](validate-data-in-datasets.md).

- Путем создания ключей, ограничений UNIQUE и т. д. в рамках фактического определения схемы набора данных.

- Путем задания свойств <xref:System.Data.DataColumn> объекта, таких как <xref:System.Data.DataColumn.MaxLength%2A> , <xref:System.Data.DataColumn.AllowDBNull%2A> и <xref:System.Data.DataColumn.Unique%2A> .

При возникновении <xref:System.Data.DataTable> изменений в записи объект вызывает несколько событий:

- <xref:System.Data.DataTable.ColumnChanging>События и <xref:System.Data.DataTable.ColumnChanged> вызываются во время и после каждого изменения в отдельном столбце. <xref:System.Data.DataTable.ColumnChanging>Событие полезно, если требуется проверить изменения в конкретных столбцах. Сведения о предложенном изменении передаются в качестве аргумента для события.
- <xref:System.Data.DataTable.RowChanging>События и <xref:System.Data.DataTable.RowChanged> вызываются во время и после любого изменения в строке. <xref:System.Data.DataTable.RowChanging>Событие является более общим. Оно указывает на то, что в строке происходит изменение, но неизвестно, какой столбец был изменен.

По умолчанию каждое изменение в столбце вызывает четыре события. Первый — это <xref:System.Data.DataTable.ColumnChanging> события и <xref:System.Data.DataTable.ColumnChanged> для конкретного изменяемого столбца. Далее приводятся <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> события и. При внесении нескольких изменений в строку события будут вызываться для каждого изменения.

> [!NOTE]
> Метод строки данных <xref:System.Data.DataRow.BeginEdit%2A> отключает <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> события и после изменения каждого отдельного столбца. В этом случае событие не возникает до <xref:System.Data.DataRow.EndEdit%2A> вызова метода, когда <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> события и вызываются только один раз. Дополнительные сведения см. в разделе [Отключение ограничений при заполнении набора данных](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

Выбранное событие зависит от того, насколько детализирована проверка. Если важно перехватить ошибку сразу же после изменения столбца, создайте проверку с помощью <xref:System.Data.DataTable.ColumnChanging> события. В противном случае используйте <xref:System.Data.DataTable.RowChanging> событие, которое может привести к перехвату нескольких ошибок одновременно. Кроме того, если данные структурированы таким образом, что значение одного столбца проверяется на основе содержимого другого столбца, выполните проверку во время <xref:System.Data.DataTable.RowChanging> события.

При обновлении записей <xref:System.Data.DataTable> объект создает события, на которые можно реагировать по мере возникновения изменений и после внесения изменений.

Если приложение использует типизированный набор данных, можно создать строго типизированные обработчики событий. При этом добавляются четыре дополнительных типизированных события, для которых можно создавать обработчики: `dataTableNameRowChanging` , `dataTableNameRowChanged` , `dataTableNameRowDeleting` и `dataTableNameRowDeleted` . Эти типизированные обработчики событий передают аргумент, включающий имена столбцов таблицы, которые упрощают запись и чтение кода.

## <a name="data-update-events"></a>События обновления данных

|Событие|Описание|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Значение в столбце изменяется. Событие передает строку и столбец, а также предлагаемое новое значение.|
|<xref:System.Data.DataTable.ColumnChanged>|Значение в столбце изменено. Событие передает строку и столбец, а также предлагаемое значение.|
|<xref:System.Data.DataTable.RowChanging>|Изменения, внесенные в <xref:System.Data.DataRow> объект, скоро будут зафиксированы в наборе данных. Если метод не вызывался <xref:System.Data.DataRow.BeginEdit%2A> , <xref:System.Data.DataTable.RowChanging> событие вызывается для каждого изменения в столбце сразу после <xref:System.Data.DataTable.ColumnChanging> вызова события. При вызове <xref:System.Data.DataRow.BeginEdit%2A> перед внесением изменений <xref:System.Data.DataTable.RowChanging> событие вызывается только при вызове <xref:System.Data.DataRow.EndEdit%2A> метода.<br /><br /> Событие передает строку пользователю, а также значение, показывающее, какой тип действия (изменение, вставка и т. д.) выполняется.|
|<xref:System.Data.DataTable.RowChanged>|Строка была изменена. Событие передает строку пользователю, а также значение, показывающее, какой тип действия (изменение, вставка и т. д.) выполняется.|
|<xref:System.Data.DataTable.RowDeleting>|Удаляется строка. Событие передает строку вам вместе со значением, указывающим, какой тип действия (Delete) выполняется.|
|<xref:System.Data.DataTable.RowDeleted>|Строка была удалена. Событие передает строку вам вместе со значением, указывающим, какой тип действия (Delete) выполняется.|

<xref:System.Data.DataTable.ColumnChanging>События, <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowDeleting> создаются во время процесса обновления. Эти события можно использовать для проверки данных или выполнения других типов обработки. Поскольку обновление обрабатывается во время этих событий, его можно отменить, вызывая исключение, которое предотвращает завершение обновления.

<xref:System.Data.DataTable.ColumnChanged>События, <xref:System.Data.DataTable.RowChanged> и <xref:System.Data.DataTable.RowDeleted> — это события уведомления, возникающие при успешном завершении обновления. Эти события полезны, если требуется выполнить дальнейшие действия на основе успешного обновления.

## <a name="validate-data-during-column-changes"></a>Проверять данные при изменении столбцов

> [!NOTE]
> **Конструктор наборов данных** создает разделяемый класс, в котором логика проверки может быть добавлена в набор данных. Созданный конструктором набор данных не удаляет или не изменяет код в разделяемом классе.

Можно проверить данные, когда значение в столбце данных изменяется в ответ на <xref:System.Data.DataTable.ColumnChanging> событие. При возникновении это событие передает аргумент события ( <xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A> ), который содержит значение, предлагаемое для текущего столбца. Основываясь на содержимом `e.ProposedValue` , вы можете:

- Примите предложенное значение, не выполняя никаких действий.

- Отклоните предложенное значение, установив ошибку столбца ( <xref:System.Data.DataRow.SetColumnError%2A> ) из обработчика событий изменения столбца.

- При необходимости используйте <xref:System.Windows.Forms.ErrorProvider> элемент управления для вывода сообщения об ошибке пользователю. Дополнительную информацию см. в разделе [Компонент ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Проверку также можно выполнить во время <xref:System.Data.DataTable.RowChanging> события.

## <a name="validate-data-during-row-changes"></a>Проверка данных при изменении строк
Можно написать код для проверки того, что каждый столбец, который необходимо проверить, содержит данные, соответствующие требованиям приложения. Это можно сделать, установив столбец, чтобы указать, что он содержит ошибку, если предлагаемое значение недопустимо. Следующие примеры задают ошибку столбца, если `Quantity` столбец имеет значение 0 или меньше. Обработчики событий изменения строк должны быть похожи на следующие примеры.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Проверка данных при изменении строки (Visual Basic)

1. Откройте свой набор данных в **Конструкторе наборов данных**. Дополнительные сведения см. [в разделе Пошаговое руководство. Создание набора данных в конструктор наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Дважды щелкните строку заголовка таблицы, которую необходимо проверить. Это действие автоматически создает <xref:System.Data.DataTable.RowChanging> обработчик событий <xref:System.Data.DataTable> в файле разделяемого класса набора данных.

    > [!TIP]
    > Дважды щелкните слева от имени таблицы, чтобы создать обработчик событий изменения строк. Если дважды щелкнуть имя таблицы, его можно изменить.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb" id="Snippet3":::

### <a name="to-validate-data-when-a-row-changes-c"></a>Проверка данных при изменении строки (C#)

1. Откройте свой набор данных в **Конструкторе наборов данных**. Дополнительные сведения см. [в разделе Пошаговое руководство. Создание набора данных в конструктор наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Дважды щелкните строку заголовка таблицы, которую необходимо проверить. Это действие создает файл разделяемого класса для <xref:System.Data.DataTable> .

    > [!NOTE]
    > **Конструктор наборов данных** не создает обработчик событий для <xref:System.Data.DataTable.RowChanging> события автоматически. Необходимо создать метод для обработки <xref:System.Data.DataTable.RowChanging> события и выполнить код для подключения события в методе инициализации таблицы.

3. Скопируйте следующий код в разделяемый класс:

    ```csharp
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>Извлечение измененных строк
Каждая строка в таблице данных имеет <xref:System.Data.DataRow.RowState%2A> свойство, которое отслеживает текущее состояние этой строки с помощью значений в <xref:System.Data.DataRowState> перечислении. Вы можете вернуть измененные строки из набора данных или таблицы данных, вызвав `GetChanges` метод <xref:System.Data.DataSet> или <xref:System.Data.DataTable> . Чтобы убедиться, что изменения существуют до вызова `GetChanges` метода, вызвав <xref:System.Data.DataSet.HasChanges%2A> метод набора данных.

> [!NOTE]
> После фиксации изменений в наборе данных или таблице данных (путем вызова <xref:System.Data.DataSet.AcceptChanges%2A> метода) `GetChanges` метод не возвращает никаких данных. Если приложению необходимо обработать измененные строки, необходимо обработать изменения перед вызовом `AcceptChanges` метода.

Вызов <xref:System.Data.DataSet.GetChanges%2A> метода набора данных или таблицы данных возвращает новый набор данных или таблицу данных, содержащие только измененные записи. Если требуется получить конкретные записи (например, только новые записи или только измененные записи), можно передать значение из <xref:System.Data.DataRowState> перечисления в качестве параметра в `GetChanges` метод.

Используйте <xref:System.Data.DataRowVersion> перечисление для доступа к разным версиям строки (например, исходным значениям, которые были в строке до ее обработки).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Получение всех измененных записей из набора данных

- Вызовите <xref:System.Data.DataSet.GetChanges%2A> метод набора данных.

     В следующем примере создается новый набор данных `changedRecords` с именем и заполняется всеми измененными записями из другого набора данных с именем `dataSet1` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet14":::

### <a name="to-get-all-changed-records-from-a-data-table"></a>Получение всех измененных записей из таблицы данных

- Вызовите <xref:System.Data.DataTable.GetChanges%2A> метод объекта DataTable.

     В следующем примере создается новая таблица данных с именем `changedRecordsTable` и заполняется всеми измененными записями из другой таблицы данных с именем `dataTable1` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet15":::

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Получение всех записей, имеющих определенное состояние строки

- Вызовите `GetChanges` метод набора данных или таблицы данных и передайте <xref:System.Data.DataRowState> значение перечисления в качестве аргумента.

     В следующем примере показано, как создать новый набор данных `addedRecords` с именем и заполнить его только записями, добавленным в `dataSet1` набор данных.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet16":::

     В следующем примере показано, как вернуть все записи, которые были недавно добавлены в `Customers` таблицу:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet17":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet17":::

## <a name="access-the-original-version-of-a-datarow"></a>Доступ к исходной версии DataRow
При внесении изменений в строки данных набор данных будет хранить как исходные ( <xref:System.Data.DataRowVersion.Original> ), так и новые ( <xref:System.Data.DataRowVersion.Current> ) версии строки. Например, перед вызовом `AcceptChanges` метода приложение может получить доступ к различным версиям записи (как определено в <xref:System.Data.DataRowVersion> перечислении) и соответствующим образом обработать изменения.

> [!NOTE]
> Разные версии строки существуют только после редактирования и до `AcceptChanges` вызова метода. После `AcceptChanges` вызова метода текущая и исходная версии будут одинаковыми.

Передача <xref:System.Data.DataRowVersion> значения вместе с индексом столбца (или именем столбца в виде строки) возвращает значение из конкретной версии строки этого столбца. Измененный столбец определяется во время <xref:System.Data.DataTable.ColumnChanging> событий и <xref:System.Data.DataTable.ColumnChanged> . Это хороший момент для проверки различных версий строк в целях тестирования. Однако при наличии временно приостановленных ограничений эти события не будут вызываться, и необходимо будет программно определять, какие столбцы были изменены. Для этого можно выполнить итерацию по <xref:System.Data.DataTable.Columns%2A> коллекции и сравнить различные <xref:System.Data.DataRowVersion> значения.

### <a name="to-get-the-original-version-of-a-record"></a>Получение исходной версии записи

- Получите доступ к значению столбца, передав в <xref:System.Data.DataRowVersion> строку, которую необходимо вернуть.

     В следующем примере показано, как использовать <xref:System.Data.DataRowVersion> значение для получения исходного значения `CompanyName` поля в <xref:System.Data.DataRow> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet21":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet21":::

## <a name="access-the-current-version-of-a-datarow"></a>Доступ к текущей версии DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Получение текущей версии записи

- Получите доступ к значению столбца, а затем добавьте в индекс параметр, указывающий, какую версию строки нужно вернуть.

     В следующем примере показано, как использовать <xref:System.Data.DataRowVersion> значение для получения текущего значения `CompanyName` поля в <xref:System.Data.DataRow> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet22":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet22":::

## <a name="see-also"></a>См. также раздел

- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Как проверить данные в элементе управления Windows Forms DataGridView](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Как отображать значки ошибок для проверки формы с помощью компонента Windows Forms ErrorProvider](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
