---
title: Добавление пользовательского элемента управления на начальную страницу | Документация Майкрософт
description: Узнайте, как добавить пользовательский элемент управления Windows Presentation Foundation (WPF) на начальную страницу в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 1e5305927ceb634c64e52bb64ce57197f1b6be4c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097608"
---
# <a name="add-user-control-to-the-start-page"></a>Добавление пользовательского элемента управления на начальную страницу

В этом пошаговом руководстве показано, как добавить ссылку на библиотеку DLL на настраиваемую начальную страницу. Пример добавляет в решение пользовательский элемент управления, создает пользовательский элемент управления, а затем ссылается на сборку из файла начальной страницы *. XAML* . На новой вкладке размещен пользовательский элемент управления, который работает как базовый веб-браузер.

Для добавления любой сборки, которая может быть вызвана из *XAML* -файла, можно использовать тот же процесс.

## <a name="add-a-wpf-user-control-to-the-solution"></a>Добавление пользовательского элемента управления WPF в решение

Сначала добавьте пользовательский элемент управления Windows Presentation Foundation (WPF) в решение начальной страницы.

1. Создайте начальную страницу, используя созданную в статье [Создание настраиваемой начальной страницы](../extensibility/creating-a-custom-start-page.md).

2. В **Обозреватель решений** щелкните решение правой кнопкой мыши, выберите **Добавить**, а затем — **Новый проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** или **Visual C#** и выберите пункт **Windows**. В средней области выберите **Библиотека пользовательских элементов управления WPF**.

4. Присвойте элементу имя `WebUserControl` и нажмите кнопку **ОК**.

## <a name="implement-the-user-control"></a>Реализация пользовательского элемента управления

Чтобы реализовать пользовательский элемент управления WPF, создайте пользовательский интерфейс в XAML, а затем напишите события кода программной части в C# или другой язык .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Написание XAML для пользовательского элемента управления

1. Откройте файл XAML для пользовательского элемента управления. В `<Grid>` элементе добавьте следующие определения строк в элемент управления.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. В элемент Main `<Grid>` добавьте следующий новый `<Grid>` элемент, который содержит текстовое поле для ввода веб-адресов и кнопку для установки нового адреса.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Добавьте следующий кадр в элемент верхнего уровня `<Grid>` сразу после `<Grid>` элемента, содержащего кнопку и текстовое поле.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. В следующем примере показан завершенный XAML для пользовательского элемента управления.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Написание событий кода программной части для пользовательского элемента управления

1. В конструкторе XAML дважды щелкните кнопку **Set Address (задать адрес** ), добавленную в элемент управления.

    Файл *UserControl1. CS* откроется в редакторе кода.

2. Заполните обработчик событий SetButton_Click следующим образом.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Этот код задает веб-адрес, введенный в текстовом поле в качестве целевого объекта для веб-браузера. Если адрес является недопустимым, код выдает ошибку.

3. Необходимо также выполнить обработку события WebFrame_Navigated:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Создайте решение.

## <a name="add-the-user-control-to-the-start-page"></a>Добавление пользовательского элемента управления на начальную страницу

Чтобы сделать этот элемент управления доступным для проекта начальной страницы, в файле проекта начальной страницы добавьте ссылку на новую библиотеку элементов управления. Затем можно добавить элемент управления в разметку XAML начальной страницы.

1. В **Обозреватель решений** в проекте начальной страницы щелкните правой кнопкой мыши элемент **ссылки** и выберите команду **Добавить ссылку**.

2. На вкладке **проекты** выберите элемент **управления UserControl** и нажмите кнопку **ОК**.

3. В меню **Сборка** выберите **Собрать решение**.

    При построении решения пользовательский элемент управления становится доступным для IntelliSense для других файлов в решении.

    Чтобы добавить элемент управления в разметку XAML начальной страницы, добавьте ссылку на пространство имен в сборку, а затем поставьте элемент управления на страницу.

### <a name="to-add-the-control-to-the-markup"></a>Добавление элемента управления в разметку

1. В **Обозреватель решений** откройте *XAML* -файл начальной страницы.

2. В области **XAML** добавьте следующее объявление пространства имен в элемент верхнего уровня <xref:System.Windows.Controls.Grid> .

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. В области **XAML** прокрутите до \<Grid> раздела.

    Раздел содержит <xref:System.Windows.Controls.TabControl> элемент в <xref:System.Windows.Controls.Grid> элементе.

4. Добавьте \<TabControl> элемент \<TabItem> , содержащий ссылку на пользовательский элемент управления.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Теперь можно протестировать элемент управления.

## <a name="test-a-manually-created-custom-start-page"></a>Тестирование настраиваемой начальной страницы, созданной вручную

1. Скопируйте файл XAML и все вспомогательные текстовые файлы или файлы разметки в папку *%UserProfile%\My Documents\Visual Studio 2015 \ startpages \\* .

2. Если начальная страница ссылается на любые элементы управления или типы в сборках, которые не установлены в Visual Studio, скопируйте сборки и вставьте их в _папку установки Visual Studio_**\Common7\IDE\PrivateAssemblies \\**.

3. В командной строке Visual Studio введите команду **devenv/Рутсуффикс exp** , чтобы открыть экспериментальный экземпляр Visual Studio.

4. В экспериментальном экземпляре перейдите на страницу **Сервис**  >  **Параметры**  >  **Среда**  >   и выберите файл XAML в раскрывающемся списке **настроить начальную страницу** .

5. В меню **Вид** выберите пункт **Начальная страница**.

    Должна отобразиться настраиваемая Начальная страница. Если вы хотите изменить какие-либо файлы, необходимо закрыть экспериментальный экземпляр, внести изменения, скопировать и вставить измененные файлы, а затем повторно открыть экспериментальный экземпляр для просмотра изменений.

## <a name="see-also"></a>См. также

- [Элементы управления контейнера WPF](/previous-versions/bb675291(v=vs.110))
- [Пошаговое руководство. Добавление пользовательского XAML-кода на начальную страницу](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)