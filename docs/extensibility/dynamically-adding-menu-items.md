---
title: Динамическое добавление пунктов меню | Документация Майкрософт
description: Узнайте, как использовать флаг команды ДинамиЦитемстарт для добавления пунктов меню во время выполнения. В этой статье показано, как задать запускаемый проект в решении Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa85d5b5cf4b99840e181fb24b5913ff72a3fee0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070340"
---
# <a name="dynamically-add-menu-items"></a>Динамическое добавление пунктов меню
Элементы меню можно добавлять во время выполнения, указывая `DynamicItemStart` флаг команды в определении кнопки заполнителя в файле Visual Studio Command-Table (*. vsct*), а затем определяя (в коде) количество пунктов меню для отображения и обработки команд. После загрузки VSPackage заполнитель заменяется на элементы динамического меню.

 Visual Studio использует динамические списки в списке **недавно** использовавшихся (MRU), в котором отображаются имена недавно открытых документов, а также список **окон** , в котором отображаются имена окон, открытых в настоящий момент.   `DynamicItemStart`Флаг для определения команды указывает, что команда является заполнителем до открытия VSPackage. При открытии VSPackage заполнитель заменяется на 0 или более команд, которые создаются во время выполнения и добавляются в динамический список. Возможно, вы не сможете увидеть позицию в меню, где динамический список отображается, пока не будет открыт пакет VSPackage.  Чтобы заполнить динамический список, Visual Studio запросит VSPackage найти команду с ИДЕНТИФИКАТОРом, первые символы которого совпадают с ИДЕНТИФИКАТОРом заполнителя. Когда Visual Studio находит соответствующую команду, она добавляет имя команды в динамический список. Затем он увеличивает идентификатор и ищет другую соответствующую команду для добавления в динамический список до тех пор, пока не будут выполняться динамические команды.

 В этом пошаговом руководстве показано, как задать запускаемый проект в решении Visual Studio с помощью команды на панели инструментов **Обозреватель решений** . В нем используется контроллер меню с динамическим раскрывающимся списком проектов в активном решении. Чтобы эта команда не отображалась, когда не открыто ни одно решение или если открытое решение содержит только один проект, пакет VSPackage загружается только в том случае, если решение содержит несколько проектов.

 Дополнительные сведения о *vsct* -файлах см. в разделе [файлы командной таблицы Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню

1. Создайте проект VSIX с именем `DynamicMenuItems` .

2. Когда откроется проект, добавьте пользовательский шаблон элемента команды и назовите его **обратном**. Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Настройка элементов в *vsct* файле
 Чтобы создать контроллер меню с элементами динамического меню на панели инструментов, необходимо указать следующие элементы:

- Две группы команд, одна из которых содержит контроллер меню и другую, содержащую пункты меню в раскрывающемся списке.

- Один элемент меню типа `MenuController`

- Две кнопки, одна из которых выступает в качестве заполнителя для пунктов меню, и другая, которая предоставляет значок и подсказку на панели инструментов.

1. В *динамикменупаккаже. vsct* определите идентификаторы команд. Перейдите в раздел символов и замените элементы IDSymbol в блоке **гуиддинамикменупаккажекмдсет** GuidSymbol. Необходимо определить элементы IDSymbol для двух групп: контроллера меню, команды заполнителя и команды привязки.

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. В разделе группы удалите существующие группы и добавьте две только что определенные группы:

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     Добавьте Менуконтроллер. Установите флаг команды Динамиквисибилити, так как он не всегда является видимым. ButtonText не отображается.

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. Добавьте две кнопки — один в качестве заполнителя для элементов динамического меню и один в качестве привязки для Менуконтроллер.

     Родителем кнопки PlaceHolder является **мименуконтроллерграуп**. Добавьте к кнопке заполнителя флаги команды ДинамиЦитемстарт, Динамиквисибилити и Текстчанжес. ButtonText не отображается.

     Кнопка привязки содержит значок и текст подсказки. Родителем кнопки привязки является также **мименуконтроллерграуп**. Добавьте флаг команды Ношовонменуконтроллер, чтобы убедиться, что кнопка не отображается в раскрывающемся списке Контроллер меню, и установите флаг команды Фиксменуконтроллер, чтобы сделать его постоянной привязкой.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. Добавьте значок в проект (в папке *Resources* ), а затем добавьте ссылку на него в *vsct* -файл. В этом пошаговом руководстве используется значок со стрелками, который входит в шаблон проекта.

5. Добавьте раздел Висибилитиконстраинтс за пределами раздела Commands прямо перед разделом Symbols. (Вы можете получить предупреждение, если оно будет добавлено после символов.) Этот раздел гарантирует, что контроллер меню отображается только при загрузке решения с несколькими проектами.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Реализация динамической команды меню
 Создается класс команды динамического меню, наследующий от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> . В этой реализации конструктор указывает предикат, который будет использоваться для сопоставления команд. Необходимо переопределить <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> метод, чтобы использовать этот предикат для задания <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> свойства, определяющего вызываемую команду.

1. Создайте новый файл класса C# с именем *динамиЦитемменукомманд. CS* и добавьте класс с именем **динамиЦитемменукомманд** , который наследует от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> :

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Добавьте следующие директивы using.

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Добавьте закрытое поле для хранения предиката соответствия:

    ```csharp
    private Predicate<int> matches;

    ```

4. Добавьте конструктор, который наследует от <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> конструктора и задает обработчик команд и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчик. Добавьте предикат для сопоставления с командой:

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. Переопределите <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> метод таким образом, чтобы он вызывал предикат Matches и задает <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> свойство:

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>Добавьте команду
 Конструктор обратном позволяет настраивать команды меню, включая динамические меню и пункты меню.

1. В *динамикменупаккаже. CS* добавьте идентификатор GUID набора команд и идентификатор команды:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. В файле *обратном. CS* добавьте следующие директивы using:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. В `DynamicMenu` классе добавьте закрытое поле **DTE2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Добавьте закрытое поле Рутитемид:

    ```csharp
    private int rootItemId = 0;
    ```

5. В конструкторе обратном добавьте команду меню. В следующем разделе мы определим обработчик команд, `BeforeQueryStatus` обработчик событий и предикат Match.

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>Реализация обработчиков
 Для реализации динамических пунктов меню в контроллере меню необходимо выполнить обработку команды при щелчке динамического элемента. Также необходимо реализовать логику, устанавливающую состояние пункта меню. Добавьте обработчики в `DynamicMenu` класс.

1. Чтобы реализовать команду **Set Startup Project** , добавьте обработчик событий **онинвокеддинамиЦитем** . Он ищет проект, имя которого совпадает с текстом вызываемой команды, и устанавливает его в качестве запускаемого проекта, устанавливая его абсолютный путь в <xref:EnvDTE.SolutionBuild.StartupProjects%2A> свойстве.

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. Добавьте `OnBeforeQueryStatusDynamicItem` обработчик событий. Это обработчик, вызываемый перед `QueryStatus` событием. Он определяет, является ли элемент меню реальным, то есть, не элементом-заполнителем, и является ли уже установленным элемент (то есть проект уже задан как запускаемый проект).

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>Реализация предиката соответствия ИДЕНТИФИКАТОРов команд

Теперь реализуйте предикат Match. Необходимо определить две вещи: сначала, является ли идентификатор команды допустимым (он больше или равен объявленному ИДЕНТИФИКАТОРу команды), и, во-вторых, указывает, указан ли возможный проект (меньше, чем число проектов в решении).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Настройка пакета VSPackage для загрузки только в том случае, если решение содержит несколько проектов
 Так как команда **задать запускаемый проект** не имеет смысла, если только активное решение не содержит более одного проекта, можно настроить пакет VSPackage для автоматической загрузки только в этом случае. Используется <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> вместе с контекстом пользовательского интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects> . В файле *динамикменупаккаже. CS* добавьте следующие атрибуты в класс динамикменупаккаже:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Проверка команды "задать запускаемый проект"
 Теперь можно протестировать код.

1. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр.

2. В экспериментальном экземпляре откройте решение, которое содержит более одного проекта.

     На панели инструментов **Обозреватель решений** должен отобразиться значок со стрелкой. Если развернуть его, должны отобразиться элементы меню, представляющие различные проекты в решении.

3. При проверке одного из проектов он превращается в запускаемый проект.

4. При закрытии решения или открытии решения, имеющего только один проект, значок панели инструментов должен исчезнуть.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
