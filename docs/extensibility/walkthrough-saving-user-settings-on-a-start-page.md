---
title: Пошаговое руководство. Сохранение параметров пользователя на начальной странице | Документация Майкрософт
description: Узнайте, как сохранить параметры пользователя для начальной страницы, сохранив параметр в реестре с помощью этого пошагового руководства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2f7dddfca06d7bc475286c73087828305464daa5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217220"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Пошаговое руководство. Сохранение параметров пользователя на начальной странице

Вы можете сохранить параметры пользователя для начальной страницы. Следуя этому пошаговому руководству, можно создать элемент управления, который сохраняет параметр в реестре при нажатии пользователем кнопки, а затем извлекает этот параметр при каждой загрузке начальной страницы. Поскольку шаблон проекта начальной страницы включает настраиваемый пользовательский элемент управления, а XAML начальной страницы по умолчанию вызывает этот элемент управления, изменять начальную страницу не нужно.

Хранилище параметров, создаваемое в этом пошаговом руководстве, представляет собой экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> интерфейса, который при вызове считывает и выполняет запись в следующий раздел реестра: **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName>**

Когда она выполняется в экспериментальном экземпляре Visual Studio, хранилище параметров считывает и выполняет запись в **HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ \<CollectionName> .**

Дополнительные сведения о сохранении параметров см. в разделе [расширение параметров пользователя и параметров](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).
>
> Шаблон проекта начальной страницы можно скачать с помощью **диспетчера расширений**.

## <a name="set-up-the-project"></a>Настройка проекта

1. Создайте проект начальной страницы, как описано в разделе [Создание настраиваемой начальной страницы](creating-a-custom-start-page.md). Назовите проект **савемисеттингс**.

2. В **Обозреватель решений** добавьте следующие ссылки на сборки в проект стартпажеконтрол:

    - EnvDTE

    - EnvDTE80

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. Shell. Interop. 11.0

3. Откройте *MyControl. XAML*.

4. В области XAML в <xref:System.Windows.Controls.UserControl> определении элемента верхнего уровня добавьте следующее объявление события после объявлений пространства имен.

    ```xml
    Loaded="OnLoaded"
    ```

5. В области конструктора щелкните основную область элемента управления и нажмите клавишу **Delete**.

     Этот шаг удаляет <xref:System.Windows.Controls.Border> элемент и все его элементы и оставляет только элемент верхнего уровня <xref:System.Windows.Controls.Grid> .

6. Перетащите элемент управления из **области элементов** в <xref:System.Windows.Controls.StackPanel> сетку.

7. Теперь перетащите объект <xref:System.Windows.Controls.TextBlock> , объект <xref:System.Windows.Controls.TextBox> и кнопку в <xref:System.Windows.Controls.StackPanel> .

8. Добавьте атрибут **x:Name** для <xref:System.Windows.Controls.TextBox> , и `Click` для события <xref:System.Windows.Controls.Button> , как показано в следующем примере.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Реализация пользовательского элемента управления

1. В области XAML щелкните правой кнопкой мыши `Click` атрибут <xref:System.Windows.Controls.Button> элемента и выберите команду **Переход к обработчику события**.

     На этом шаге открывается объект *MyControl. XAML. CS* и создается обработчик заглушки для `Button_Click` события.

2. Добавьте следующие `using` директивы в начало файла.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs" id="Snippet11":::

3. Добавьте закрытое `SettingsStore` свойство, как показано в следующем примере.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Это свойство сначала получает ссылку на <xref:EnvDTE80.DTE2> интерфейс, содержащий объектную модель автоматизации, из <xref:System.Windows.FrameworkElement.DataContext%2A> пользовательского элемента управления, а затем использует DTE для получения экземпляра <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> интерфейса. Затем он использует этот экземпляр для возврата текущих параметров пользователя.

4. Заполните `Button_Click` событие следующим образом.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     При этом содержимое текстового поля записывается в поле "Мисеттинг" в коллекции "MySettings" в реестре. Если коллекция не существует, она создается.

5. Добавьте следующий обработчик для `OnLoaded` события пользовательского элемента управления.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Этот код задает для текстового поля текущее значение "Мисеттинг".

6. Создайте пользовательский элемент управления.

7. В **Обозреватель решений** откройте *source. extension. vsixmanifest*.

8. В редакторе манифеста задайте для параметра **Название продукта** значение **сохранить начальную страницу параметров**.

     Этот компонент задает имя начальной страницы в том виде, в котором оно отображается в списке **Настройка начальной страницы** в диалоговом окне **Параметры** .

9. Сборка *StartPage. XAML*.

## <a name="test-the-control"></a>Тестирование элемента управления

1. Нажмите клавишу **F5**.

     Откроется экспериментальный экземпляр Visual Studio.

2. В экспериментальном экземпляре в меню **Сервис** выберите пункт **Параметры**.

3. В узле **Среда** щелкните **Запуск**, а затем в списке **Настройка начальной страницы** выберите **[установлено расширение] сохранить начальную страницу параметров**.

     Нажмите кнопку **ОК**.

4. Закройте начальную страницу, если она открыта, а затем в меню **вид** выберите пункт **Начальная страница**.

5. На начальной странице перейдите на вкладку **MyControl** .

6. В текстовом поле введите **Cat** и нажмите кнопку **Сохранить мой параметр**.

7. Закройте начальную страницу и снова откройте ее.

     Слово «Кот» должно отображаться в текстовом поле.

8. Замените слово «Cat» словом «собака». Не нажимайте кнопку.

9. Закройте начальную страницу и снова откройте ее.

     Слово «собака» должно отображаться в текстовом поле, даже если вы не сохранили параметр, поскольку Visual Studio сохраняет окна инструментов в памяти, даже если они закрыты, пока Visual Studio не закроется.

10. Закройте экспериментальный экземпляр Visual Studio.

11. Нажмите клавишу **F5** , чтобы снова открыть экспериментальный экземпляр.

12. Слово «Кот» должно отображаться в текстовом поле.

## <a name="next-steps"></a>Дальнейшие действия

Этот пользовательский элемент управления можно изменить, чтобы сохранить и получить любое количество пользовательских параметров, используя разные значения из разных обработчиков событий для получения и задания `SettingsStore` Свойства. Если `propertyName` для каждого вызова используется другой параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , значения не перезапишут друг друга в реестре.

## <a name="see-also"></a>См. также раздел

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Добавление команд Visual Studio на начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
