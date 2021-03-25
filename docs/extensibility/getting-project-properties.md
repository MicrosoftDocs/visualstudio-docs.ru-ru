---
title: Получение свойств проекта | Документация Майкрософт
description: Сведения о том, как отображать свойства проекта в окне инструментов. В этом примере показан элемент управления "дерево" в окне инструментов.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8de3f32951cb70b8115781ce067950c7e518b102
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057667"
---
# <a name="get-project-properties"></a>Получение свойств проекта

В этом пошаговом руководстве показано, как отобразить свойства проекта в окне инструментов.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Создание проекта VSIX и Добавление окна инструментов

1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать ресурсы расширения. Создайте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `ProjectPropertiesExtension` . Шаблон проекта VSIX можно найти в диалоговом окне " **Новый проект** ", выполнив поиск по слову "VSIX".

2. Добавьте окно инструментов, добавив пользовательский шаблон элемента окна инструментов с именем `ProjectPropertiesToolWindow` . В **Обозреватель решений** щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить**  >  **новый элемент**. В **диалоговом окне Добавление нового элемента** перейдите в раздел **Visual C# элементы**  >  **расширяемость** и выберите **настраиваемое окно инструментов**. В поле **имя** в нижней части диалогового окна измените имя файла на `ProjectPropertiesToolWindow.cs` . Дополнительные сведения о создании настраиваемого окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Выполните сборку решения и убедитесь в том, что оно компилируется без ошибок.

### <a name="to-display-project-properties-in-a-tool-window"></a>Отображение свойств проекта в окне инструментов

1. В файле Прожектпропертиестулвиндовкомманд. cs добавьте следующие директивы using.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. В *прожектпропертиестулвиндовконтрол. XAML* удалите существующую кнопку и добавьте TreeView из панели элементов. Можно также удалить обработчик событий щелчка из файла *прожектпропертиестулвиндовконтрол. XAML. CS* .

3. В *прожектпропертиестулвиндовкомманд. CS* используйте метод, `ShowToolWindow()` чтобы открыть проект и прочитать его свойства, а затем добавьте свойства в TreeView. Код для Шовтулвиндов должен выглядеть следующим образом:

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр.

5. Откройте проект в экспериментальном экземпляре.

6. В окне **Просмотр**  >  **других окон** щелкните **прожектпропертиестулвиндов**.

  Элемент управления "дерево" должен отображаться в окне инструментов вместе с именем первого проекта и всех его свойств.
