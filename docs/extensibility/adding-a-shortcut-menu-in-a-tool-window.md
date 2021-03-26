---
title: Добавление контекстного меню в окне инструментов | Документация Майкрософт
description: Узнайте, как добавить контекстное меню в окно инструментов в Visual Studio, которое появляется при щелчке правой кнопкой мыши на кнопке, текстовом поле или на фоне окна.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3ba0eb2324812ca7536b361d602bb683d627c743
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097621"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Добавление контекстного меню в окно инструментов
В этом пошаговом руководстве в окне инструментов помещается контекстное меню. Контекстное меню — это меню, которое появляется, когда пользователь щелкает правой кнопкой мыши кнопку, текстовое поле или фон окна. Команды в контекстном меню ведут себя так же, как команды в других меню или на панелях инструментов. Для поддержки контекстного меню укажите его в *vsct* -файле и отобразите в ответ на щелчок правой кнопкой мыши.

Окно инструментов состоит из пользовательского элемента управления WPF в пользовательском классе окна инструментов, который наследует от <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .

В этом пошаговом руководстве показано, как создать контекстное меню в виде меню Visual Studio, объявляя пункты меню в *vsct* -файле, а затем используя управляемую платформу пакетов для их реализации в классе, который определяет окно инструментов. Такой подход упрощает доступ к командам Visual Studio, элементам пользовательского интерфейса и модели объектов автоматизации.

Кроме того, если контекстное меню не будет иметь доступ к функциональным возможностям Visual Studio, можно использовать <xref:System.Windows.FrameworkElement.ContextMenu%2A> свойство элемента XAML в пользовательском элементе управления. Дополнительные сведения см. в разделе [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Предварительные требования
Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Создание пакета контекстного меню окна инструментов

1. Создайте проект VSIX с именем `TWShortcutMenu` и добавьте в него шаблон окна инструментов с именем **шорткутмену** . Дополнительные сведения о создании окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Указание контекстного меню
Контекстное меню, как показано в этом пошаговом руководстве, позволяет пользователю выбрать цвет из списка цветов, используемых для заполнения окна инструментов.

1. В *шорткутменупаккаже. vsct* найдите в элементе GuidSymbol с именем гуидшорткутменупаккажекмдсет и объявите контекстное меню, группу контекстного меню и пункты меню. Теперь элемент GuidSymbol должен выглядеть следующим образом:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Непосредственно перед элементом Buttons создайте элемент Menus и затем определите контекстное меню.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Контекстное меню не имеет родителя, так как оно не является частью меню или панели инструментов.

3. Создайте элемент Groups с элементом группы, который содержит элементы контекстного меню, и свяжите группу с контекстным меню.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. В элементе Buttons (кнопки) определите отдельные команды, которые будут отображаться в контекстном меню. Элемент Buttons должен выглядеть следующим образом:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. В *шорткутменукомманд. CS* Добавьте определения для идентификатора GUID набора команд, контекстного меню и пунктов меню.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Это те же идентификаторы команд, которые определены в разделе символов файла *шорткутменупаккаже. vsct* . Контекстная группа не указана здесь, так как она необходима только в *vsct* -файле.

## <a name="implementing-the-shortcut-menu"></a>Реализация контекстного меню
 В этом разделе реализуется контекстное меню и его команды.

1. В *шорткутмену. CS* окно инструментов может получить службу команд меню, но содержащийся в ней элемент управления не может. Ниже показано, как сделать командную службу меню доступной для пользовательского элемента управления.

2. В *шорткутмену. CS* добавьте следующие директивы using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Переопределите метод Initialize () окна инструментов, чтобы получить службу команд меню и добавить элемент управления, передав командную службу меню конструктору:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. В конструкторе окна инструментов Шорткутмену удалите строку, которая добавляет элемент управления. Теперь конструктор должен выглядеть следующим образом:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. В *шорткутменуконтрол. XAML. CS* Добавьте закрытое поле для службы команд меню и измените конструктор элемента управления, чтобы он занимал службу команд меню. Затем с помощью службы команд меню добавьте команды контекстного меню. Конструктор Шорткутменуконтрол теперь должен выглядеть, как в следующем коде. Обработчик команд будет определен позже.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. В *шорткутменуконтрол. XAML* добавьте <xref:System.Windows.UIElement.MouseRightButtonDown> событие в элемент верхнего уровня <xref:System.Windows.Controls.UserControl> . Файл XAML теперь должен выглядеть следующим образом:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. В *шорткутменуконтрол. XAML. CS* добавьте заглушку для обработчика событий.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Добавьте следующие директивы using в один и тот же файл:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Реализуйте `MyToolWindowMouseRightButtonDown` событие следующим образом.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    При этом создается <xref:System.ComponentModel.Design.CommandID> объект для контекстного меню, определяется расположение щелчка мыши и открывается контекстное меню в этом расположении с помощью <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> метода.

10. Реализуйте обработчик команд.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    В этом случае только один метод обрабатывает события для всех пунктов меню, определяя <xref:System.ComponentModel.Design.CommandID> и соответствующим образом устанавливая цвет фона. Если пункты меню содержали несвязанные команды, то для каждой команды был создан отдельный обработчик событий.

## <a name="test-the-tool-window-features"></a>Тестирование функций окна инструментов

1. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

2. В экспериментальном экземпляре выберите **представление/другие окна**, а затем щелкните **шорткутмену**. При этом должно отобразиться окно инструментов.

3. Щелкните правой кнопкой мыши в тексте окна инструментов. Должно отобразиться контекстное меню со списком цветов.

4. Выберите цвет в контекстном меню. Цвет фона окна инструментов должен быть изменен на выбранный цвет.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
- [Использование и предоставление служб](../extensibility/using-and-providing-services.md)
