---
title: Привязка элементов управления WPF к службе данных WCF
description: Привязка элементов управления WPF к службе данных WCF в Visual Studio. Элементы управления привязаны к записям клиентов, инкапсулированным в WCF-службе данных.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ae6a2fd6eac9f59a7836dae23d442962e1b2b27e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215556"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Привязка элементов управления WPF к службе данных WCF

В этом пошаговом руководстве вы создадите приложение WPF, содержащее элементы управления с привязкой к данным. Элементы управления привязаны к записям клиентов, инкапсулированным в WCF-службе данных. Вы также добавите кнопки, позволяющие клиентам просматривать и обновлять записи.

В этом пошаговом руководстве описаны следующие задачи:

- Создание модели данных с использованием сущностей (EDM), сформированной из данных в учебной базе данных AdventureWorksLT.

- Создание службы данных WCF, предоставляющей данные в EDM приложению WPF.

- Создание набора элементов управления с привязкой к данным путем перетаскивания элементов из окна **Источники данных** в конструктор WPF.

- Создание кнопок для перехода вперед и назад по записям клиентов.

- Создание кнопки, сохраняющей изменения данных в элементах управления в службе данных WCF и базовом источнике данных.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Предварительные требования

Для выполнения этого пошагового руководства требуются следующие компоненты:

- Visual Studio

- Доступ к запущенному экземпляру SQL Server или SQL Server Express с подключенной учебной базой данных AdventureWorksLT. Базу данных AdventureWorksLT можно загрузить с [веб-сайта CodePlex](https://archive.codeplex.com/?p=SqlServerSamples).

Перед изучением приведенных ниже концепций будет полезно, хотя и не обязательно, ознакомиться со следующим пошаговым руководством.

- [Службы данных WCF](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Модели данных в [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

- Модели EDM и ADO.NET Entity Framework. Дополнительные сведения см. в разделе [Entity Framework обзор](/dotnet/framework/data/adonet/ef/overview).

- Привязка данных WPF. Дополнительные сведения см. в разделе [Общие сведения о привязке данных](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Создание проекта службы

1. Начните это пошаговое руководство, создав проект **веб-приложения** на C# или Visual Basic ASP.NET. Назовите проект **адвентуреворкссервице**.

2. В **обозревателе решений** щелкните правой кнопкой мыши **Default.aspx** и выберите пункт **Удалить**. Этот файл не является обязательным для этого пошагового руководства.

## <a name="create-an-entity-data-model-for-the-service"></a>Создание EDM для службы

Чтобы предоставить данные приложению с помощью службы данных WCF, необходимо определить модель данных для службы. Служба данных WCF поддерживает два типа моделей данных: модели EDM и пользовательские модели данных, которые определяются с помощью объектов среды CLR, реализующих <xref:System.Linq.IQueryable%601> интерфейс. В данном пошаговом руководстве вы создадите модель EDM для использования в качестве модели данных.

1. В меню **Проект** выберите **Добавить новый элемент**.

2. В списке "Установленные шаблоны" щелкните **Данные** и выберите элемент проекта **Модель ADO.NET EDM**.

3. Измените имя на `AdventureWorksModel.edmx` и нажмите кнопку **Добавить**.

     Открывается **Мастер моделей EDM**.

4. На странице **Выбор содержимого модели** щелкните **Создать из базы данных** и нажмите кнопку **Далее**.

5. На странице **Выбор подключения к базе данных** выберите один из следующих параметров:

    - Если подключение к учебной базе данных AdventureWorksLT доступно в раскрывающемся списке, то выберите его.

    - Щелкните **Создать подключение** и создайте подключение к базе данных AdventureWorksLT.

6. На странице **Выбор подключения базы данных** убедитесь, что выбран параметр **Сохранить параметры соединения сущности в App.Config как**, а затем нажмите кнопку **Далее**.

7. На странице **Выбор объектов базы данных** разверните узел **Таблицы** и выберите таблицу **SalesOrderHeader**.

8. Нажмите кнопку **Готово**.

## <a name="create-the-service"></a>Создание службы

Создание WCF-службы данных для предоставления данных в EDM приложению WPF:

1. В меню **Проект** выберите команду **Добавить новый элемент**.

2. В списке **Установленные шаблоны** щелкните **Веб-сайт** и выберите элемент проекта **Служба данных WCF**.

3. В поле **имя** введите `AdventureWorksService.svc` и нажмите кнопку **добавить**.

     Visual Studio добавит в `AdventureWorksService.svc` проект.

## <a name="configure-the-service"></a>Настройка службы

Вам нужно настроить службу для использования созданной модели EDM:

1. В `AdventureWorks.svc` файле кода замените объявление класса **адвентуреворкссервице** следующим кодом.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb" id="Snippet1":::

     Этот код обновляет класс **адвентуреворкссервице** , чтобы он наследовался от <xref:System.Data.Services.DataService%601> класса, который работает с `AdventureWorksLTEntities` классом контекста объекта в EDM. Он также обновляет метод `InitializeService`, чтобы предоставить клиентам службы полный доступ на чтение/запись к сущности `SalesOrderHeader`.

2. Соберите проект и убедитесь в отсутствии ошибок.

## <a name="create-the-wpf-client-application"></a>Создание клиентского приложения WPF

Чтобы отобразить данные из службы данных WCF, создайте новое приложение WPF с источником данных, основанным на службе. Позднее в этом пошаговом руководстве вы добавите в приложение элементы управления с привязкой к данным.

1. В **обозревателе решений** щелкните правой кнопкой мыши узел решения, выберите команду **Добавить** и пункт **Новый проект**.

2. В диалоговом окне **Новый проект** разверните узел **Visual C#** или **Visual Basic**, а затем выберите **Windows**.

3. Выберите шаблон проекта **Приложение WPF**.

4. В поле **Имя** введите `AdventureWorksSalesEditor`, а затем нажмите кнопку **ОК**.

   Visual Studio добавит `AdventureWorksSalesEditor` проект в решение.

5. В меню **Данные** выберите команду **Показать источники данных**.

   Открывается окно **Источники данных**.

6. В окне **Источники данных** выберите **Добавить новый источник данных**.

   Открывается **мастер настройки источника данных**.

7. На странице **Выбор типа источника данных мастера** выберите **Служба** и нажмите кнопку **Далее**.

8. В диалоговом окне **Добавление ссылки на службу** выберите **Найти**.

   Visual Studio выполняет поиск доступных служб в текущем решении и добавляет `AdventureWorksService.svc` их в список доступных служб в поле **службы** .

9. Введите **AdventureWorksService** в поле **Пространство имен**.

10. В поле **Службы** щелкните **AdventureWorksService.svc** и нажмите кнопку **ОК**.

    Visual Studio скачивает сведения о службе и возвращается в **Мастер настройки источника данных**.

11. На странице **Добавление ссылки на службу** нажмите кнопку **Готово**.

    Visual Studio добавляет узлы, которые представляют данные, возвращаемые службой в окно **Источники данных**.

## <a name="define-the-user-interface"></a>Определение пользовательского интерфейса

Добавьте несколько кнопок в окно, изменив в XAML в конструкторе WPF. Позднее в рамках данного пошагового руководства вы добавите код, позволяющий пользователям просматривать и обновлять торговые записи с помощью этих кнопок.

1. В **обозревателе решений** дважды щелкните файл **MainWindow.xaml**.

   Открывается окно в Конструкторе WPF.

2. В представлении [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] конструктора добавьте следующий код между тегами `<Grid>`:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Выполните построение проекта.

## <a name="create-the-data-bound-controls"></a>Создание элементов управления с привязкой к данным

Создайте элементы управления, отображающие записи клиентов, перетащив `SalesOrderHeaders` узел из окна **Источники данных** в конструктор.

1. В окне **Источники данных** щелкните раскрывающееся меню для узла **SalesOrderHeaders** и выберите команду **Сведения**.

2. Разверните узел **SalesOrderHeaders**.

3. Для этого примера некоторые поля не отображаются, поэтому щелкните раскрывающееся меню рядом со следующими узлами и выберите **Нет**:

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **уникаль**

    Это действие не позволяет Visual Studio создать элементы управления с привязкой к данным для этих узлов на следующем шаге. В этом пошаговом руководстве предполагается, что конечному пользователю не нужно видеть эти данные.

4. Из окна **Источники данных** перетащите узел **SalesOrderHeaders** на строку сетки под строкой с кнопками.

     Visual Studio формирует XAML и код, который создает набор элементов управления, привязанных к данным в таблице **Продукт**. Дополнительные сведения о созданных XAML и коде см. в разделе [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. Щелкните в конструкторе текстовое поле рядом с меткой **Идентификатор клиента**.

6. В окне **Свойства** установите флажок рядом со свойством **IsReadOnly**.

7. Установите свойство **IsReadOnly** для каждого из следующих текстовых полей:

    - **Номер заказа на покупку**

    - **Код заказа на продажу**

    - **Число заказов на продажу**

## <a name="load-the-data-from-the-service"></a>Загрузка данных из службы

Используйте объект прокси службы для загрузки данных о продажах из службы. Затем назначьте возвращенные данные источнику данных <xref:System.Windows.Data.CollectionViewSource> в окне WPF.

1. В конструкторе, чтобы создать `Window_Loaded` обработчик событий, дважды щелкните текст, который считывает: **MainWindow**.

2. Замените этот обработчик событий следующим кодом. Замените адрес *localhost* в этом коде на локальный адрес вашего компьютера разработчика.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet2":::

## <a name="navigate-sales-records"></a>Навигация по записям о продажах

Добавьте код, позволяющий пользователям прокручивать записи о продажах с помощью **\<** and **>** кнопок.

1. В конструкторе дважды щелкните кнопку **<** на поверхности окна.

     Visual Studio открывает файл кода программной части и создает обработчик событий `backButton_Click` для события <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Добавьте следующий код в созданный обработчик событий `backButton_Click`:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet3":::

3. Вернитесь в конструктор и дважды щелкните кнопку **>** .

     Visual Studio открывает файл кода программной части и создает обработчик событий `nextButton_Click` для события <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

4. Добавьте следующий код в созданный обработчик событий `nextButton_Click`:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet4":::

## <a name="save-changes-to-sales-records"></a>Сохранить изменения в записях о продажах

Добавьте код, позволяющий пользователям просматривать и сохранять изменения в торговых записях с помощью кнопки **Сохранить изменения**:

1. В конструкторе дважды щелкните кнопку **Сохранить изменения**.

     Visual Studio открывает файл кода программной части и создает обработчик событий `saveButton_Click` для события <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Добавьте следующий код в обработчик событий `saveButton_Click`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet5":::

## <a name="test-the-application"></a>Тестирование приложения

Выполните сборку и запуск приложения, чтобы убедиться, что вы можете просмотреть и обновить записи клиентов:

1. В меню **Сборка** выберите пункт **построить решение**. Убедитесь, что сборка решения выполняется без ошибок.

2. Нажмите клавиши **CTRL** + **F5**.

     Visual Studio запускает проект **AdventureWorksService** без его отладки.

3. В **обозревателе решений** щелкните правой кнопкой мыши проект **AdventureWorksSalesEditor**.

4. В контекстном меню окна **Отладка** щелкните **запустить новый экземпляр**.

     Выполняется запуск приложения. Проверьте выполнение следующих условий.

    - Текстовые поля отображают разные поля данных из первой торговой записи, имеющей код заказа на продажу **71774**.

    - **>** **<** Чтобы перемещаться по другим записям о продажах, можно нажать кнопки или.

5. Введите текст в поле **Комментарий** для одной из торговых записей, а затем нажмите кнопку **Сохранить изменения**.

6. Закройте приложение и снова запустите его из Visual Studio.

7. Перейдите к измененной торговой записи и убедитесь, что изменения сохранились после перезапуска приложения.

8. Закройте приложение.

## <a name="next-steps"></a>Дальнейшие действия

После прохождения пошагового руководства вы можете выполнить следующие задачи.

- Узнайте, как использовать окно **Источники данных** в Visual Studio для привязки элементов управления WPF к другим типам источников данных. Дополнительные сведения см. в разделе [Привязка элементов управления WPF к набору данных](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Узнайте, как использовать окно **Источники данных** в Visual Studio для отображения связанных данных (то есть данных в отношении "родитель — потомок") в элементах управления WPF. Дополнительные сведения см. [в разделе Пошаговое руководство. Отображение связанных данных в приложении WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>См. также раздел

- [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Привязка элементов управления WPF к набору данных](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Общие сведения об WCF (платформа .NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Обзор Entity Framework (платформа .NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Общие сведения о привязке данных (платформа .NET Framework)](/dotnet/desktop-wpf/data/data-binding-overview)
