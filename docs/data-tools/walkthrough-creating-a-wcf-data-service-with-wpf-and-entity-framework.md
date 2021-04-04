---
title: Создание службы данных WCF с помощью & WPF Entity Framework
description: Создание службы данных WCF с WPF и Entity Framework, размещенной в веб-приложении ASP.NET, и доступ к нему из Windows Forms приложения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f519d8e3bfe01fc3e4a1e4cfe82f4f8502c84821
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215699"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Пошаговое руководство. Создание службы данных WCF с помощью WPF и Entity Framework
В этом пошаговом руководстве демонстрируется создание простой службы [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] в веб-приложении [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и последующий доступ к ней из приложения Windows Forms.

В этом пошаговом руководстве вы:

- Создайте веб-приложение для размещения [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Создайте объект [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] , представляющий `Customers` таблицу в базе данных Northwind.

- Создайте таблицу [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Создайте клиентское приложение и добавьте ссылку на [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Будет включена привязка данных к службе и создан пользовательский интерфейс.

- При необходимости в приложение будут добавлены возможности фильтрации.

## <a name="prerequisites"></a>Предварительные требования
В этом пошаговом руководстве используется SQL Server Express LocalDB и образец базы данных Northwind.

1. Если у вас нет SQL Server Express LocalDB, установите его на [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)или с помощью **Visual Studio Installer**. В **Visual Studio Installer** можно установить SQL Server Express LocalDB как часть рабочей нагрузки **хранения и обработки данных** или как отдельный компонент.

2. Установите учебную базу данных Northwind, выполнив следующие действия.

    1. В Visual Studio откройте окно **Обозреватель объектов SQL Server** . (**Обозреватель объектов SQL Server** устанавливается как часть рабочей нагрузки **хранения и обработки данных** в Visual Studio Installer.) Разверните узел **SQL Server** . Щелкните правой кнопкой мыши экземпляр LocalDB и выберите **создать запрос**.

       Откроется окно редактора запросов.

    2. Скопируйте [скрипт Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных Northwind с нуля и заполняет ее данными.

    3. Вставьте скрипт T-SQL в редактор запросов, а затем нажмите кнопку **выполнить** .

       По истечении короткого времени выполнение запроса завершается и создается база данных Northwind.

## <a name="creating-the-service"></a>Создание службы
Чтобы создать [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], нужно добавить веб-проект, создать [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] и службу из модели.

На первом шаге вы добавили веб-проект для размещения службы.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>Создание веб-проекта

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

2. В диалоговом окне **Новый проект** разверните узел **Visual Basic** или **Visual C#** и выберите пункт **Веб**, а затем выберите шаблон **Веб-приложение ASP.NET**.

3. В текстовом поле **Имя** введите **NorthwindWeb** и нажмите кнопку **ОК**.

4. В диалоговом окне **Новый проект ASP.NET** в списке **Выбор шаблона** выберите **Пустой**, а затем нажмите кнопку **ОК**.

На следующем шаге создается объект [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] , представляющий `Customers` таблицу в базе данных Northwind.

### <a name="to-create-the-entity-data-model"></a>Создание модели EDM

1. В строке меню выберите **Проект** > **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите узел **Данные** и выберите элемент **Модель EDM ADO.NET**.

3. В текстовом поле **имя** введите `NorthwindModel` , а затем нажмите кнопку **добавить** .

     Появится мастер модели EDM.

4. В мастере моделей EDM на странице **Выбор модели содержимого** выберите элемент **Конструктор EF из базы данных** и нажмите кнопку **Далее**.

5. На странице **Выбор подключения к базе данных** выполните одно из следующих действий:

    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

         -или-

    - Нажмите кнопку **Создать подключение** для создания нового подключения к данным. Дополнительные сведения см. в разделе [Добавление новых соединений](../data-tools/add-new-connections.md).

6. Если база данных требует пароль, нажмите кнопку **Да, включить конфиденциальные данные в строку подключения**, а затем нажмите кнопку **Далее**.

    > [!NOTE]
    > Если появится диалоговое окно, выберите **Да**, чтобы сохранить файл в проекте.

7. На странице **Выберите версию** выберите переключатель **Entity Framework 5.0** и нажмите кнопку **Далее**.

    > [!NOTE]
    > Чтобы использовать последнюю версию Entity Framework 6 со службами WCF, нужно установить пакет NuGet WCF Data Services Entity Framework Provider. См. статью [использование службы данных WCF 5.6.0 с Entity Framework 6 +](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. На странице **Выбор объектов базы данных** разверните узел **Таблицы**, установите флажок **Customers** и нажмите кнопку **Готово**.

     Отобразится схема сущностная модель, а в проект будет добавлен файл *NorthwindModel. EDMX* .

На следующем шаге вы создадите и протестируете службу данных.

### <a name="to-create-the-data-service"></a>Создание службы данных

1. В строке меню выберите **Проект** > **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите узел **Веб** и элемент **Служба данных WCF 5.6**.

3. В текстовом поле **имя** введите `NorthwindCustomers` , а затем нажмите кнопку **добавить** .

     Файл **NorthwindCustomers.svc** появится в **редакторе кода**.

4. В **редакторе кода** найдите первый комментарий `TODO:` и замените код следующим:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs" id="Snippet1":::

5. Замените комментарии в обработчике событий `InitializeService` следующим кодом:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs" id="Snippet2":::


6. В строке меню выберите **Отладка**  >  **начать без отладки** , чтобы запустить службу. Откроется окно браузера, и отобразится схема XML для службы.

7. В **адресной** строке введите `Customers` в конце URL-адреса для **норсвиндкустомерс. svc**, а затем нажмите клавишу **Ввод** .

     Отобразится XML-представление данных в `Customers` таблице.

    > [!NOTE]
    > В некоторых случаях обозреватель Internet Explorer может неправильно интерпретировать данные как RSS-канал. Необходимо убедиться, что параметр, определяющий, отображаются ли RSS-каналы, отключен. Дополнительные сведения см. в разделе [Устранение неполадок ссылок на службы](../data-tools/troubleshooting-service-references.md).

8. Закройте окно браузера.

На следующих шагах вы создадите клиентское приложение Windows Forms для использования службы.

## <a name="creating-the-client-application"></a>Создание клиентского приложения
Чтобы создать клиентское приложение, нужно добавить второй проект, добавить к проекту ссылку на службу, настроить источник данных и создать пользовательский интерфейс, отображающий данные из службы.

На первом шаге в решение добавляется проект Windows Forms, который задается в качестве запускаемого проекта.

### <a name="to-create-the-client-application"></a>Создание клиентского приложения

1. В строке меню выберите файл, **Добавить**  >  **Новый проект**.

2. В диалоговом окне **Новый проект** разверните узел **Visual Basic** или **Visual C#** , выберите узел **Windows** , а затем выберите **Windows Forms приложение**.

3. В текстовом поле **Имя** введите `NorthwindClient` и нажмите кнопку **ОК**.

4. В **обозревателе решений** выберите узел проекта **NorthwindClient**.

5. В строке меню выберите **Проект**, затем **Назначить запускаемым проектом**.

На следующем шаге вы добавите в [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] веб-проект ссылку на службу.

### <a name="to-add-a-service-reference"></a>Добавление ссылки на службу

1. В строке меню выберите **проект**  >  **Добавление ссылки на службу**.

2. В диалоговом окне **Добавление ссылки на службу** нажмите кнопку **Найти**.

     В поле **Адрес** появится URL-адрес службы NorthwindCustomers.

3. Нажмите кнопку **ОК**, чтобы добавить ссылку на службу.

На следующем шаге вы настроите источник данных, чтобы включить привязку данных к службе.

### <a name="to-enable-data-binding-to-the-service"></a>Включение привязки данных к службе

1. В строке меню выберите **Просмотреть**  >  **другие**  >  **Источники данных** Windows.

   Открывается окно **Источники данных**.

2. В окне **Источники данных** нажмите кнопку **Добавить новый источник данных**.

3. На странице **Выбор типа источника данных****мастера настройки источника данных** выберите **Объект** и нажмите кнопку **Далее**.

4. На странице **Выбор объектов данных** последовательно разверните узлы **NorthwindClient** и **NorthwindClient.ServiceReference1**.

5. Установите флажок **Customer** и нажмите кнопку **Готово**.

На следующем шаге создается пользовательский интерфейс, отображающий данные из службы.

### <a name="to-create-the-user-interface"></a>Создание пользовательского интерфейса

1. В окне **Источники данных** откройте контекстное меню для узла **Customers** и выберите команду **Копировать**.

2. В конструкторе форм в файле **Form1.vb** или **Form1.cs** откройте контекстное меню и выберите команду **Вставить**.

    На форму добавится элемент управления <xref:System.Windows.Forms.DataGridView>, компонент <xref:System.Windows.Forms.BindingSource> и компонент <xref:System.Windows.Forms.BindingNavigator>.

3. Выберите элемент управления **CustomersDataGridView** и в окне **Свойства** установите для свойства **Закрепить** значение **Заполнение**.

4. В **Обозреватель решений** откройте контекстное меню узла **Form1** и выберите пункт **Просмотреть код** , чтобы открыть редактор кода, и добавьте следующий `Imports` `Using` оператор или в начало файла:

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. Добавьте следующий код в обработчик событий `Form1_Load` .

   ```vb
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
           Dim proxy As New NorthwindEntities _
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
           Me.CustomersBindingSource.DataSource = proxy.Customers
       End Sub
   ```

   ```csharp
   private void Form1_Load(object sender, EventArgs e)
   {
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
   this.CustomersBindingSource.DataSource = proxy.Customers;
   }
   ```

6. В **обозревателе решений** откройте контекстное меню файла **NorthwindCustomers.svc** и выберите команду **Просмотреть в браузере**. Откроется Internet Explorer, и отобразится схема XML для службы.

7. Скопируйте URL-адрес из адресной строки обозревателя Internet Explorer.

8. В коде, добавленном на этапе 4, выберите код `http://localhost:53161/NorthwindCustomers.svc/` и замените его только что скопированным URL-адресом.

9. В строке меню выберите **Отладка**  >  **начать отладку** , чтобы запустить приложение. Отобразятся сведения о клиенте.

   Теперь в наличии имеется рабочее приложение, которое будет отображать список клиентов из службы NorthwindCustomers. При необходимости в отображении дополнительных данных посредством службы, свойство [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] можно изменить, чтобы включить дополнительные таблицы из базы данных Northwind.

На следующем необязательном шаге вы узнаете, как фильтровать данные, возвращаемые службой.

## <a name="adding-filtering-capabilities"></a>Добавление возможностей фильтрации
На этом шаге вы настраиваете приложение для фильтрации данных по городу клиента.

### <a name="to-add-filtering-by-city"></a>Добавление фильтрации по городу

1. В **обозревателе решений** откройте контекстное меню узла **Form1.vb** или **Form1.cs** и выберите команду **Открыть**.

2. Добавьте в форму элементы управления <xref:System.Windows.Forms.TextBox> и <xref:System.Windows.Forms.Button> с **панели элементов**.

3. Откройте контекстное меню для <xref:System.Windows.Forms.Button> элемента управления, выберите **Просмотреть код**, а затем добавьте следующий код в `Button1_Click` обработчик событий:

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4. В коде выше замените `http://localhost:53161/NorthwindCustomers.svc` URL-адресом из обработчика событий `Form1_Load`.

5. В строке меню выберите **Отладка**  >  **начать отладку** , чтобы запустить приложение.

6. В текстовом поле введите **London** и нажмите кнопку. Будут отображены только клиенты из Лондона.

## <a name="see-also"></a>См. также раздел

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Практическое руководство. Добавление, обновление или удаление ссылки на службу данных WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
