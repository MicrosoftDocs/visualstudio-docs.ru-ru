---
title: Расширение фильтра обозреватель решений | Документация Майкрософт
description: Узнайте, как расширить функциональные возможности фильтра обозреватель решений, чтобы показать или скрыть различные файлы в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d1256b807d67f95aa8ca1e952a4dca7bd550e0fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075020"
---
# <a name="extend-the-solution-explorer-filter"></a>Расширение фильтра обозреватель решений
Можно расширить функциональные возможности фильтра **Обозреватель решений** , чтобы показать или скрыть разные файлы. Например, можно создать фильтр, отображающий только файлы фабрики классов C# в **Обозреватель решений**, как показано в этом пошаговом руководстве.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Создание проекта пакета Visual Studio

1. Создайте проект VSIX с именем `FileFilter` . Добавьте пользовательский шаблон элемента команды с именем **FileFilter**. Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Добавьте ссылку на `System.ComponentModel.Composition` и `Microsoft.VisualStudio.Utilities` .

3. Сделайте команду меню на панели инструментов **Обозреватель решений** . Откройте файл *филефилтерпаккаже. vsct* .

4. Измените `<Button>` блок на следующий:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Обновление файла манифеста

1. В файле *source. extension. vsixmanifest* Добавьте ресурс, который является компонентом MEF.

2. На вкладке **активы** нажмите кнопку **создать** .

3. В поле **тип** выберите **Microsoft. VisualStudio. MefComponent**.

4. В поле **источник** выберите **проект в текущем решении**.

5. В поле **проект** выберите **FileFilter**, а затем нажмите кнопку **ОК** .

### <a name="add-the-filter-code"></a>Добавление кода фильтра

1. Добавьте в файл *филефилтерпаккажегуидс. CS* несколько идентификаторов GUID:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Добавьте файл класса в проект FileFilter с именем *филенамефилтер. CS*.

3. Замените пустое пространство имен и пустой класс приведенным ниже кодом.

     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)`Метод принимает коллекцию, содержащую корень решения ( `rootItems` ), и возвращает коллекцию элементов, включаемых в фильтр.

     `ShouldIncludeInFilter`Метод фильтрует элементы в иерархии **Обозреватель решений** на основе указанного условия.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. В *FileFilter. CS* удалите размещение команд и обработку кода из конструктора FileFilter. Результат должен выглядеть следующим образом:

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     Удалите `ShowMessageBox()` также метод.

5. В *филефилтерпаккаже. CS* замените код в `Initialize()` методе следующим кодом:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Тестирование кода

1. Постройте и запустите проект. Откроется второй экземпляр Visual Studio. Это называется экспериментальным экземпляром.

2. В экспериментальном экземпляре Visual Studio откройте проект C#.

3. Найдите кнопку, добавленную на панели инструментов **Обозреватель решений** . Это должна быть четвертая кнопка слева.

4. При нажатии кнопки все файлы должны быть отфильтрованы, и вы увидите, что **все элементы отфильтрованы из представления.** в **Обозреватель решений**.
