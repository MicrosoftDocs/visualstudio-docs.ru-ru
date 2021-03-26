---
title: Изменение внешнего вида команды | Документация Майкрософт
description: Узнайте, как предоставить отзыв, изменяющий внешний вид команды, например сделать команды доступной или недоступной, скрыть/показать или установить или снять флажок.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b6911d865b253ff82ffcc6c4911e0989f109f28
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089827"
---
# <a name="change-the-appearance-of-a-command"></a>Изменение внешнего вида команды
Вы можете отправить отзыв пользователю, изменив внешний вид команды. Например, может потребоваться, чтобы команда выглядела иначе, если она недоступна. Можно сделать команды доступными или недоступными, скрыть или показать их, а также установить или снять флажки в меню.

Чтобы изменить внешний вид команды, выполните одно из следующих действий.

- Укажите соответствующие флаги в определении команды в файле таблицы команд.

- Используйте <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> службу.

- Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс и измените необработанные объекты команды.

  Следующие шаги показывают, как найти и обновить внешний вид команды с помощью платформы управляемых пакетов (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Изменение внешнего вида команды меню

1. Следуйте инструкциям в разделе [изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md) , чтобы создать пункт меню с именем `New Text` .

2. В файле *чанжеменутекст. CS* добавьте следующую инструкцию using:

    ```csharp
    using System.Security.Permissions;
    ```

3. В файле *чанжеменутекстпаккажегуидс. CS* добавьте следующую строку:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. В файле *чанжеменутекст. CS* замените код в методе метода ShowMessageBox следующим кодом:

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Получите команду, которую требуется обновить, из <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> объекта, а затем задайте соответствующие свойства для объекта Command. Например, следующий метод делает указанную команду из набора команд VSPackage доступной или недоступной. Следующий код делает пункт меню `New Text` недоступным после щелчка.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.package.GetService<IMenuCommandService, OleMenuCommandService>();
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);
        MenuCommand mc = mcs.FindCommand(newCmdID);
        if (mc != null)
        {
            mc.Enabled = enableCmd;
            cmdUpdated = true;
        }
        return cmdUpdated;
    }
    ```

6. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр Visual Studio.

7. В меню **Сервис** выберите команду **вызвать чанжеменутекст** . На этом этапе имя команды **вызывает чанжеменутекст**, поэтому обработчик команд не вызывает **чанжемикомманд ()**.

8. В меню **Сервис** должен появиться **новый текст**. Нажмите кнопку **создать текст**. Команда теперь должна быть неактивна.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
- [Командная таблица Visual Studio (. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
