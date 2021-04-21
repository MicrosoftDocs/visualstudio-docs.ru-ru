---
title: Пошаговое руководство. Вставка данных в книгу на сервере
description: Узнайте, как вставлять данные в набор данных, кэшированный в книге Microsoft Excel, не запуская Excel с помощью класса ServerDocument.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
- workbooks [Office development in Visual Studio], inserting data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bf5d3bcb09ce1db013b89e60b22308f1904c4796
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827725"
---
# <a name="walkthrough-insert-data-into-a-workbook-on-a-server"></a>Пошаговое руководство. Вставка данных в книгу на сервере
  В этом пошаговом руководстве показано, как вставить данные в набор данных, кэшированный в Microsoft Office книгу Excel, не запуская Excel с помощью <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- Определение набора данных, содержащего данные из базы данных AdventureWorksLT.

- Создание экземпляров набора данных в проекте книги Excel и проекте консольного приложения.

- Создание объекта <xref:Microsoft.Office.Tools.Excel.ListObject> , привязанного к набору данных в книге.

- Добавление набора данных в книгу в кэш данных.

- Вставка данных в кэшированный набор данных путем выполнения кода в консольном приложении без запуска Excel.

  Хотя в этом пошаговом руководстве предполагается, что код выполняется на компьютере разработчика, код, продемонстрированный в этом пошаговом руководстве, можно использовать на сервере, на котором не установлен Excel.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Доступ к выполняющемуся экземпляру Microsoft SQL Server или Microsoft SQL Server Express, к которому присоединен образец базы данных AdventureWorksLT. Базу данных AdventureWorksLT можно загрузить с [веб-сайта CodePlex](https://archive.codeplex.com/?p=SqlServerSamples). Дополнительные сведения о подключении базы данных см. в следующих разделах:

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

    В противном случае нажмите **Создать подключение** и в диалоговом окне **Добавление подключения** создайте новое подключение. Дополнительные сведения см. в разделе [инструкции. подключение к данным в базе данных](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md).

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

2. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.

3. В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .

4. В списке шаблонов проектов выберите проект **Книга Excel 2010** или **Книга Excel 2013** .

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

## <a name="checkpoint"></a>Контрольная точка
 Создайте и запустите проект книги Excel, чтобы убедиться, что он компилируется и выполняется без ошибок.

### <a name="to-build-and-run-the-project"></a>Построение и запуск проекта

1. В **Обозреватель решений** щелкните правой кнопкой мыши проект **адвентуреворксрепорт** , выберите пункт **Отладка** и щелкните **запустить новый экземпляр**.

     Проект будет построен, а книга откроется в Excel. Элемент <xref:Microsoft.Office.Tools.Excel.ListObject> в **Лист1** пуст, так как `adventureWorksLTDataSet` объект в кэше данных еще не содержит данных. В следующем разделе будет использоваться консольное приложение для заполнения `adventureWorksLTDataSet` объекта данными.

2. Закройте Excel. Не сохраняйте изменения.

## <a name="create-a-console-application-project"></a>Создание проекта консольного приложения
 Создайте проект консольного приложения, который будет использоваться для вставки данных в кэшированный набор данных в книге.

### <a name="to-create-the-console-application-project"></a>Создание проекта консольного приложения

1. В **Обозреватель решений** щелкните правой кнопкой мыши решение **AdventureWorksDataset** , наведите указатель на пункт **добавить** и выберите пункт **Новый проект**.

2. В области **типы проектов** разверните узел **Visual C#** или **Visual Basic**, а затем выберите пункт **Windows**.

3. Выберите панель **Консольное приложение** в области **Шаблоны**.

4. В поле **имя** введите объект **записи**. Не изменяйте расположение.

5. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет проект **записи** в **Обозреватель решений** и открывает файл кода **Program. CS** или **Module1. vb** .

## <a name="add-data-to-the-cached-dataset-by-using-the-console-application"></a>Добавление данных в кэшированный набор данных с помощью консольного приложения
 Используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс в консольном приложении для заполнения кэшированного набора данных в книге данными.

### <a name="to-add-data-to-the-cached-dataset"></a>Добавление данных в кэшированный набор данных

1. В **Обозреватель решений** щелкните правой кнопкой мыши проект **записи** и выберите команду **Добавить ссылку**.

2. На вкладке **.NET** выберите **Microsoft. VisualStudio. Tools. Applications. ServerDocument**.

3. Нажмите кнопку **ОК**.

4. В **Обозреватель решений** щелкните правой кнопкой мыши проект **записи** и выберите команду **Добавить ссылку**.

5. На вкладке **проекты** выберите **AdventureWorksDataset** и нажмите кнопку **ОК**.

6. Откройте файл *Program. CS* или *Module1. vb* в редакторе кода.

7. Добавьте следующий оператор **using** (для C#) или **Imports** (for Visual Basic) в начало файла кода.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet1":::

8. Добавьте в метод `Main` следующий код. Этот код объявляет следующие объекты:

   - Экземпляры `AdventureWorksLTDataSet` `ProductTableAdapter` типов и, определенные в проекте **AdventureWorksDataset** .

   - Путь к книге Адвентуреворксрепорт в папке Build проекта **адвентуреворксрепорт** .

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Объект, используемый для доступа к кэшу данных в книге.

     > [!NOTE]
     > В следующем коде предполагается, что вы используете книгу с расширением *xlsx* . Если книга в проекте имеет другое расширение файла, при необходимости измените путь.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet3":::

9. Добавьте следующий код в `Main` метод после кода, добавленного на предыдущем шаге. Этот код выполняет следующие задачи:

   - Он заполняет объект типизированного набора данных с помощью адаптера таблицы.

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Для доступа к кэшированному набору данных в книге используется свойство класса.

   - Он использует <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> метод для заполнения кэшированного набора данных данными из локального типизированного набора данных.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet4":::

10. В **Обозреватель решений** щелкните правой кнопкой мыши проект **записи** , наведите указатель на пункт **Отладка** и выберите команду **запустить новый экземпляр**.

     Проект будет построен, а консольное приложение отобразит несколько сообщений о состоянии, когда заполнится локальный набор данных и когда приложение сохранит данные в кэшированном наборе данных в книге. Нажмите клавишу **Enter** , чтобы закрыть это приложение.

## <a name="test-the-workbook"></a>Тестирование книги
 При открытии книги в <xref:Microsoft.Office.Tools.Excel.ListObject> теперь отображаются данные, добавленные в кэшированный набор данных с помощью консольного приложения.

### <a name="to-test-the-workbook"></a>Тестирование книги

1. Закройте книгу Адвентуреворксрепорт в конструкторе Visual Studio, если она все еще открыта.

2. В проводнике откройте книгу Адвентуреворксрепорт, которая находится в папке Build проекта **адвентуреворксрепорт** . По умолчанию папка сборки находится в одном из следующих расположений:

    - *%UserProfile%\My документс\адвентуреворксрепорт\бин\дебуг* (для Windows XP и более ранних версий)

    - *%Усерпрофиле%\документс\адвентуреворксрепорт\бин\дебуг* (для Windows Vista)

3. Убедитесь, что <xref:Microsoft.Office.Tools.Excel.ListObject> заполнены данными после открытия книги.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о работе с кэшированными данными см. в следующих разделах:

- Изменение данных в кэшированном наборе данных без запуска Excel. Дополнительные сведения см. [в разделе Пошаговое руководство. изменение кэшированных данных в книге на сервере](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>См. также статью

- [Пошаговое руководство. изменение кэшированных данных в книге на сервере](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
