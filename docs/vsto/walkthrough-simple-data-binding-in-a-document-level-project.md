---
title: Пошаговое руководство. Простая привязка данных в проекте уровня документа
description: Изучите основные сведения о привязке данных в проекте уровня документа, а также в том, что одно поле данных в SQL Server базе данных привязано к именованному диапазону в Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 36d4da65a6cd39c53f1f9d8edf4f9d9b1fe46284
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826854"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Пошаговое руководство. Простая привязка данных в проекте уровня документа
  В этом пошаговом руководстве демонстрируются основы привязки данных в проекте уровня документа. Одно поле данных в SQL Server базе данных привязано к именованному диапазону в Microsoft Office Excel. В этом пошаговом руководстве также показано, как добавлять элементы управления, позволяющие прокручивать все записи в таблице.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- Создание источника данных для проекта Excel.

- Добавление элементов управления на лист.

- Прокрутка записей базы данных.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Доступ к серверу с помощью образца базы данных Northwind SQL Server.

- Разрешения на чтение и запись в базу данных SQL Server.

## <a name="create-a-new-project"></a>Создание нового проекта
 На этом шаге вы создадите проект книги Excel.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект книги Excel с именем **Моя простая привязка данных**, используя либо Visual Basic, либо C#. Убедитесь, что выбрано **Создание нового документа** . Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio откроет новую книгу Excel в конструкторе и добавит **простой проект привязки данных** в **Обозреватель решений**.

## <a name="create-the-data-source"></a>Создание источника данных
 С помощью окна **Источники данных** добавьте типизированный набор данных в свой проект.

### <a name="to-create-the-data-source"></a>Создание источника данных

1. Если окно **Источники данных** не отображается, отобразите его с помощью команды **Просмотреть**  >  **другие**  >  **Источники данных** Windows в строке меню.

2. Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

3. Выберите **база данных** и нажмите кнопку **Далее**.

4. Выберите подключение данных к образцу базы данных Northwind SQL Server или добавьте новое соединение с помощью кнопки **создать подключение** .

5. После выбора или создания соединения нажмите кнопку **Далее**.

6. Снимите флажок сохранить соединение, если он установлен, а затем нажмите кнопку **Далее**.

7. Разверните узел **таблицы** в окне **объекты базы данных** .

8. Установите флажок рядом с таблицей **Клиенты** .

9. Нажмите кнопку **Готово**.

   Мастер добавит таблицу **Customers** в окно **Источники данных** . Он также добавляет в проект типизированный набор данных, видимый в **Обозреватель решений**.

## <a name="add-controls-to-the-worksheet"></a>Добавление элементов управления на лист
 В этом пошаговом руководстве на первом листе потребуются два именованных диапазона и четыре кнопки. Сначала добавьте два именованных диапазона из окна **Источники данных** , чтобы они автоматически привязываются к источнику данных. Затем добавьте кнопки из **панели элементов**.

### <a name="to-add-two-named-ranges"></a>Добавление двух именованных диапазонов

1. Убедитесь, что в конструкторе Visual Studio открыта книга *мой простой Binding.xlsxданных* , где отображается **Лист1** .

2. Откройте окно **Источники данных** и разверните узел **Клиенты** .

3. Выберите столбец **CompanyName** и щелкните появившуюся стрелку раскрывающегося списка.

4. Выберите элемент **NamedRange** в раскрывающемся списке и перетащите столбец **CompanyName** в ячейку **a1**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Элемент управления с именем `companyNameNamedRange` создается в ячейке **a1**. В то же время в <xref:System.Windows.Forms.BindingSource> `customersBindingSource` проект добавляются именованный, адаптер таблицы и <xref:System.Data.DataSet> экземпляр. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource> , который, в свою очередь, привязан к <xref:System.Data.DataSet> экземпляру.

5. Выберите столбец **CustomerID** в окне **Источники данных** , а затем щелкните появившуюся стрелку раскрывающегося списка.

6. Щелкните элемент **NamedRange** в раскрывающемся списке, а затем перетащите столбец **CustomerID** в ячейку **B1**.

7. <xref:Microsoft.Office.Tools.Excel.NamedRange> `customerIDNamedRange` В ячейке **B1** создается другой элемент управления с именем, который привязывается к <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Добавление четырех кнопок

1. На вкладке **Общие элементы управления** **панели элементов** добавьте <xref:System.Windows.Forms.Button> элемент управления в ячейку **a3** листа.

    Эта кнопка называется `Button1` .

2. Добавьте еще три кнопки в следующие ячейки в этом порядке, чтобы имена отображались следующим образом:

   |Cell (Ячейка)|(Имя)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   Следующим шагом является добавление текста к кнопкам, а в C# — Добавление обработчиков событий.

## <a name="initialize-the-controls"></a>Инициализация элементов управления
 Задайте текст кнопки и добавьте обработчики событий во время <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> события.

### <a name="to-initialize-the-controls"></a>Инициализация элементов управления

1. В **Обозреватель решений** щелкните правой кнопкой мыши **Лист1. vb** или **Sheet1. CS** и выберите в контекстном меню пункт **Просмотреть код** .

2. Добавьте следующий код в метод, `Sheet1_Startup` чтобы задать текст для каждой кнопки.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet2":::

3. Для только C# добавьте обработчики событий для событий нажатия кнопки в `Sheet1_Startup` метод.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet3":::

   Теперь добавьте код для управления <xref:System.Windows.Forms.Control.Click> событиями кнопок, чтобы пользователь мог просматривать записи.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Добавление кода для включения прокрутки записей
 Добавьте код в <xref:System.Windows.Forms.Control.Click> обработчик событий каждой кнопки, чтобы перемещаться по записям.

### <a name="to-move-to-the-first-record"></a>Переход к первой записи

1. Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> события `Button1` кнопки и добавьте следующий код для перехода к первой записи:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet4":::

### <a name="to-move-to-the-previous-record"></a>Переход к предыдущей записи

1. Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> события `Button2` кнопки и добавьте следующий код, чтобы переместить положение обратно на одну:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet5":::

### <a name="to-move-to-the-next-record"></a>Переход к следующей записи

1. Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> события `Button3` кнопки и добавьте следующий код, чтобы переместить эту точку на одну:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet6":::

### <a name="to-move-to-the-last-record"></a>Переход к последней записи

1. Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> события `Button4` кнопки и добавьте следующий код для перехода к последней записи:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать книгу, чтобы убедиться, что вы можете просматривать записи в базе данных.

### <a name="to-test-your-workbook"></a>Проверка книги

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Убедитесь, что первая запись отображается в ячейках **a1** и **B1**.

3. Нажмите кнопку **>** ( `Button3` ) и убедитесь, что следующая запись отображается в ячейке **a1** и **B1**.

4. Нажмите другие кнопки прокрутки, чтобы убедиться, что запись изменилась ожидаемым образом.

## <a name="next-steps"></a>Дальнейшие действия
 В этом пошаговом руководстве показаны основные принципы привязки именованного диапазона к полю в базе данных. Ниже приводятся некоторые из возможных последующих задач.

- Кэшировать данные, чтобы их можно было использовать в автономном режиме. Дополнительные сведения см. в разделе [как кэшировать данные для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Привязка ячеек к нескольким столбцам в таблице, а не к одному полю. Дополнительные сведения см. [в разделе Пошаговое руководство. сложная привязка данных в проекте уровня документа](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).

- Используйте <xref:System.Windows.Forms.BindingNavigator> элемент управления для прокрутки записей. Дополнительные сведения см. [в разделе Практические руководства. Навигация по данным с помощью элемента управления Windows Forms BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>См. также статью
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Данные в решениях Office](../vsto/data-in-office-solutions.md)
- [Пошаговое руководство. сложная привязка данных в проекте уровня документа](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
