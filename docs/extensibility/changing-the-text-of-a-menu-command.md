---
title: Изменение текста команды меню | Документация Майкрософт
description: Узнайте, как изменить текстовую метку команды меню с помощью службы Именукоммандсервице, просмотрев этот пример кода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 47389352e0491c20b7eb6409c36091179bf967d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068067"
---
# <a name="change-the-text-of-a-menu-command"></a>Изменение текста команды меню
В следующих шагах показано, как изменить текстовую метку команды меню с помощью <xref:System.ComponentModel.Design.IMenuCommandService> службы.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Изменение метки команды меню с помощью Именукоммандсервице

1. Создайте проект VSIX с именем `MenuText` с помощью команды меню с именем **чанжеменутекст**. Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. В файле *vsct* добавьте `TextChanges` флаг в команду меню, как показано в следующем примере.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. В файле *чанжеменутекст. CS* Создайте обработчик событий, который будет вызываться перед отображением команды меню.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    Вы также можете обновить состояние команды меню в этом методе, изменив <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> свойства, и <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> объекта.

4. В конструкторе Чанжеменутекст замените исходную инициализацию команды и код размещения кодом, который создает <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (а не `MenuCommand` ), который представляет команду меню, добавляет <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчик событий и передает команду меню в службу команд меню.

    Вот как это должно выглядеть:

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.

6. В меню **Сервис** должна отобразиться команда с именем **Invoke чанжеменутекст**.

7. Щелкните команду. Должно отобразиться окно с сообщением о том, что **менуитемкаллбакк** был вызван. Когда вы откроете окно сообщения, вы увидите, что имя команды в меню Сервис теперь является **новым текстом**.
