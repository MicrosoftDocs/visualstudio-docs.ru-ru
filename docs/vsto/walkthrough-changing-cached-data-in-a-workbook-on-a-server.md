---
title: Пошаговое руководство. изменение кэшированных данных в книге на сервере
description: Узнайте, как изменить набор данных, кэшированный в книге Microsoft Excel, не запуская Excel с помощью класса ServerDocument.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f03175abb843abefe5266724890457c795369d63
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824436"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Пошаговое руководство. изменение кэшированных данных в книге на сервере
  В этом пошаговом руководстве показано, как изменить набор данных, кэшированный в Microsoft Office книгу Excel, не запуская Excel с помощью <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- Определение набора данных, содержащего данные из базы данных AdventureWorksLT.

- Создание экземпляров набора данных в проекте книги Excel и проекте консольного приложения.

- Создание объекта <xref:Microsoft.Office.Tools.Excel.ListObject> , привязанного к набору данных в книге, и заполнение <xref:Microsoft.Office.Tools.Excel.ListObject> данными при открытии книги.

- Добавление набора данных в книгу в кэш данных.

- Изменение столбца данных в кэшированном наборе данных путем выполнения кода в консольном приложении без запуска Excel.

  Хотя в этом пошаговом руководстве предполагается, что код выполняется на компьютере разработчика, код, продемонстрированный в этом пошаговом руководстве, можно использовать на сервере, на котором не установлен Excel.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Доступ к выполняющемуся экземпляру Microsoft SQL Server или Microsoft SQL Server Express, к которому присоединен образец базы данных AdventureWorksLT. Базу данных AdventureWorksLT можно скачать из [репозитория SQL Server примеров GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Дополнительные сведения о подключении базы данных см. в следующих разделах:

  - Сведения о присоединении базы данных с помощью SQL Server Management Studio или SQL Server Management Studio Express см. в разделе [как присоединить базу данных (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Сведения о присоединении базы данных с помощью командной строки см. в разделе [как присоединить файл базы данных к SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Создание проекта библиотеки классов, определяющего набор данных
 Чтобы использовать тот же набор данных в проекте книги Excel и в консольном приложении, необходимо определить набор данных в отдельной сборке, на которую ссылаются оба этих проекта. В этом пошаговом руководстве определите набор данных в проекте библиотеки классов.

### <a name="to-create-the-class-library-project"></a>Создание проекта библиотеки классов

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. В области Шаблоны разверните узел **Visual C#** или **Visual Basic**, а затем выберите пункт **Windows**.

4. В списке шаблонов проектов выберите **Библиотека классов**.

5. В поле **имя** введите **AdventureWorksDataset**.

6. Нажмите кнопку **Обзор**, перейдите к папке *%UserProfile%\My Documents* (для Windows XP и более ранних версий) или *%усерпрофиле%\документс* (для Windows Vista), а затем нажмите кнопку **выбрать папку**.

7. Убедитесь, что в диалоговом окне **Новый проект** не установлен флажок **создать каталог для решения** .

8. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет проект **AdventureWorksDataset** в **Обозреватель решений** и открывает файл кода **Class1. CS** или **Class1. vb** .

9. В **Обозреватель решений** щелкните правой кнопкой мыши **Class1. CS** или **Class1. vb** и выберите команду **Удалить**. Этот файл не требуется для этого пошагового руководства.

## <a name="define-a-dataset-in-the-class-library-project"></a>Определение набора данных в проекте библиотеки классов
 Определите типизированный набор данных, содержащий данные из базы данных AdventureWorksLT для SQL Server 2005. Далее в этом пошаговом руководстве вы будете ссылаться на этот набор данных из проекта книги Excel и проекта консольного приложения.

 Набор данных представляет собой *типизированный набор* данных, представляющий данные в таблице Product базы данных AdventureWorksLT. Дополнительные сведения о типизированных наборах данных см. [в разделе Инструменты набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Определение типизированного набора данных в проекте библиотеки классов

1. В **Обозреватель решений** щелкните проект **AdventureWorksDataset** .

2. Если окно **Источники данных** не отображается, отобразите его с помощью команды **Просмотреть**  >  **другие**  >  **Источники данных** Windows в строке меню.

3. Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

4. Щелкните **База данных** и нажмите кнопку **Далее**.

5. Если у вас есть подключение к базе данных AdventureWorksLT, выберите это подключение и нажмите кнопку **Далее**.

    В противном случае нажмите **Создать подключение** и в диалоговом окне **Добавление подключения** создайте новое подключение. Дополнительные сведения см. в разделе [Добавление новых соединений](../data-tools/add-new-connections.md).

6. На странице **Сохранение подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

7. На странице **Выбор объектов базы данных** разверните узел **таблицы** и выберите **продукт (SalesLT)**.

8. Нажмите кнопку **Готово**.

    Файл *AdventureWorksLTDataSet. xsd* добавляется в проект **AdventureWorksDataset** . В этом файле определены следующие элементы:

   - Типизированный набор данных с именем `AdventureWorksLTDataSet`. Этот набор данных представляет содержимое таблицы Product в базе данных AdventureWorksLT.

   - Адаптер таблицы с именем `ProductTableAdapter` . Этот TableAdapter можно использовать для чтения и записи данных в `AdventureWorksLTDataSet` . Дополнительные сведения см. в разделе [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Далее в пошаговом руководстве используются оба эти объекта.

9. В **Обозреватель решений** щелкните правой кнопкой мыши **AdventureWorksDataset** и выберите пункт **Сборка**.

     Убедитесь, что сборка проекта выполняется без ошибок.

## <a name="create-an-excel-workbook-project"></a>Создание проекта книги Excel
 Создайте проект книги Excel для интерфейса для данных. Далее в этом пошаговом руководстве будет создан объект <xref:Microsoft.Office.Tools.Excel.ListObject> , отображающий данные, и в книге будет добавлен экземпляр набора данных в кэш данных.

### <a name="to-create-the-excel-workbook-project"></a>Создание проекта книги Excel

1. В **Обозреватель решений** щелкните правой кнопкой мыши решение **AdventureWorksDataset** , наведите указатель на пункт **добавить** и выберите пункт **Новый проект**.

2. В области Шаблоны разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office**.

3. В развернутом узле **Office** выберите узел **2010** .

4. В списке шаблонов проектов выберите проект книга Excel.

5. В поле **имя** введите **адвентуреворксрепорт**. Не изменяйте расположение.

6. Нажмите кнопку **ОК**.

     Откроется **Мастер проектов набора средств Visual Studio для Office** .

7. Убедитесь, что выбран пункт **создать новый документ** , и нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает книгу **адвентуреворксрепорт** в конструкторе и добавляет проект **адвентуреворксрепорт** в **Обозреватель решений**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Добавление набора данных в источники данных в проекте книги Excel
 Прежде чем можно будет отобразить набор данных в книге Excel, необходимо сначала добавить набор данных в источники данных в проекте книги Excel.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Добавление набора данных в источники данных в проекте книги Excel

1. В **Обозреватель решений** дважды щелкните **Лист1. CS** или **Sheet1. vb** в проекте **адвентуреворксрепорт** .

     Книга откроется в конструкторе.

2. В меню **Данные** выберите команду **Добавить новый источник данных**.

     Откроется **Мастер настройки источника данных** .

3. Щелкните **объект**, а затем нажмите кнопку **Далее**.

4. На странице **Выбор объекта для привязки** нажмите кнопку **Добавить ссылку**.

5. На вкладке **проекты** щелкните **AdventureWorksDataset** и нажмите кнопку **ОК**.

6. В пространстве имен **AdventureWorksDataset** сборки **AdventureWorksDataset** щелкните **AdventureWorksLTDataSet** и нажмите кнопку **Готово**.

     Откроется окно **Источники данных** , и в список источников данных будет добавлен **AdventureWorksLTDataSet** .

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Создание объекта ListObject, привязанного к экземпляру набора данных
 Чтобы отобразить набор данных в книге, создайте объект <xref:Microsoft.Office.Tools.Excel.ListObject> , привязанный к экземпляру набора данных. Дополнительные сведения о привязке элементов управления к данным см. [в разделе Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Создание объекта ListObject, привязанного к экземпляру набора данных

1. В окне **Источники данных** разверните узел **AdventureWorksLTDataSet** в разделе **AdventureWorksDataset**.

2. Выберите узел **продукт** , щелкните появившуюся стрелку раскрывающегося списка и выберите в раскрывающемся списке элемент **ListObject** .

     Если стрелка раскрывающегося списка не отображается, убедитесь, что книга открыта в конструкторе.

3. Перетащите таблицу **Product** в ячейку a1.

     <xref:Microsoft.Office.Tools.Excel.ListObject>На листе создается элемент управления с именем `productListObject` , начиная с ячейки a1. Одновременно в проект добавляется объект набора данных `adventureWorksLTDataSet` и объект <xref:System.Windows.Forms.BindingSource> с именем `productBindingSource` . Объект <xref:Microsoft.Office.Tools.Excel.ListObject> привязан к объекту <xref:System.Windows.Forms.BindingSource>, который в свою очередь привязан к объекту набора данных.

## <a name="add-the-dataset-to-the-data-cache"></a>Добавление набора данных в кэш данных
 Чтобы включить код вне проекта книги Excel для доступа к набору данных в книге, необходимо добавить набор данных в кэш данных. Дополнительные сведения о кэше данных см. в разделе [кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md) и [кэширование данных](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Добавление набора данных в кэш данных

1. В конструкторе щелкните **adventureWorksLTDataSet**.

2. В окне **Свойства** задайте для свойства **модификаторы** значение **Public**.

3. Присвойте  свойству CacheInDocument **значение true**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Инициализация набора данных в книге
 Прежде чем можно будет получить данные из кэшированного набора данных с помощью консольного приложения, необходимо сначала заполнить кэшированный набор данных данными.

### <a name="to-initialize-the-dataset-in-the-workbook"></a>Инициализация набора данных в книге

1. В **Обозреватель решений** щелкните правой кнопкой мыши файл **Sheet1. CS** или **Sheet1. vb** и выберите пункт **Просмотреть код**.

2. Замените обработчик событий `Sheet1_Startup` следующим кодом. Этот код использует экземпляр `ProductTableAdapter` класса, который определен в проекте **AdventureWorksDataset** для заполнения кэшированного набора данных данными, если в настоящее время он пуст.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb" id="Snippet8":::

## <a name="checkpoint"></a>Контрольная точка
 Создайте и запустите проект книги Excel, чтобы убедиться, что он компилируется и выполняется без ошибок. Эта операция также заполняет кэшированный набор данных и сохраняет данные в книге.

### <a name="to-build-and-run-the-project"></a>Построение и запуск проекта

1. В **Обозреватель решений** щелкните правой кнопкой мыши проект **адвентуреворксрепорт** , выберите пункт **Отладка** и щелкните **запустить новый экземпляр**.

     Проект будет построен, а книга откроется в Excel. Проверьте выполнение следующих условий.

    - <xref:Microsoft.Office.Tools.Excel.ListObject>Заполняется данными.

    - Значение в столбце **ListPrice** для первой строки <xref:Microsoft.Office.Tools.Excel.ListObject> равно 1431,5. Далее в этом пошаговом руководстве будет использоваться консольное приложение для изменения значений в столбце **ListPrice** .

2. Сохраните книгу. Не изменяйте имя файла или расположение книги.

3. Закройте Excel.

## <a name="create-a-console-application-project"></a>Создание проекта консольного приложения
 Создайте проект консольного приложения, который будет использоваться для изменения данных в кэшированном наборе данных в книге.

### <a name="to-create-the-console-application-project"></a>Создание проекта консольного приложения

1. В **Обозреватель решений** щелкните правой кнопкой мыши решение **AdventureWorksDataset** , наведите указатель на пункт **добавить** и выберите пункт **Новый проект**.

2. В области **типы проектов** разверните узел **Visual C#** или **Visual Basic**, а затем выберите пункт **Windows**.

3. Выберите панель **Консольное приложение** в области **Шаблоны**.

4. В поле **имя** введите объект **записи**. Не изменяйте расположение.

5. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет проект **записи** в **Обозреватель решений** и открывает файл кода **Program. CS** или **Module1. vb** .

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Изменение данных в кэшированном наборе данных с помощью консольного приложения
 Используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс в консольном приложении для считывания данных в локальный `AdventureWorksLTDataSet` объект, изменения этих данных, а затем сохраните их обратно в кэшированный набор данных.

### <a name="to-change-data-in-the-cached-dataset"></a>Изменение данных в кэшированном наборе данных

1. В **Обозреватель решений** щелкните правой кнопкой мыши проект **записи** и выберите команду **Добавить ссылку**.

2. На вкладке **.NET** выберите **Microsoft. VisualStudio. Tools. Applications**.

3. Нажмите кнопку **ОК**.

4. В **Обозреватель решений** щелкните правой кнопкой мыши проект **записи** и выберите команду **Добавить ссылку**.

5. На вкладке **проекты** выберите **AdventureWorksDataset** и нажмите кнопку **ОК**.

6. Откройте файл *Program. CS* или *Module1. vb* в редакторе кода.

7. Добавьте следующий оператор **using** (для C#) или **Imports** (for Visual Basic) в начало файла кода.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet1":::

8. Добавьте в метод `Main` следующий код. Этот код объявляет следующие объекты:

   - Экземпляр `AdventureWorksLTDataSet` типа, определенный в проекте **AdventureWorksDataset** .

   - Путь к книге Адвентуреворксрепорт в папке Build проекта **адвентуреворксрепорт** .

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Объект, используемый для доступа к кэшу данных в книге.

     > [!NOTE]
     > В следующем коде предполагается, что вы используете книгу с расширением *xlsx* . Если книга в проекте имеет другое расширение файла, при необходимости измените путь.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet6":::

9. Добавьте следующий код в `Main` метод после кода, добавленного на предыдущем шаге. Этот код выполняет следующие задачи:

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Для доступа к кэшированному набору данных в книге используется свойство класса.

   - Он считывает данные из кэшированного набора данных в локальный набор данных.

   - Он изменяет `ListPrice` значение каждого продукта в таблице Product набора данных.

   - Он сохраняет изменения в кэшированном наборе данных в книге.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet7":::

10. В **Обозреватель решений** щелкните правой кнопкой мыши проект **записи** , наведите указатель на пункт **Отладка** и выберите команду **запустить новый экземпляр**.

     Консольное приложение отображает сообщения во время считывания кэшированного набора данных в локальный набор данных, изменяет цены продукта в локальном наборе данных и сохраняет новые значения в кэшированном наборе данных. Нажмите клавишу **Enter** , чтобы закрыть это приложение.

## <a name="test-the-workbook"></a>Тестирование книги
 При открытии книги <xref:Microsoft.Office.Tools.Excel.ListObject> теперь отображает изменения, внесенные в `ListPrice` столбец данных в кэшированном наборе данных.

### <a name="to-test-the-workbook"></a>Тестирование книги

1. Закройте книгу Адвентуреворксрепорт в конструкторе Visual Studio, если она все еще открыта.

2. Откройте книгу Адвентуреворксрепорт, которая находится в папке Build проекта **адвентуреворксрепорт** . По умолчанию папка сборки находится в одном из следующих расположений:

    - *%UserProfile%\My документс\адвентуреворксрепорт\бин\дебуг* (для Windows XP и более ранних версий)

    - *%Усерпрофиле%\документс\адвентуреворксрепорт\бин\дебуг* (для Windows Vista)

3. Убедитесь, что значение в столбце **ListPrice** для первой строки в <xref:Microsoft.Office.Tools.Excel.ListObject> теперь равно 1574,65.

4. Закройте книгу.

## <a name="see-also"></a>См. также статью

- [Пошаговое руководство. Вставка данных в книгу на сервере](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
