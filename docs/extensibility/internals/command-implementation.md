---
title: Реализация команды | Документация Майкрософт
description: Сведения о реализации команд в Visual Studio, настройке группы команд в VSPackage, добавлении команды к ней, регистрации команды и ее реализации.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 93c99b131340d2e53b931619d4e5742d9e19f570
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091143"
---
# <a name="command-implementation"></a>Реализация команды
Для реализации команды в VSPackage необходимо выполнить следующие задачи.

1. В *vsct* -файле Настройте группу команд и добавьте в нее команду. Дополнительные сведения см. в разделе [файлы командных таблиц Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

2. Зарегистрируйте команду в Visual Studio.

3. Реализуйте команду.

В следующих разделах объясняется, как регистрировать и реализовывать команды.

## <a name="register-commands-with-visual-studio"></a>Регистрация команд в Visual Studio
 Если команда отображается в меню, необходимо добавить в <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage и использовать в качестве значения имя меню или его идентификатор ресурса.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Кроме того, необходимо зарегистрировать команду с помощью <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . Эту службу можно получить с помощью метода, <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Если пакет VSPackage является производным от <xref:Microsoft.VisualStudio.Shell.Package> .

```
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
if ( null != mcs )
{
    // Create the command for the menu item.
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );
    mcs.AddCommand( menuItem );
}

```

## <a name="implement-commands"></a>Реализация команд
 Существует несколько способов реализации команд. Если вам нужна статическая команда меню, которая является командой, которая всегда выглядит одинаковым образом и в том же меню, создайте команду, используя, <xref:System.ComponentModel.Design.MenuCommand> как показано в примерах из предыдущего раздела. Чтобы создать статическую команду, необходимо предоставить обработчик событий, отвечающий за выполнение команды. Так как команда всегда включена и видима, нет необходимости предоставлять свое состояние Visual Studio. Если вы хотите изменить состояние команды в зависимости от определенных условий, можно создать команду как экземпляр <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> класса, а в конструкторе предоставить обработчик событий для выполнения команды и `QueryStatus` обработчика уведомлений Visual Studio при изменении состояния команды. Также можно реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> как часть класса команд или, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Если вы предоставляете команду в составе проекта. У двух интерфейсов и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> класса есть методы, которые уведомляют Visual Studio об изменении состояния команды, а также другие методы, которые обеспечивают выполнение команды.

 При добавлении команды в службу команд она становится одной из цепочки команд. При реализации уведомлений о состоянии и методов выполнения для команды следует принять во внимание только для этой конкретной команды и передавать все остальные варианты в другие команды в цепочке. Если не передать команду в (обычно путем возврата <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> ), Visual Studio может работать неправильно.

## <a name="querystatus-methods"></a>Методы QueryStatus
 При реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> метода проверьте идентификатор GUID набора команд, к которому принадлежит команда, и идентификатор команды. Соблюдайте следующие правила.

- Если идентификатор GUID не распознан, ваша реализация любого метода должна возвращать значение <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP> .

- Если ваша реализация любого из методов распознает GUID, но не реализовал команду, метод должен вернуть значение <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

- Если ваша реализация любого из методов распознает и идентификатор GUID, и команду, то метод должен задать поле Command-flags каждой команды (в `prgCmds` параметре), используя следующие <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Флаги:

  - `OLECMDF_SUPPORTED`: Команда поддерживается.

  - `OLECMDF_INVISIBLE`: Команда не должна быть видимой.

  - `OLECMDF_LATCHED`: Команда включена и по-видимому установлен.

  - `OLECMDF_ENABLED`: Команда включена.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Команда должна быть скрыта, если она отображается в контекстном меню.

  - `OLECMDF_NINCHED`: Команда является контроллером меню и не включена, но список раскрывающихся меню не пуст и по-прежнему доступен. (Этот флаг редко используется.)

- Если команда была определена в файле *. vsct* с `TextChanges` флагом, задайте следующие параметры:

  - Присвойте `rgwz` элементу `pCmdText` параметра новый текст команды.

  - Задайте `cwActual` `pCmdText` для элемента параметра размер строки команды.

Кроме того, убедитесь, что текущий контекст не является функцией автоматизации, если только команда не предназначена специально для работы с функциями автоматизации.

Чтобы указать, что вы поддерживаете определенную команду, возвратите <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Для всех остальных команд возвращается <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

В следующем примере `QueryStatus` метод сначала проверяет, что контекст не является функцией автоматизации, а затем находит правильный идентификатор GUID набора команд и идентификатор команды. Сама команда настроена как включенная и поддерживаемая. Другие команды не поддерживаются.

```csharp
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)
        {
            // make the Right command visible
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;
                return VSConstants.S_OK;
            }
        }
        return Constants.OLECMDERR_E_NOTSUPPORTED;
    }
}
```

## <a name="execution-methods"></a>Методы выполнения
 Реализация `Exec` метода напоминает реализацию `QueryStatus` метода. Во-первых, убедитесь, что контекст не является функцией автоматизации. Затем проверьте идентификатор GUID и идентификатор команды. Если идентификатор GUID или идентификатора команды не распознан, возвращается значение <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

 Чтобы обработать команду, выполните ее и вернитесь <xref:Microsoft.VisualStudio.VSConstants.S_OK> в случае успешности выполнения. Ваша команда отвечает за обнаружение и уведомление об ошибках; Поэтому при сбое выполнения верните код ошибки. В следующем примере показано, как должен быть реализован метод выполнения.

```csharp
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)
        {
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                //execute the command
                return VSConstants.S_OK;
            }
        }
    }
    return Constants.OLECMDERR_E_NOTSUPPORTED;
}
```

## <a name="see-also"></a>См. также

- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
