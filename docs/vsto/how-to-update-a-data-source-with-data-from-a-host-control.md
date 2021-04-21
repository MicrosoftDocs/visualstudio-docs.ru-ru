---
title: Руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения
description: Узнайте, как можно привязать элемент управления ведущего приложения к источнику данных и обновить источник данных изменениями, внесенными в данные в элементе управления.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9aab30b9c2fa363ef68d7d3f70ca05ca6c387a3c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828934"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения
  Вы можете привязать элемент управления ведущего приложения к источнику данных и обновлять источник данных с помощью изменений, внесенных в данные в элементе управления. Этот процесс включает два основных этапа.

1. Обновление источника данных в памяти с использованием измененных данных в элементе управления. Как правило, источник данных в памяти — это <xref:System.Data.DataSet>, <xref:System.Data.DataTable>или какой-либо другой объект данных.

2. Обновление базы данных с использованием измененных данных в источнике данных в памяти. Это применимо только в том случае, если источник данных подключен к внутренней базе данных, например к базе данных SQL Server или Microsoft Office Access.

   Дополнительные сведения о ведущих элементах управления и привязке данных см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md) и [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>Обновление источника данных в памяти
 По умолчанию элементы управления ведущего приложения с поддержкой простой привязки данных (например, элементы управления содержимым в документе Word или элемент управления диапазона на листе Excel) не сохраняют изменения данных в источнике данных в памяти. То есть когда пользователь изменяет значение в элементе управления ведущего приложения и затем выходит из этого элемента управления, новое значение в элементе управления не сохраняется автоматически в источнике данных.

 Для сохранения данных в источник данных можно написать код, который обновляет источник данных в ответ на определенное событие во время выполнения, или можно настроить элемент управления так, чтобы источник данных обновлялся автоматически при изменении значения в элементе управления.

 Нет необходимости сохранять изменения <xref:Microsoft.Office.Tools.Excel.ListObject> в источнике данных в памяти. При привязке элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> к данным элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> автоматически сохраняет изменения в источнике данных в памяти без необходимости написания дополнительного кода.

### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Обновление источника данных в памяти во время выполнения

- Вызовите метод <xref:System.Windows.Forms.Binding.WriteValue%2A> объекта <xref:System.Windows.Forms.Binding> , который привязывает элемент управления к источнику данных.

     В следующем примере выполняется сохранение изменений, внесенных в элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в листе Excel, в источнике данных. В этом примере предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `namedRange1` , свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> которого привязано к полю в источнике данных.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet1":::

### <a name="automatically-update-the-in-memory-data-source"></a>Автоматическое обновление источника данных в памяти
 Вы также можете настроить элемент управления, чтобы он автоматически обновлял источник данных в памяти. В проекте уровня документа это можно сделать с помощью кода или конструктора. В проекте надстройки VSTO необходимо использовать код.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Установка автоматического обновления источника данных в памяти элементом управления с помощью кода

1. Используйте режим System. Windows. Forms. Датасаурцеупдатемоде. OnPropertyChanged <xref:System.Windows.Forms.Binding> объекта, который привязывает элемент управления к источнику данных. Обновлять источник данных можно двумя способами.

   - Чтобы обновить источник данных при проверке элемента управления, присвойте этому свойству значение System. Windows. Forms. Датасаурцеупдатемоде. onvalid.

   - Чтобы обновить источник данных при изменении значения свойства, привязанного к данным элемента управления, присвойте этому свойству значение System. Windows. Forms. Датасаурцеупдатемоде. OnPropertyChanged.

     > [!NOTE]
     > Параметр System. Windows. Forms. Датасаурцеупдатемоде. OnPropertyChanged не применяется к элементам управления ведущего приложения Word, так как Word не предлагает уведомления об изменении документа или элемента управления. Однако этот вариант можно использовать для элементов управления Windows Forms в документах Word.

     В следующем примере элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> настраивается для автоматического обновления источника данных при изменении значения в этом элементе управления. В этом примере предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `namedRange1` , свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> которого привязано к полю в источнике данных.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet19":::

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Установка автоматического обновления источника данных в памяти элементом управления с помощью конструктора

1. В Visual Studio откройте документ Word или книгу Excel в конструкторе.

2. Щелкните элемент управления, который вы хотите настроить для автоматического обновления источника данных.

3. В окне **Свойства** разверните свойство **(DataBindings)** .

4. Рядом со свойством **(дополнительно)** нажмите кнопку с многоточием (![висуалстудиоеллипсесбуттон снимок экрана](../vsto/media/vbellipsesbutton.png "Снимок экрана VisualStudioEllipsesButton")).

5. В диалоговом окне **Форматирование и дополнительная привязка** щелкните раскрывающийся список **Режим обновления источника данных** и выберите одно из следующих значений.

    - Для обновления источника данных при проверке элемента управления выберите значение **OnValidation**.

    - Для обновления источника данных при изменении значения свойства привязки к данным элемента управления выберите значение **OnPropertyChanged**.

        > [!NOTE]
        > Вариант с **OnPropertyChanged** не применяется для элементов управления ведущего приложения Word, поскольку Word не предоставляет уведомления об изменении документа или изменении элемента управления. Однако этот вариант можно использовать для элементов управления Windows Forms в документах Word.

6. Закройте диалоговое окно **Форматирование и дополнительная привязка** .

## <a name="update-the-database"></a>Обновление базы данных
 Если источник данных в памяти связан с базой данных, необходимо обновить базу данных с использованием изменений в источнике данных. Дополнительные сведения об обновлении базы данных см. в разделе [Сохранение данных в базе данных](../data-tools/save-data-back-to-the-database.md)  и [Обновление данных с помощью адаптера таблицы TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .

### <a name="to-update-the-database"></a>Обновление базы данных

1. Вызовите метод <xref:System.Windows.Forms.BindingSource.EndEdit%2A> объекта <xref:System.Windows.Forms.BindingSource> для элемента управления.

     Объект <xref:System.Windows.Forms.BindingSource> создается автоматически при добавлении элемента управления с привязкой к данным в документ или книгу во время разработки. Объект <xref:System.Windows.Forms.BindingSource> подключает элемент управления к типизированному набору данных. Дополнительные сведения см. в разделе [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

     В следующем примере кода предполагается, что проект содержит <xref:System.Windows.Forms.BindingSource> с именем `customersBindingSource`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet20":::

2. Вызовите `Update` метод созданного адаптера TableAdapter в проекте.

     Адаптер таблицы TableAdapter создается автоматически при добавлении элемента управления с привязкой к данным в документ или книгу во время разработки. Адаптер таблицы TableAdapter подключает типизированный набор данных в проекте к базе данных. Дополнительные сведения см. в разделе [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     В следующем примере кода предполагается, что у вас есть соединение с таблицей Customers в базе данных Northwind, а проект содержит TableAdapter с именем `customersTableAdapter` и типизированный набор данных с именем `northwindDataSet` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet21":::

## <a name="see-also"></a>См. также статью
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
- [Обновление данных с помощью адаптера таблицы TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Пошаговое руководство. Прокрутка записей базы данных на листе](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Как заполнить листы данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Как заполнить документы данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Как заполнить документы данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Как заполнить документы данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)
