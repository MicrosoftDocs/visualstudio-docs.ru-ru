---
title: Добавление команд Visual Studio на начальную страницу | Документация Майкрософт
description: Узнайте о различных способах привязки команд Visual Studio к объектам XAML на настраиваемой начальной странице в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4e2ec238d3cb8c2e7d843018fc45e97207c6d5f4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097530"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Добавление команд Visual Studio на начальную страницу

При создании настраиваемой начальной страницы к ней можно добавить команды Visual Studio. В этом документе рассматриваются различные способы привязки команд Visual Studio к объектам XAML на начальной странице.

Дополнительные сведения о командах в XAML см. в разделе [Общие сведения о командах](/dotnet/framework/wpf/advanced/commanding-overview) .

## <a name="add-commands-from-the-command-well"></a>Добавление команд с помощью команды

Начальная страница, созданная при [создании настраиваемой начальной страницы](../extensibility/creating-a-custom-start-page.md) , добавила <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> пространства имен и, как показано ниже.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Добавьте еще одно пространство имен для Microsoft. VisualStudio. Shell из сборки *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (В проекте может потребоваться добавить ссылку на эту сборку.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Можно использовать `vscom:` псевдоним для привязки команд Visual Studio к элементам управления XAML на странице, присвоив <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> свойству элемента управления значение `vscom:VSCommands.ExecuteCommand` . Затем можно присвоить <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> свойству имя выполняемой команды, как показано в следующем примере.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> `x:`Псевдоним, который ссылается на схему XAML, требуется в начале всех команд.

 Можно задать `Command` для свойства значение любой команды, доступ к которой можно получить из **командного** окна. Список доступных команд см. в разделе [псевдонимы команд Visual Studio](../ide/reference/visual-studio-command-aliases.md).

 Если команда для добавления требует дополнительного параметра, ее можно добавить в значение `CommandParameter` Свойства. Отделяйте параметры от команд с помощью пробелов, как показано в следующем примере.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Вызов расширений из командной строки
 Команды можно вызывать из зарегистрированных пакетов VSPackage с использованием того же синтаксиса, который используется для вызова других команд Visual Studio. Например, если установленный пакет VSPackage добавляет в меню **вид** команду **Домашняя страница** , можно вызвать эту команду, задав для значение `CommandParameter` `View.HomePage` .

> [!NOTE]
> При вызове команды, связанной с VSPackage, пакет должен быть загружен при вызове команды.

## <a name="add-commands-from-assemblies"></a>Добавление команд из сборок
 Чтобы вызвать команду из сборки или получить доступ к коду в VSPackage, не связанном с командой меню, необходимо создать псевдоним для сборки, а затем вызвать псевдоним.

### <a name="to-call-a-command-from-an-assembly"></a>Вызов команды из сборки

1. В решении добавьте ссылку на сборку.

2. В верхней части файла *StartPage. XAML* добавьте директиву пространства имен для сборки, как показано в следующем примере.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Вызовите команду, задав `Command` свойство объекта XAML, как показано в следующем примере.

     Кода

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Необходимо скопировать сборку и вставить ее в *.. \\ {Папка установки Visual Studio} \Common7\IDE\PrivateAssemblies \* , чтобы убедиться, что она загружена перед вызовом.

## <a name="add-commands-with-the-dte-object"></a>Добавление команд с помощью объекта DTE
 Доступ к объекту DTE можно получить с начальной страницы как в разметке, так и в коде.

 В разметке доступ к нему можно получить с помощью синтаксиса [расширения разметки Binding](/dotnet/framework/wpf/advanced/binding-markup-extension) для вызова <xref:EnvDTE.DTE> объекта. Этот подход можно использовать для привязки к простым свойствам, таким как те, которые возвращают коллекции, но нельзя выполнить привязку к методам или службам. В следующем примере показан <xref:System.Windows.Controls.TextBlock> элемент управления, привязанный к <xref:EnvDTE._DTE.Name%2A> свойству, и <xref:System.Windows.Controls.ListBox> элемент управления, перечисляющий <xref:EnvDTE.Window.Caption%2A> свойства коллекции, возвращаемой <xref:EnvDTE._DTE.Windows%2A> свойством.

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 Пример см. в разделе [Пошаговое руководство. Сохранение параметров пользователя на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>См. также

- [Добавление пользовательского элемента управления на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md)
