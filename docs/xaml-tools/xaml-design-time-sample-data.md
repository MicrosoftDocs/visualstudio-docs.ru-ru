---
title: Использование демонстрационных данных времени разработки с Конструктор XAML в Visual Studio
description: Узнайте, как использовать демонстрационные данные времени разработки в XAML.
ms.date: 05/28/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: a987435d454771bdecf078e78af089405718d261
ms.sourcegitcommit: 5366c6bca3fb217a2fbf847998387578f51ec45c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748056"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Использование демонстрационных данных времени разработки с Конструктор XAML в Visual Studio

Некоторые элементы управления, относящиеся к данным, такие как ListView, ListBox или DataGrid, трудно визуализировать без данных. В этом документе мы рассмотрим новый подход, позволяющий разработчикам работать над проектами **.NET Core WPF** или проектами **платформа .NET Framework WPF** с новым конструктором для включения демонстрационных данных в этих элементах управления. 

## <a name="sample-data-feature-basics"></a>Основные сведения о функциях образцов данных

Образец данных предназначен только для визуализации во время разработки. Это означает, что они отображаются только в конструкторе XAML, а не в работающем приложении. Таким образом, он применяется к версии времени разработки свойства ItemsSource `d:ItemsSource` . Для работы с образцом данных требуется пространство имен времени разработки. Чтобы приступить к работе, добавьте следующие строки кода в заголовок документа XAML, если их еще нет:

> [!NOTE]
> Дополнительные сведения о свойствах времени разработки в XAML см. в статье [свойства времени разработки XAML](/xaml/xaml-tools/xaml/xaml-designtime-data.md) .

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

После добавления пространств имен можно использовать `d:ItemsSource="{d:SampleData}"` для включения демонстрационных данных в ListView, ListBox или DataGrid. Пример:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![Выборка данных с помощью DataGrid](media\xaml-sample-data-empty-datagrid.png "Образец данных, включенный в DataGrid")](media\xaml-sample-data-empty-datagrid.png#lightbox)

В этом примере без `d:ItemsSource="{d:SampleData}"` конструктор XAML будет отображаться пустой элемент DataGrid. Вместо этого в `d:SampleData` нем отображаются созданные образцы данных по умолчанию.

По умолчанию отображается 5 элементов. Однако можно использовать свойство **ItemCount** , чтобы указать, сколько элементов вы хотите отобразить. Например: `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>Демонстрационные данные работают с DataTemplates

Образцы данных работают для элементов управления ListBox, ListView или DataGrid при использовании шаблонов данных. Функция образца данных анализирует DataTemplate и попытается создать соответствующие для него данные. Образцы данных будут создаваться только для элементов в шаблонах DataTemplate, использующих привязки. Образцы данных будут создаваться, даже если у привязок еще нет источника.
Пример:

```xml
<ListView d:ItemsSource="{d:SampleData ItemCount=3}">
     <ListView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <Image Width="50" Source="{Binding ProfilePicture}"/>
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{Binding FirstName}" Margin="5"/>
                    <Label Content="{Binding LastName}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

[![Пример ListView данных с помощью DataTemplate](media\xaml-sample-data-templated-listview.png "Демонстрационные данные, используемые в ListView с помощью DataTemplate")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>Включение демонстрационных данных с предложенными действиями

Чтобы легко включить или отключить выборку данных для элемента управления из конструктора, можно использовать функцию предлагаемые действия. Предлагаемые действия — это лампочка в конструкторе, которая отображается в правом верхнем углу при выборе элемента управления. Можно включить выборку данных, выбрав элемент управления, щелкнув лампочку, а затем щелкнув `Show Sample Data` . Пример:

[![Примеры предлагаемых действий с данными](media\xaml-sample-data-suggested-actions.png "Включение демонстрационных данных с предложенными действиями")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>Пример данных с помощью Ивалуеконвертерс 

Функции выборки данных не полностью поддерживают конвертеры. Однако вы можете заставить его работать, выполнив одно или оба следующих действия:
- Убедитесь, что `Convert` функция может выполнять сценарий, где значение уже является TargetType.

- Реализуйте `ConvertBack` функцию, которая преобразует значение обратно в исходный тип. 

## <a name="troubleshooting"></a>Устранение неполадок

Если образец данных не отображает ничего или не отображает правильный тип, можно попытаться обновить конструктор или закрыть и повторно открыть страницу.

Если возникла проблема, которая не указана в этом разделе или не может быть исправлена путем обновления страницы, сообщите нам об этом с помощью средства [сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio.md) .

### <a name="requirements"></a>Требования

- Для работы с образцом данных требуется Visual Studio 2019 версии [16,10](/visualstudio/releases/2019/release-notes-v16.10) или более поздней.

- Поддерживает проекты Windows для настольных компьютеров, предназначенные для Windows Presentation Foundation (WPF) для .NET Core или платформа .NET Framework при использовании нового конструктора. Чтобы включить новый конструктор для платформа .NET Framework перейдите в меню Сервис > параметры > среда > Предварительная версия, выберите новый Конструктор XAML WPF для платформа .NET Framework а затем перезапустите Visual Studio.

## <a name="see-also"></a>См. также раздел

- [Свойства времени разработки XAML](/xaml/xaml-tools/xaml/xaml-designtime-data)
- [XAML в приложениях WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML в приложениях UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML в приложениях Xamarin.Forms](/xamarin/xamarin-forms/xaml/)