---
title: Добавление окна инструментов | Документация Майкрософт
description: Узнайте, как создать окно инструментов и интегрировать его в Visual Studio путем добавления элемента управления и панели инструментов, содержащей команду, в окно инструментов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 314a684e34c91f43abe9babe4cdd6efc8a15cc35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085524"
---
# <a name="add-a-tool-window"></a>Добавление окна инструментов

В этом пошаговом руководстве вы узнаете, как создать окно инструментов и интегрировать его в Visual Studio следующими способами.

- Добавление элемента управления в окно инструментов.

- Добавление панели инструментов в окно инструментов.

- Добавьте команду на панель инструментов.

- Реализуйте команды.

- Задайте расположение по умолчанию для окна инструментов.

## <a name="prerequisites"></a>Предварительные требования

Пакет SDK для Visual Studio входит в состав программы установки Visual Studio в качестве дополнительного компонента. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Создание окна инструментов

1. Создайте проект с именем **фирсттулвин** с помощью шаблона VSIX и добавьте пользовательский шаблон элемента окна инструментов с именем **фирсттулвиндов**.

    > [!NOTE]
    > Дополнительные сведения о создании расширения с помощью окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Добавление элемента управления в окно инструментов

1. Удалите элемент управления по умолчанию. Откройте *фирсттулвиндовконтрол. XAML* и удалите элемент " **Click Me!** ". .

2. На **панели элементов** разверните раздел **все элементы управления WPF** и перетащите элемент управления " **элемент мультимедиа** " в форму **фирсттулвиндовконтрол** . Выберите элемент управления и в окне **Свойства** назовите этот элемент **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Добавление панели инструментов в окно инструментов
Добавив панель инструментов следующим образом, вы гарантируете, что ее градиенты и цвета будут согласованы с остальной частью интегрированной среды разработки.

1. В **Обозреватель решений** откройте *фирсттулвиндовпаккаже. vsct*. Файл *. vsct* определяет графические элементы пользовательского интерфейса (GUI) в окне инструментов с помощью XML.

2. В `<Symbols>` разделе найдите `<GuidSymbol>` узел, атрибут которого `name` имеет значение `guidFirstToolWindowPackageCmdSet` . Добавьте следующие два `<IDSymbol>` элемента в список `<IDSymbol>` элементов этого узла, чтобы определить панель инструментов и группу панелей инструментов.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Непосредственно над `<Buttons>` разделом создайте `<Menus>` раздел, похожий на следующий:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Существует несколько различных видов меню. Это меню представляет собой панель инструментов в окне инструментов, определяемую его `type` атрибутом. `guid`Параметры и `id` составляют полный идентификатор панели инструментов. Как правило, в `<Parent>` меню содержится группа, содержащая. Однако панель инструментов определяется как собственная родительская. Таким образом, для элементов и используется один и тот же идентификатор `<Menu>` `<Parent>` . `priority`Атрибут имеет значение только "0".

4. Во многих случаях панели инструментов напоминают меню. Например, так как меню могут иметь группы команд, панели инструментов могут также иметь группы. (В меню группы команд разделяются горизонтальными линиями. На панелях инструментов группы не разделяются визуальными разделителями.)

    Добавьте `<Groups>` раздел, содержащий `<Group>` элемент. Определяет группу, идентификатор которой был объявлен в `<Symbols>` разделе. Добавьте `<Groups>` раздел сразу после `<Menus>` раздела.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Установив для родительского идентификатора GUID и идентификатора идентификатор GUID и идентификатор панели инструментов, вы добавите группу на панель инструментов.

## <a name="add-a-command-to-the-toolbar"></a>Добавление команды на панель инструментов

Добавьте команду на панель инструментов, которая отображается как кнопка.

1. В `<Symbols>` разделе объявите следующие элементы IDSymbol сразу после объявлений групп панелей инструментов и панелей инструментов.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Добавьте в раздел элемент Button `<Buttons>` . Этот элемент появится на панели инструментов в окне инструментов с значком **поиска** (лупа).

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. Откройте *фирсттулвиндовкомманд. CS* и добавьте следующие строки в класс сразу после существующих полей.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Это делает команды доступными в коде.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Добавление свойства MediaPlayer в Фирсттулвиндовконтрол
В обработчиках событий для элементов управления панели инструментов код должен иметь доступ к элементу управления Media Player, который является дочерним по отношению к классу Фирсттулвиндовконтрол.

В **Обозреватель решений** щелкните правой кнопкой мыши *фирсттулвиндовконтрол. XAML*, выберите пункт **Просмотреть код** и добавьте следующий код в класс фирсттулвиндовконтрол.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Создание экземпляра окна инструментов и панели инструментов
Добавьте панель инструментов и команду меню, которая вызывает диалоговое окно **открытия файла** и воспроизводит выбранный файл мультимедиа.

1. Откройте *фирсттулвиндов. CS* и добавьте следующие `using` директивы:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. В классе Фирсттулвиндов добавьте открытую ссылку на элемент управления Фирсттулвиндовконтрол.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. В конце конструктора присвойте этой переменной элемента управления только что созданный элемент управления.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Создайте экземпляр панели инструментов внутри конструктора.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. На этом этапе конструктор Фирсттулвиндов должен выглядеть следующим образом:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Добавьте команду меню на панель инструментов. В классе Фирсттулвиндовкомманд. cs добавьте следующую директиву using:

    ```csharp
    using System.Windows.Forms;
    ```

7. В классе Фирсттулвиндовкомманд добавьте следующий код в конце метода Шовтулвиндов (). Команда Буттонхандлер будет реализована в следующем разделе.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Реализация команды меню в окне инструментов

1. В классе Фирсттулвиндовкомманд добавьте метод Буттонхандлер, который вызывает диалоговое окно **открытия файла** . Если файл выбран, он воспроизводит файл мультимедиа.

2. В классе Фирсттулвиндовкомманд добавьте закрытую ссылку на окно Фирсттулвиндов, которое создается в методе Финдтулвиндов ().

    ```csharp
    private FirstToolWindow window;
    ```

3. Измените метод Шовтулвиндов (), чтобы задать определенное выше окно (чтобы обработчик команд Буттонхандлер мог получить доступ к элементу управления "окно". Ниже приведен полный метод Шовтулвиндов ().

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. Добавьте метод Буттонхандлер. Он создает OpenFileDialog для пользователя, чтобы указать файл мультимедиа для воспроизведения, а затем воспроизводит выбранный файл.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Задание расположения по умолчанию для окна инструментов

Затем укажите расположение по умолчанию в интегрированной среде разработки для окна инструментов. Сведения о конфигурации для окна инструментов находятся в файле *фирсттулвиндовпаккаже. CS* .

1. В *фирсттулвиндовпаккаже. CS* найдите <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> атрибут `FirstToolWindowPackage` класса, который передает тип фирсттулвиндов в конструктор. Чтобы указать расположение по умолчанию, необходимо добавить дополнительные параметры в конструктор, как показано ниже.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Первый именованный параметр — `Style` , а его значение — `Tabbed` , то есть окно будет вкладкой в существующем окне. Положение закрепления задается `Window` параметром n в данном случае — идентификатор GUID **Обозреватель решений**.

    > [!NOTE]
    > Дополнительные сведения о типах окон в интегрированной среде разработки см. в разделе <xref:EnvDTE.vsWindowType> .

## <a name="test-the-tool-window"></a>Тестирование окна инструментов

1. Нажмите клавишу **F5** , чтобы открыть новый экземпляр экспериментальной сборки Visual Studio.

2. В меню **вид** наведите указатель мыши на пункт **другие окна** и выберите пункт **первое окно инструментов**.

    Окно инструментов проигрывателя мультимедиа должно открываться в том же расположении, что и **Обозреватель решений**. Если он по-прежнему отображается в том же расположении, что и ранее, сбросьте макет окна (окно **или Сброс макета окна**).

3. Нажмите кнопку (она содержит значок **поиска** ) в окне инструментов. Выберите поддерживаемый звуковой или видеофайл, например *к:\виндовс\медиа\чимес.ВАВ*, и нажмите кнопку **Открыть**.

    Вы должны слышать звук подвеска.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
