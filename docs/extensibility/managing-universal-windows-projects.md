---
title: Управление универсальными проектами Windows | Документация Майкрософт
description: Для поддержки универсальных приложений Windows расширения Visual Studio, управляющие проектами, должны быть осведомлены о структуре проекта универсального приложения Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8af418d8ffcaad18aca4497078f4e24f9bb679fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090646"
---
# <a name="manage-universal-windows-projects"></a>Управление универсальными проектами Windows

Универсальные приложения для Windows — это приложения, предназначенные для Windows 8.1 и Windows Phone 8,1, позволяя разработчикам использовать код и другие ресурсы на обеих платформах. Общий код и ресурсы хранятся в общем проекте, а зависящий от платформы код и ресурсы хранятся в отдельных проектах, один для Windows, а другой — для Windows Phone. Дополнительные сведения об универсальных приложениях Windows см. в разделе [универсальные приложения для Windows](/windows/uwp/get-started/create-uwp-apps). Расширения Visual Studio, управляющие проектами, должны учитывать, что проекты универсальных приложений Windows имеют структуру, отличающуюся от одноплатформенных приложений. В этом пошаговом руководстве показано, как перемещаться по общему проекту и управлять общими элементами.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Навигация по общему проекту

1. Создайте проект VSIX C# с именем **тестуниверсалпрожект**. (**Файл**  >  **Новые**  >  **Проект** , а затем  >    >  **пакет Visual Studio** для расширения C#). Добавьте шаблон **настраиваемого командного** элемента проекта (на **Обозреватель решений** щелкните правой кнопкой мыши узел проекта и выберите **добавить**  >  **новый элемент**, а затем перейдите в раздел **расширяемость**). Назовите файл **тестуниверсалпрожект**.

2. Добавьте ссылку на *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* и *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (в разделе **Extensions** ).

3. Откройте *тестуниверсалпрожект. CS* и добавьте следующие `using` директивы:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. В `TestUniversalProject` классе добавьте закрытое поле, указывающее на окно **вывод** .

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Установите ссылку на область вывода в конструкторе Тестуниверсалпрожект:

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }

        // get a reference to the Output window
        output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. Удалите существующий код из `ShowMessageBox` метода:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Получите объект DTE, который будет использоваться для нескольких различных целей в этом пошаговом руководстве. Кроме того, убедитесь, что решение загружено при нажатии кнопки меню.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Найдите общий проект. Общий проект является чистым контейнером; Он не создает и не создает выходные данные. Следующий метод находит первый общий проект в решении, выполняя поиск <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта, имеющего возможность совместного использования проекта.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. В `ShowMessageBox` методе выводится заголовок (имя проекта, которое отображается в **Обозреватель решений**) общего проекта.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Получите проект активной платформы. Проекты платформы — это проекты, содержащие код и ресурсы, зависящие от платформы. Следующий метод использует новое поле <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> для получения проекта активной платформы.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. В `ShowMessageBox` методе выводится заголовок активного проекта платформы.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                    MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Выполните итерацию по проектам платформы. Следующий метод получает все импортированные (платформы) проекты из общего проекта.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Если пользователь открыл проект универсального приложения Windows на C++ в экспериментальном экземпляре, приведенный выше код создает исключение. Это известная проблема. Чтобы избежать исключения, замените `foreach` блок выше на следующий:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. В `ShowMessageBox` методе выводится заголовок каждого проекта платформы. Вставьте следующий код после строки, в которой выводится заголовок активного проекта платформы. В этом списке отображаются только загруженные проекты платформы.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Изменение активного проекта платформы. Следующий метод задает активный проект с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. В `ShowMessageBox` методе измените активный проект платформы. Вставьте этот код в `foreach` блок.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Теперь попробуйте. Нажмите клавишу F5, чтобы запустить экспериментальный экземпляр. Создайте проект приложения универсального концентратора C# в экспериментальном экземпляре (в диалоговом окне **Новый проект** —   >    >    >  приложение **универсального**  >  **концентратора** Visual C# для Windows 8). После загрузки решения перейдите в меню **Сервис** и выберите команду **вызвать тестуниверсалпрожект**, а затем проверьте текст в области **вывода** . Вы должны увидеть нечто вроде этого:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Управление общими элементами в проекте платформы

1. Найдите общие элементы в проекте платформы. Элементы в общем проекте отображаются в проекте платформы как общие элементы. Они не отображаются в **Обозреватель решений**, но можно проанализировать иерархию проекта, чтобы найти их. Следующий метод просматривает иерархию и собирает все общие элементы. При необходимости выводится заголовок каждого элемента,. Общие элементы определяются новым свойством <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> .

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
        }
    }
    ```

2. В `ShowMessageBox` метод добавьте следующий код для пошагового анализа элементов иерархии проекта платформы. Вставьте его в `foreach` блок.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Чтение общих элементов. Общие элементы отображаются в проекте платформы как скрытые связанные файлы, а все свойства можно считать обычными связанными файлами. Следующий код считывает полный путь к первому общему элементу.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Теперь попробуйте. Нажмите клавишу **F5** , чтобы запустить экспериментальный экземпляр. Создайте проект приложения универсального концентратора c# в экспериментальном экземпляре (в диалоговом окне **Новый проект** , **Visual C#**  >  **Windows**  >  **8**  >  **универсальное**  >  **приложение-концентратор**) перейдите в меню **Сервис** и выберите команду **вызвать тестуниверсалпрожект**, а затем проверьте текст в области **вывода** . Вы должны увидеть нечто вроде этого:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Обнаружение изменений в проектах платформы и общих проектах

1. Вы можете использовать события иерархии и проекта для обнаружения изменений в общих проектах так же, как и для проектов платформы. Однако элементы проекта в общем проекте не отображаются, что означает, что определенные события не срабатывают при изменении общих элементов проекта.

    Рассмотрим последовательность событий при переименовании файла в проекте:

   1. Имя файла изменяется на диске.

   2. Файл проекта обновляется и включает новое имя файла.

      События иерархии (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> ) обычно отслеживание изменений, отображаемых в пользовательском интерфейсе, как в **Обозреватель решений**. События иерархии рассматривайте, что операция переименования файлов состоит из удаления файлов, а затем добавления файлов. Однако при изменении невидимых элементов система событий иерархии запускает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> событие, но не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> событие. Таким образом, при переименовании файла в проекте платформы можно получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> , но если переименовать файл в общем проекте, вы получите только <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> .

      Для наблюдения за изменениями в элементах проекта можно выполнять обработку событий элементов проекта DTE (найденных в <xref:EnvDTE.ProjectItemsEventsClass> ). Однако при обработке большого количества событий можно повысить производительность обработки событий в <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> . В этом пошаговом руководстве показаны только события иерархии и события DTE. В этой процедуре прослушиватель событий добавляется в общий проект и проект платформы. Затем при переименовании одного файла в общем проекте и другом файле в проекте платформы можно просмотреть события, которые запускаются для каждой операции переименования.

      В этой процедуре прослушиватель событий добавляется в общий проект и проект платформы. Затем при переименовании одного файла в общем проекте и другом файле в проекте платформы можно просмотреть события, которые запускаются для каждой операции переименования.

2. Добавьте прослушиватель событий. Добавьте в проект новый файл класса и вызовите его *хиерарчевентлистенер. CS*.

3. Откройте файл *хиерарчевентлистенер. CS* и добавьте следующие директивы using:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. `HierarchyEventListener`Реализуйте класс <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> следующим образом:

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Реализуйте члены <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> , как показано в приведенном ниже коде.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. В том же классе добавьте еще один обработчик событий для события DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> , который происходит при каждом переименовании элемента проекта.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Подпишитесь на события иерархии. Необходимо зарегистрироваться отдельно для каждого отслеживаемого проекта. Добавьте следующий код в `ShowMessageBox` , один для общего проекта, а другой для одного из проектов платформы.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. Подпишитесь на событие элемента проекта DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> . После подключения второго прослушивателя добавьте следующий код.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Измените общий элемент. Нельзя изменять общие элементы в проекте платформы; Вместо этого их необходимо изменить в общем проекте, который является действительным владельцем этих элементов. Идентификатор соответствующего элемента можно получить в общем проекте с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> , указав полный путь к общему элементу. Затем можно изменить общий элемент. Изменение распространяется на проекты платформы.

    > [!IMPORTANT]
    > Перед изменением элемента проекта следует определить, является ли он общим элементом.

     Следующий метод изменяет имя файла элемента проекта.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Вызовите этот метод после того, как весь другой код в программе `ShowMessageBox` изменит имя файла на элемент в общем проекте. Вставьте его после кода, который получает полный путь к элементу в общем проекте.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Постройте и запустите проект. Создайте приложение универсального концентратора C# в экспериментальном экземпляре, откройте меню **Сервис** и выберите команду **вызвать тестуниверсалпрожект** и проверьте текст в области вывода общие. Необходимо изменить имя первого элемента в общем проекте (предполагается, что он будет файлом *app. XAML* ), и вы увидите, что <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> событие запущено. В этом случае, так как при переименовании *app. XAML* будет также выполнено переименование *app. XAML. CS* , вы увидите четыре события (по два для каждого проекта платформы). (События DTE не отслеживания элементов в общем проекте.) Вы должны увидеть два <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> события (по одному для каждого проекта платформы), но не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> события.

12. Теперь попробуем переименовать файл в проекте платформы, и вы увидите разницу в возможностях событий. Добавьте следующий код в `ShowMessageBox` после вызова `ModifyFileName` .

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Постройте и запустите проект. Создайте универсальный проект на C# в экспериментальном экземпляре, откройте меню **Сервис** и выберите команду **вызвать тестуниверсалпрожект** и проверьте текст в области "общие выходные данные". После переименования файла в проекте платформы вы увидите <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> событие и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> событие. Поскольку изменение файла не привело к изменению других файлов, и, поскольку изменения элементов в проекте платформы не будут распространяться в любом месте, существует только одно из этих событий.