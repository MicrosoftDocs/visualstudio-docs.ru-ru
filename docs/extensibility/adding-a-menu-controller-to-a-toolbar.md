---
title: Добавление контроллера меню на панель инструментов | Документация Майкрософт
description: Узнайте, как создать контроллер меню и добавить его на панель инструментов окна инструментов в Visual Studio, а затем реализовать команды контроллера меню и протестировать его.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 304f4ea11abc332c01603f96b6b67c0bd22e38c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060072"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Добавление контроллера меню на панель инструментов
В этом пошаговом руководстве выполняется сборка в пошаговом руководстве по [добавлению панели инструментов в окно](../extensibility/adding-a-toolbar-to-a-tool-window.md) инструментов и показано, как добавить контроллер меню на панель инструментов окна инструментов. Приведенные здесь действия также можно применить к панели инструментов, созданной в пошаговом руководстве [Добавление панели инструментов](../extensibility/adding-a-toolbar.md) .

Контроллер меню является разделенным элементом управления. В левой части контроллера меню отображается последняя использованная команда, которую можно запустить, щелкнув ее. В правой части контроллера меню находится стрелка, при нажатии которой открывается список дополнительных команд. При выборе команды в списке выполняется команда, которая заменяет команду в левой части контроллера меню. Таким образом, контроллер меню действует как кнопка, которая всегда показывает последнюю использованную команду из списка.

Контроллеры меню могут отображаться в меню, но чаще всего используются на панелях инструментов.

## <a name="prerequisites"></a>Предварительные требования
Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Создание контроллера меню

1. Выполните процедуры, описанные в разделе [Добавление панели инструментов в окно инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md) , чтобы создать окно инструментов с панелью инструментов.

2. В *твтесткоммандпаккаже. vsct* перейдите в раздел символы. В элементе GuidSymbol с именем **гуидтвтесткоммандпаккажекмдсет** объявите контроллер меню, группу контроллера меню и три пункта меню.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. В разделе меню после последней записи меню Определите контроллер меню в виде меню.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    `TextChanges` `TextIsAnchorCommand` Флаги и должны быть включены, чтобы разрешить контроллеру меню отражать последнюю выбранную команду.

4. В разделе группы после последней записи группы добавьте группу контроллер меню.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Если установить в качестве родительского контроллера меню, все команды, помещенные в эту группу, отображаются в контроллере меню. `priority`Атрибут опускается, что задает для него значение по умолчанию 0, так как это единственная группа в контроллере меню.

5. В разделе кнопки после последней записи кнопки добавьте элемент Button для каждого из пунктов меню.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. На этом этапе можно просмотреть контроллер меню. Выполните сборку решения и запустите отладку. Вы должны увидеть экспериментальный экземпляр.

   1. В меню **вид/другие окна** откройте окно **инструментов теста**.

   2. Контроллер меню появится на панели инструментов окна инструментов.

   3. Щелкните стрелку в правой части контроллера меню, чтобы просмотреть три возможные команды.

      Обратите внимание, что при нажатии команды название контроллера меню изменится на отображение этой команды. В следующем разделе мы добавим код для активации этих команд.

## <a name="implement-the-menu-controller-commands"></a>Реализация команд контроллера меню

1. В *твтесткоммандпаккажегуидс. CS* добавьте идентификаторы команд для трех пунктов меню после существующих идентификаторов команд.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. В *твтесткомманд. CS* добавьте следующий код в начало `TWTestCommand` класса.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. В конструкторе Твтесткомманд после последнего вызова `AddCommand` метода добавьте код для маршрутизации событий для каждой команды с помощью одних и тех же обработчиков.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Добавьте обработчик событий в класс **твтесткомманд** , чтобы пометить выбранную команду как отмеченную.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Добавьте обработчик событий, отображающий MessageBox, когда пользователь выбирает команду в контроллере меню:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Тестирование контроллера меню

1. Выполните сборку решения и запустите отладку. Вы должны увидеть экспериментальный экземпляр.

2. Откройте окно " **тест** " в меню " **вид/другие окна** ".

    Контроллер меню появится в панели инструментов в окне инструментов и отобразит **элемент MC 1**.

3. Нажмите кнопку Контролер меню слева от стрелки.

    Вы увидите три элемента, первый из которых выбран и имеет выделенное поле вокруг его значка. Щелкните **элемент MC 3**.

    Появится диалоговое окно с сообщением **, выбранным в меню элемент контроллера. 3**. Обратите внимание, что сообщение соответствует тексту на кнопке контроллера меню. Кнопка контроллер меню теперь отображает **элемент MC 3**.

## <a name="see-also"></a>См. также
- [Добавление панели инструментов в окно инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)
