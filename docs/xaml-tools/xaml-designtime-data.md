---
title: Использование данных времени разработки в Конструкторе XAML в Visual Studio
description: Узнайте, как использовать данные времени разработки в XAML.
ms.date: 04/22/2021
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: 47bf978bc32c651cb90130ecc90517bfe1c29cdd
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761112"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Использование данных времени разработки в Конструкторе XAML в Visual Studio

Некоторые макеты трудно визуализировать без данных. В этом документе мы рассмотрим один из подходов, который разработчики классических проектов могут использовать для макетирования данных в Конструкторе XAML. Этот подход предусматривает использование существующего игнорируемого пространства имен "d:". С его помощью можно быстро добавлять данные времени разработки на страницы и в элементы управления без необходимости создавать целый макетированный объект ViewModel либо просто проверять, как изменение свойства может повлиять на приложение, чтобы не переживать о возможных последствиях для сборок выпуска. Все данные d: используются только Конструктором XAML. Значения игнорируемого пространства имен не компилируются в приложение.

> [!NOTE]
> Если вы используете Xamarin.Forms, см. статью о [данных времени разработки в Xamarin.Forms](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data).

## <a name="design-time-data-basics"></a>Основные сведения о данных времени разработки

Данные времени разработки — это макетированные данные, которые задаются, чтобы упростить визуализацию элементов управления в Конструкторе XAML. Чтобы приступить к работе, добавьте следующие строки кода в заголовок документа XAML, если их еще нет:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

После добавления пространств имен можно указывать `d:` перед любым атрибутом или элементом управления, чтобы он отображался только в Конструкторе XAML, но не во время выполнения.

Например, можно добавить текст в элемент TextBlock, к которому обычно привязаны данные.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![Данные времени разработки в виде текста в элементе TextBlock](media\xaml-design-time-textblock.png "Данные времени разработки в виде текста в элементе Label")](media\xaml-design-time-textblock.png#lightbox)

Если бы в этом примере не было атрибута `d:Text`, в Конструкторе XAML в элементе TextBlock не отображалось бы никакого содержимого. Теперь же отображается текст "Name!" там, где во время выполнения в элементе TextBlock будут реальные данные.

`d:` можно использовать с атрибутами для любого элемента управления .NET Core UWP или WPF, такими как цвет, размер шрифта и интервал. Его можно также добавить в сам элемент управления.

```xml
<d:Button Content="Design Time Button" />
```

[![Данные времени разработки для элемента управления Button](media\xaml-design-time-button.png "Данные времени разработки для элемента управления Button")](media\xaml-design-time-button.png#lightbox)

В этом примере кнопка отображается только во время разработки. Используйте этот метод, чтобы добавить заполнитель для пользовательского элемента управления и опробовать различные элементы управления. Во время выполнения все атрибуты и элементы управления `d:` будут пропускаться.

## <a name="preview-images-at-design-time"></a>Предварительный просмотр изображений во время разработки

Можно задать источник времени разработки для изображений, которые привязаны к странице или загружаются динамически. Добавьте в проект изображение, которое требуется отображать в Конструкторе XAML. Затем это изображение можно отобразить в Конструкторе XAML во время разработки:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> Изображение в этом примере должно существовать в решении.

## <a name="design-time-data-for-listviews"></a>Данные времени разработки для ListView

Элемент ListView — это популярный способ отображения данных в классическом приложении. Однако его сложно визуализировать без каких-либо данных. С помощью этой возможности вы можете создавать встроенные данные времени разработки (ItemSource или Items). В Конструкторе XAML содержимое этого массива отображается в ListView во время разработки.

### <a name="wpf-net-core-example"></a>Пример WPF .NET Core
Чтобы использовать тип system:String, необходимо включить `xmlns:system="clr-namespace:System;assembly=mscorlib` в заголовок XAML.

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![Данные времени разработки для ListView](media\xaml-design-time-listview-strings.png "Данные времени разработки для ListView")](media\xaml-design-time-listview-strings.png#lightbox)

В предыдущем примере показан ListView с тремя элементами TextBlock в Конструкторе XAML.

Можно также создать массив объектов данных. Например, открытые свойства объекта данных `City` можно конструировать как данные времени разработки.

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

Чтобы использовать этот класс в XAML, необходимо импортировать пространство имен в корневой узел.

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![Фактическая модель в данных времени разработки для ListView](media\xaml-design-time-listview-models.png "Данные времени разработки фактической модели для ListView")](media\xaml-design-time-listview-models.png#lightbox)

Преимущество заключается в возможности привязки элементов управления к статической версии модели времени разработки.

### <a name="uwp-example"></a>Пример UWP

x:Array не поддерживается в UWP. Поэтому мы можем использовать `<d:ListView.Items>`. Чтобы использовать тип system:String, необходимо включить `http://schemas.microsoft.com/winfx/2009/xaml` в заголовок XAML.

```xml
    <StackPanel>
        <ListView>
            <d:ListView.Items>
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </d:ListView.Items>
        </ListView>
    </StackPanel>
```

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Использование данных времени разработки с пользовательскими типами и свойствами

Эта функция по умолчанию работает только с элементами управления и свойствами платформы. В этом разделе мы рассмотрим действия, необходимые для того, чтобы использовать собственные элементы управления в качестве элементов управления времени разработки. Эта новая возможность доступна клиентам, использующим Visual Studio 2019 версии [16.8](/visualstudio/releases/2019/release-notes/) или более позднюю версию. Это можно сделать, если выполнены три условия.

- Пользовательское пространство имен xmlns

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Версия вашего пространства имен, используемая во время разработки. Чтобы сделать это, достаточно добавить в конце /design.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- Добавление префикса времени разработки в пространство имен mc:Ignorable

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

После выполнения всех этих действий вы можете использовать префикс `myDesignTimeControls` для создания элементов управления времени разработки.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Создание пользовательского пространства имен xmlns

Чтобы создать пользовательское пространство имен xmlns в WPF .NET Core, необходимо сопоставить пользовательское пространство имен XML с пространством имен CLR, в котором находятся элементы управления. Это можно сделать, добавив атрибут уровня сборки `XmlnsDefinition` в файл `AssemblyInfo.cs`. Этот файл находится в корневой иерархии проекта.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Диагностика

Если возникла проблема, которая не указана в этом разделе, сообщите нам об этом с помощью средства [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio.md).

### <a name="requirements"></a>Требования

- Для использования данных времени разработки требуется Visual Studio 2019 версии [16.7](/visualstudio/releases/2019/release-notes-v16.7) или более поздней.

- Поддерживаются классические проекты Windows, предназначенные для Windows Presentation Foundation (WPF) для .NET Core и UWP. Эта функция также доступна для .NET Framework в [канале предварительной версии](/visualstudio/releases/2019/release-notes-preview). Чтобы включить ее, откройте раздел **Инструменты** > **Параметры** > **Среда** > **Предварительные версии функции**, выберите **Создать Конструктор XAML WPF для .NET Framework** и перезапустите Visual Studio.

- Начиная с Visual Studio 2019 версии 16.7 эта функция работает со всеми встроенными элементами управления платформ WPF и UWP. Поддержка элементов управления сторонних разработчиков теперь доступна в [выпуске 16.8](/visualstudio/releases/2019/release-notes/).

### <a name="the-xaml-designer-stopped-working"></a>Конструктор XAML перестал работать

Попробуйте закрыть и снова открыть XAML-файл, а также очистить и перестроить проект.

## <a name="see-also"></a>См. также раздел

- [Использование данных времени разработки со средством предварительного просмотра Xamarin.Forms](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [XAML в приложениях WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML в приложениях UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML в приложениях Xamarin.Forms](/xamarin/xamarin-forms/xaml/)