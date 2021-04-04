---
title: Простое приложение для данных с WPF и Entity Framework 6
description: В этом пошаговом руководстве вы узнаете, как создать простое приложение для работы с формами в Visual Studio с Windows Presentation Foundation (WPF) и Entity Framework 6.
ms.custom: SEO-VS-2020
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: e3432dd9a72fa71ea1e749dd28e80a3d55cce19c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216063"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Создание простого приложения для обработки данных с помощью WPF и Entity Framework 6

В этом пошаговом руководстве показано, как создать базовое приложение "формы для данных" в Visual Studio. Приложение использует SQL Server LocalDB, базу данных Northwind, Entity Framework 6 (не Entity Framework Core) и Windows Presentation Foundation для платформа .NET Framework (не .NET Core). В нем показано, как выполнить базовую привязку данных с помощью представления «основной/подробности», а также с пользовательским навигатором привязки с кнопками для **перехода далее**, **Переместить назад**, **Перейти к началу**, **Перейти к концу**, **Обновить** и **Удалить**.

Эта статья посвящена использованию средств для данных в Visual Studio и не пытается объяснить основные технологии в любой глубине. Предполагается, что у вас есть базовые знания XAML, Entity Framework и SQL. В этом примере также не демонстрируется Архитектура Model-View-ViewModel (MVVM), которая является стандартом для приложений WPF. Однако этот код можно скопировать в собственное приложение MVVM с небольшими изменениями.

## <a name="install-and-connect-to-northwind"></a>Установка и подключение к Northwind

В этом примере используется SQL Server Express LocalDB и образец базы данных Northwind. Если поставщик данных ADO.NET для этого продукта поддерживает Entity Framework, он также должен работать с другими продуктами базы данных SQL.

1. Если у вас нет SQL Server Express LocalDB, установите его на [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)или с помощью **Visual Studio Installer**. В **Visual Studio Installer** можно установить SQL Server Express LocalDB как часть рабочей нагрузки **Разработка классических приложений .NET** или в качестве отдельного компонента.

2. Установите учебную базу данных Northwind, выполнив следующие действия.

    1. В Visual Studio откройте окно **Обозреватель объектов SQL Server** . (**Обозреватель объектов SQL Server** устанавливается как часть рабочей нагрузки **хранения и обработки данных** в **Visual Studio Installer**.) Разверните узел **SQL Server** . Щелкните правой кнопкой мыши экземпляр LocalDB и выберите **создать запрос**.

       Откроется окно редактора запросов.

    2. Скопируйте [скрипт Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных Northwind с нуля и заполняет ее данными.

    3. Вставьте скрипт T-SQL в редактор запросов, а затем нажмите кнопку **выполнить** .

       По истечении короткого времени выполнение запроса завершается и создается база данных Northwind.

3. [Добавление новых подключений](../data-tools/add-new-connections.md) для базы данных Northwind.

## <a name="configure-the-project"></a>Настройка проекта

1. В Visual Studio создайте новый проект **приложения WPF** на C#.

2. Добавьте пакет NuGet для Entity Framework 6. В **Обозреватель решений** выберите узел проекта. В главном меню выберите **проект**  >  **Управление пакетами NuGet**.

     ![Пункт меню "Управление пакетами NuGet"](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. В **диспетчере пакетов NuGet** щелкните ссылку **Обзор** . Entity Framework, вероятно, является верхним пакетом в списке. Щелкните **установить** на правой панели и следуйте инструкциям на экране. В окне вывода появится сообщение о завершении установки.

     ![Entity Framework пакет NuGet](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. Теперь можно использовать Visual Studio для создания модели на основе базы данных Northwind.

## <a name="create-the-model"></a>Создание модели

1. Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и последовательно выберите **Добавить** > **Новый элемент**. В левой области в узле C# выберите **данные** и в средней области выберите **ADO.NET EDM**.

   ![Новый элемент модели Entity Framework](../data-tools/media/raddata-ef-new-project-item.png)

2. Вызовите модель `Northwind_model` и нажмите кнопку **ОК**. Откроется **мастер EDM** . Выберите элемент **конструктор EF из базы данных** , а затем нажмите кнопку **Далее**.

   ![Модель EF из базы данных](../data-tools/media/raddata-ef-model-from-database.png)

3. На следующем экране введите или выберите соединение с базой данных LocalDB Northwind (например, (LocalDB) \MSSQLLocalDB), укажите базу данных Northwind и нажмите кнопку **Далее**.

4. На следующей странице мастера выберите таблицы, хранимые процедуры и другие объекты базы данных для включения в модель Entity Framework. Разверните узел dbo в представлении в виде дерева и выберите **Customers**, **Orders** и **Order Details**. Оставьте установленными значения по умолчанию и нажмите кнопку **Готово**.

    ![Выбор объектов базы данных для модели](../data-tools/media/raddata-choose-ef-objects.png)

5. Мастер создает классы C#, представляющие модель Entity Framework. Классы являются простыми старыми классами C#, и они являются привязкум к пользовательскому интерфейсу WPF. Файл *EDMX* описывает связи и другие метаданные, связывающие классы с объектами в базе данных. *TT* — это шаблоны T4, которые создают код, работающий с моделью, и сохраняет изменения в базе данных. Все эти файлы можно просмотреть в **Обозреватель решений** в узле Northwind_model.

      ![Файлы модели обозреватель решений EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    Область конструктора для файла *EDMX* позволяет изменять некоторые свойства и связи в модели. Мы не будем использовать конструктор в этом пошаговом руководстве.

6. Файлы *. TT* являются общим целям и необходимо настроить один из них для работы с DataBinding WPF, что требует обсерваблеколлектионс. В **Обозреватель решений** разверните узел Northwind_model, пока не найдете *Northwind_model. TT*. (Убедитесь, что вы не используете *. Файл Context.tt* , который находится непосредственно под *EDMX* -файлом.)

   - Замените два вхождения <xref:System.Collections.ICollection> на <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Замените первое вхождение <xref:System.Collections.Generic.HashSet%601> на <xref:System.Collections.ObjectModel.ObservableCollection%601> около строки 51. Не заменяйте второй экземпляр hash.

   - Замените единственное вхождение <xref:System.Collections.Generic> (около строки 431) на <xref:System.Collections.ObjectModel> .

7. Нажмите клавиши **CTRL** + **SHIFT** + **B** , чтобы построить проект. По завершении сборки классы модели видимы в мастере источников данных.

Теперь все готово для подключения этой модели к XAML-странице, чтобы можно было просматривать, перемещать и изменять данные.

## <a name="databind-the-model-to-the-xaml-page"></a>Привязка модели к странице XAML

Можно написать собственный код привязки данных, но гораздо проще позволить Visual Studio сделать это самостоятельно.

1. В главном меню выберите **проект**  >  **Добавить новый источник данных** , чтобы открыть **Мастер настройки источника данных**. Выберите **объект** , так как вы привязываетесь к классам модели, а не к базе данных:

     ![Мастер настройки источника данных с источником объекта](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Разверните узел проекта и выберите **Customer (клиент**). (Источники для заказов автоматически формируются из свойства навигации Orders в Customer.)

     ![Добавление классов сущностей в качестве источников данных](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. Нажмите кнопку **Готово**.

4. Перейдите к файлу *MainWindow. XAML* в представлении кода. Мы постоянно используем XAML для целей этого примера. Измените заголовок MainWindow на что-то более описательное и увеличьте его высоту и ширину до 600 x 800. Вы всегда можете изменить его позже. Теперь добавьте эти три определения строк в главную сетку, одну строку для кнопок навигации, одну для сведений клиента и одну для сетки, которая показывает их заказы:

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Теперь откройте файл *MainWindow. XAML* , чтобы просмотреть его в конструкторе. В результате окно **Источники данных** будет отображаться как параметр в окне Visual Studio рядом с **областью элементов**. Щелкните вкладку, чтобы открыть окно, или нажмите сочетание клавиш **SHIFT** + **ALT** + **D** или выберите **Просмотр**  >  **других**  >  **источников данных** Windows. Мы будем отображать каждое свойство в классе Customers в отдельном текстовом поле. Сначала щелкните стрелку в поле со списком **Клиенты** и выберите **сведения**. Затем перетащите узел в среднюю часть области конструктора, чтобы разработчик знал, что он должен находиться в средней строке. В случае его невозможности вручную указать строку в XAML. По умолчанию элементы управления размещаются вертикально в элементе Grid, но на этом этапе их можно расположить в форме. Например, может иметь смысл разместить текстовое поле **Name** сверху, над адресом. Пример приложения для этой статьи переупорядочивает поля и перемещает их в два столбца.

     ![Привязка источника данных клиентов к отдельным элементам управления](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     В представлении кода теперь можно увидеть новый `Grid` элемент в строке 1 (средняя строка) родительской сетки. Родительская сетка имеет `DataContext` атрибут, который ссылается на CollectionViewSource, добавленный в `Windows.Resources` элемент. Учитывая этот контекст данных, при привязке первого текстового поля к **адресу** это имя сопоставляется со `Address` свойством в текущем `Customer` объекте в CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Когда клиент отображается в верхней половине окна, необходимо просмотреть заказы в нижней половине. Заказы отображаются в одном элементе управления представления сетки. Для работы привязки "основной — подробности" необходимо выполнить привязку к свойству Orders в классе Customers, а не к отдельному узлу Orders. Перетащите свойство Orders класса Customers в нижнюю половину формы, чтобы конструктор поместит его в строку 2:

     ![Перетаскивание классов Orders в виде сетки](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio создала весь код привязки, который подключает элементы управления пользовательского интерфейса к событиям в модели. Для того чтобы увидеть некоторые данные, необходимо написать код для заполнения модели. Сначала перейдите к файлу *MainWindow. XAML. CS* и добавьте член данных в класс MainWindow для контекста данных. Этот объект, который был создан для вас, действует примерно так же, как элемент управления, отслеживающий изменения и события в модели. Вы также добавите элементы данных CollectionViewSource для клиентов и заказов, а также связанную логику инициализации конструктора. Начало класса должно выглядеть следующим образом:

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet1":::

     Добавьте `using` директиву для System. Data. Entity, чтобы перевести метод расширения нагрузки в область:

     ```csharp
     using System.Data.Entity;
     ```

     Теперь прокрутите вниз и найдите `Window_Loaded` обработчик событий. Обратите внимание, что в Visual Studio добавлен объект CollectionViewSource. Представляет объект Норсвиндентитиес, выбранный при создании модели. Вы уже добавили это, так что вам это не нужно. Выполним замену кода в `Window_Loaded` , чтобы метод теперь выглядел следующим образом:

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet2":::


8. Нажмите клавишу **F5**. Вы должны увидеть сведения для первого клиента, полученного в CollectionViewSource. Их заказы также должны отображаться в сетке данных. Форматирование не имеет ничего хорошего, так что давайте исправляется. Можно также создать способ просмотра других записей и выполнения базовых операций CRUD.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Настройка макета страницы и добавление сеток для новых клиентов и заказов

Расположение по умолчанию, созданное Visual Studio, не идеально подходит для вашего приложения, поэтому мы предоставим конечный XAML-код для копирования кода. Также требуются некоторые «формы» (которые являются сетками), чтобы пользователь мог добавить нового клиента или заказ. Чтобы добавить нового клиента и заказ, необходим отдельный набор текстовых полей, не привязанных к данным `CollectionViewSource` . Вы можете указать, какую сетку пользователь видит в любой момент, установив свойство Visible в методах обработчика. Наконец, вы добавите кнопку Удалить в каждую строку сетки заказы, чтобы позволить пользователю удалить отдельный заказ.

Сначала добавьте эти стили в `Windows.Resources` элемент в файле *MainWindow. XAML*:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

Затем замените всю внешнюю сетку этой разметкой:

```xaml
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Добавление кнопок для навигации, добавления, обновления и удаления

В Windows Forms приложениях вы получаете объект BindingNavigator с кнопками для навигации по строкам в базе данных и выполнения базовых операций CRUD. WPF не предоставляет BindingNavigator, но достаточно просто создать его. Это можно сделать с помощью кнопок в горизонтальном StackPanel и связать кнопки с командами, привязанными к методам в коде программной части.

Логика команды состоит из четырех частей: (1) команды, (2) привязки, (3) кнопки и (4) обработчики команд в коде программной части.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Добавление команд, привязок и кнопок в XAML

1. Сначала добавьте команды в файл *MainWindow. XAML* внутри `Windows.Resources` элемента:

    ```xaml
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2. CommandBinding сопоставляет `RoutedUICommand` событие с методом в коде программной части. Добавьте этот `CommandBindings` элемент после `Windows.Resources` закрывающего тега:

    ```xaml
    <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3. Теперь добавьте с помощью `StackPanel` кнопок навигации, добавления, удаления и обновления. Сначала добавьте этот стиль в `Windows.Resources` :

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Во-вторых, вставьте этот код сразу после элемента `RowDefinitions` для внешнего `Grid` элемента в верхнюю часть страницы XAML:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Добавление обработчиков команд в класс MainWindow

Код программной части является минимальным, за исключением методов Add и DELETE. Навигация выполняется путем вызова методов для свойства View объекта CollectionViewSource. В этом `DeleteOrderCommandHandler` примере показано, как выполнить каскадное удаление в заказе. Сначала необходимо удалить связанные с ним Order_Details. `UpdateCommandHandler`Добавляет нового клиента или заказа в коллекцию или просто обновляет существующего клиента или заказ с учетом изменений, внесенных пользователем в текстовые поля.

Добавьте эти методы обработчика в класс MainWindow в *MainWindow. XAML. CS*. Если CollectionViewSource для таблицы Customers имеет другое имя, необходимо изменить имя в каждом из этих методов:

:::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet3":::


## <a name="run-the-application"></a>Выполнение приложения

Чтобы начать отладку, нажмите клавишу **F5**. Данные о клиентах и заказах должны быть заполнены в сетке, а кнопки навигации должны работать надлежащим образом. Щелкните **фиксация** , чтобы добавить нового клиента или заказ в модель после того, как вы введете данные. Нажмите кнопку **Отмена** , чтобы вернуться из нового клиента или новой формы заказа без сохранения данных. Вы можете вносить изменения в существующие клиенты и заказы непосредственно в текстовые поля, и эти изменения автоматически записываются в модель.

## <a name="see-also"></a>См. также

- [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Документация по Entity Framework](/ef/)
