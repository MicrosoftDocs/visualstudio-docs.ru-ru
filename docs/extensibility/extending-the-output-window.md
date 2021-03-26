---
title: Расширение окно вывода | Документация Майкрософт
description: Узнайте, как расширить окно вывода в пакете SDK для Visual Studio, а также как создавать пользовательские панели и управлять ими.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf875d070d27d307380f23e71af2bda7c4a205b5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075046"
---
# <a name="extend-the-output-window"></a>Расширение окна вывода
Окно **вывода** представляет собой набор панелей текста, предназначенных для чтения и записи. В Visual Studio имеются следующие встроенные панели: **Сборка**, в которой проекты обмениваются сообщениями о сборках, и **Общие**, в которых [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] сообщения взаимодействуют с интегрированной средой разработки. Проекты автоматически получают ссылку на область **сборки** через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> методы интерфейса, а Visual Studio предоставляет прямой доступ к панели " **Общие** " через <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> службу. Помимо встроенных панелей можно создавать пользовательские панели и управлять ими.

 Окно **вывода** можно контролировать непосредственно через <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> интерфейсы и. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>Интерфейс, предлагаемый <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> службой, определяет методы для создания, извлечения и уничтожения областей окна **вывода** . <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>Интерфейс определяет методы для отображения панелей, скрытия панелей и манипулирования их текстом. Альтернативный способ управления окном **вывода** заключается в использовании <xref:EnvDTE.OutputWindow> объектов и <xref:EnvDTE.OutputWindowPane> в объектной модели автоматизации Visual Studio. Эти объекты инкапсулируют почти все функциональные возможности <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> интерфейсов и. Кроме того, <xref:EnvDTE.OutputWindow> объекты и <xref:EnvDTE.OutputWindowPane> добавляют некоторые функции более высокого уровня, чтобы упростить перечисление областей окна **вывода** и извлечение текста из панелей.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Создание расширения, использующего область вывода
 Вы можете создать расширение, которое будет выполнять различные аспекты области вывода.

1. Создайте проект VSIX с именем `TestOutput` с помощью команды меню с именем **TestOutput**. Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Добавьте следующие ссылки.

    1. EnvDTE

    2. EnvDTE80

3. В *TestOutput. CS* добавьте следующую инструкцию using:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. В *TestOutput. CS* удалите `ShowMessageBox` метод. Добавьте следующую заглушку метода:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. В конструкторе TestOutput измените обработчик команд на Аутпуткоммандхандлер. Ниже приведена часть, которая добавляет команды:

    ```csharp
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    if (commandService != null)
    {
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
        EventHandler eventHandler = OutputCommandHandler;
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

6. В разделах ниже приводятся различные методы, демонстрирующие различные способы работы с областью вывода. Эти методы можно вызывать в теле `OutputCommandHandler()` метода. Например, следующий код добавляет `CreatePane()` метод, указанный в следующем разделе.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Создание окна вывода с помощью Ивсаутпутвиндов
 В этом примере показано, как создать новую область окна **вывода** с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> интерфейса.

```csharp
void CreatePane(Guid paneGuid, string title,
    bool visible, bool clearWithSolution)
{
    IVsOutputWindow output =
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));
    IVsOutputWindowPane pane;

    // Create a new pane.
    output.CreatePane(
        ref paneGuid,
        title,
        Convert.ToInt32(visible),
        Convert.ToInt32(clearWithSolution));

    // Retrieve the new pane.
    output.GetPane(ref paneGuid, out pane);

     pane.OutputString("This is the Created Pane \n");
}
```

 Если добавить этот метод к расширению, указанному в предыдущем разделе, то при нажатии команды **Invoke TestOutput** вы увидите окно **вывода** с заголовком, в котором отображается надпись **Показать выходные данные из: креатедпане** и слова, **созданные** на панели.

## <a name="create-an-output-window-with-outputwindow"></a>Создание окна вывода с помощью Аутпутвиндов
 В этом примере показано, как создать область окна **вывода** с помощью <xref:EnvDTE.OutputWindow> объекта.

```csharp
void CreatePane(string title)
{
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;

    try
    {
        // If the pane exists already, write to it.
        panes.Item(title);
    }
    catch (ArgumentException)
    {
        // Create a new pane and write to it.
        panes.Add(title);
    }
}
```

 Хотя <xref:EnvDTE.OutputWindowPanes> коллекция позволяет извлекать область окна **вывода** по заголовку, заголовки областей не обязательно должны быть уникальными. Если вы сомневаетесь в уникальности заголовка, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> метод, чтобы получить нужную панель по его идентификатору GUID.

 Если добавить этот метод к расширению, указанному в предыдущем разделе, то при нажатии команды **Invoke TestOutput** вы увидите окно вывода с заголовком, в котором **отображается надпись Показать выходные данные из: дтепане** и слова, **добавленные** в область dte на панели.

## <a name="delete-an-output-window"></a>Удаление окна вывода
 В этом примере показано, как удалить область окна **вывода** .

```csharp
void DeletePane(Guid paneGuid)
{
    IVsOutputWindow output =
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));

    IVsOutputWindowPane pane;
    output.GetPane(ref paneGuid, out pane);

    if (pane == null)
    {
        CreatePane(paneGuid, "New Pane\n", true, true);
    }
     else
    {
        output.DeletePane(ref paneGuid);
    }
}
```

 Если добавить этот метод к расширению, указанному в предыдущем разделе, то при нажатии команды **Invoke TestOutput** вы увидите окно вывод с заголовком **отображать выходные данные из: Новая панель** и слова, **добавленные** в область создания в самой панели. При повторном нажатии команды **Invoke TestOutput** панель удаляется.

## <a name="get-the-general-pane-of-the-output-window"></a>Получение панели «Общие» окна «вывод»
 В этом примере показано, как получить встроенную **общую** панель окна **вывод** .

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Если добавить этот метод к расширению, указанному в предыдущем разделе, то при нажатии команды **Invoke TestOutput** вы увидите, что в окне **вывод** отображается слово **найденная общая область** на панели.

## <a name="get-the-build-pane-of-the-output-window"></a>Получение области "сборка" окна "вывод"
 В этом примере показано, как найти область **построения** и выполнить запись в нее. Так как панель **сборки** не активируется по умолчанию, она также активирует ее.

```csharp
void OutputTaskItemStringExExample(string buildMessage)
{
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));

    EnvDTE.OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;
    foreach (EnvDTE.OutputWindowPane pane in panes)
        {
            if (pane.Name.Contains("Build"))
            {
                pane.OutputString(buildMessage + "\n");
                pane.Activate();
                return;
             }
        }
}
```
