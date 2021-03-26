---
title: Добавление поиска в окно инструментов | Документация Майкрософт
description: Узнайте, как добавлять функции поиска, включая поле поиска, фильтрацию и индикатор хода выполнения, в окно инструментов в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82176afaacae3b9f4553c8b1b5b41b9a4f10dace
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097556"
---
# <a name="add-search-to-a-tool-window"></a>Добавление поиска в окно инструментов
При создании или обновлении окна инструментов в расширении можно добавить те же функциональные возможности поиска, которые появляются в Visual Studio в других местах. Эта функция включает следующие функции:

- Поле поиска, которое всегда находится в пользовательской области панели инструментов.

- Индикатор хода выполнения, который перекрывается на самом поле поиска.

- Возможность показывать результаты сразу после ввода каждого символа (мгновенного поиска) или только после нажатия клавиши **Ввод** (Поиск по запросу).

- Список, в котором отображаются термины, для которых вы недавно искали.

- Возможность фильтровать поиск по конкретным полям или аспектам целевых объектов поиска.

Следуя этому пошаговому руководству, вы научитесь выполнять следующие задачи:

1. Создайте проект VSPackage.

2. Создание окна инструментов, содержащего элемент управления UserControl с текстовым полем, предназначенным только для чтения.

3. Добавьте поле поиска в окно инструментов.

4. Добавьте реализацию поиска.

5. Включение мгновенного поиска и отображение индикатора выполнения.

6. Добавьте параметр **учитывать регистр** .

7. Добавьте фильтр " **Поиск только с линиями** ".

## <a name="to-create-a-vsix-project"></a>Создание проекта VSIX

1. Создайте проект VSIX с именем `TestToolWindowSearch` и окном инструментов с именем **тестсеарч**. Если вам нужна помощь, см. раздел [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Создание окна инструментов

1. В `TestToolWindowSearch` проекте откройте файл *тестсеарчконтрол. XAML* .

2. Замените существующий `<StackPanel>` блок следующим блоком, который добавляет доступ только <xref:System.Windows.Controls.TextBox> для чтения к элементу <xref:System.Windows.Controls.UserControl> в окне инструментов.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. В файле *тестсеарчконтрол. XAML. CS* добавьте следующую директиву using:

    ```csharp
    using System.Text;
    ```

4. Удалите `button1_Click()` метод.

     В классе **тестсеарчконтрол** добавьте следующий код.

     Этот код добавляет открытое <xref:System.Windows.Controls.TextBox> свойство с именем **сеарчресултстекстбокс** и общедоступное строковое свойство с именем **сеарчконтент**. В конструкторе Сеарчресултстекстбокс устанавливается в текстовое поле, а Сеарчконтент инициализируется набором строк, разделенных символами новой строки. Содержимое текстового поля также инициализируется набором строк.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.

6. В строке меню выберите **Просмотреть**  >  **другие**  >  **тестсеарч** Windows.

     Откроется окно инструментов, но элемент управления поиском еще не отображается.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Добавление поля поиска в окно инструментов

1. В файле *тестсеарч. CS* добавьте в класс следующий код `TestSearch` . Код переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> свойство таким образом, чтобы метод доступа Get возвращал `true` .

     Чтобы включить поиск, необходимо переопределить <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> свойство. <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>Класс реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> и предоставляет реализацию по умолчанию, которая не включает поиск.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

3. В экспериментальном экземпляре Visual Studio откройте **тестсеарч**.

     В верхней части окна инструментов отображается элемент управления Поиск с подложкой **поиска** и значком лупы. Однако поиск еще не работает, так как процесс поиска не был реализован.

## <a name="to-add-the-search-implementation"></a>Добавление реализации поиска
 При включении поиска в <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> , как в предыдущей процедуре, окно инструментов создает узел поиска. Этот узел настраивает и управляет процессами поиска, которые всегда происходят в фоновом потоке. Поскольку <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> класс управляет созданием узла поиска и настройкой поиска, необходимо только создать задачу поиска и предоставить метод поиска. Процесс поиска выполняется в фоновом потоке, а вызовы элемента управления окна инструментов происходят в потоке пользовательского интерфейса. Поэтому для управления вызовами, выполняемыми с элементом управления, необходимо использовать метод [среадхелпер. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) .

1. В файле *тестсеарч. CS* добавьте следующие `using` директивы:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. В `TestSearch` классе добавьте следующий код, который выполняет следующие действия:

    - Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> метод для создания задачи поиска.

    - Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> метод для восстановления состояния текстового поля. Этот метод вызывается, когда пользователь отменяет задачу поиска и когда пользователь устанавливает или отменяет установку параметров или фильтров. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>И, и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> вызываются в ПОТОКЕ пользовательского интерфейса. Поэтому нет необходимости обращаться к текстовому полю с помощью метода [среадхелпер. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) .

    - Создает класс с именем `TestSearchTask` , наследуемый от <xref:Microsoft.VisualStudio.Shell.VsSearchTask> , который предоставляет реализацию по умолчанию <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> .

         В `TestSearchTask` конструктор задает закрытое поле, которое ссылается на окно инструментов. Чтобы предоставить метод поиска, переопределите <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> методы и. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>Метод позволяет реализовать процесс поиска. Этот процесс включает выполнение поиска, отображение результатов поиска в текстовом поле и вызов реализации базового класса этого метода для сообщения о завершении поиска.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. Протестируйте реализацию поиска, выполнив следующие действия.

    1. Перестройте проект и начните отладку.

    2. В экспериментальном экземпляре Visual Studio снова откройте окно инструментов, введите текст поиска в окне поиска и нажмите клавишу **Ввод**.

         Должны отобразиться правильные результаты.

## <a name="to-customize-the-search-behavior"></a>Настройка поведения поиска
 Изменяя параметры поиска, можно вносить разнообразные изменения в то, как отображается элемент управления поиском и как выполняется поиск. Например, можно изменить водяной знак (текст по умолчанию, отображаемый в поле поиска), минимальную и максимальную ширину элемента управления поиском, а также указать, следует ли отображать индикатор выполнения. Кроме того, можно изменить точку, с которой начинается поиск результатов поиска (по запросу или мгновенного поиска), а также указать, следует ли отображать список терминов, для которых вы недавно искали. Полный список параметров можно найти в <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> классе.

1. В файле * Тестсеарч. cs * добавьте в класс следующий код `TestSearch` . Этот код включает мгновенный поиск вместо поиска по запросу (это означает, что пользователю не нужно нажать клавишу **Ввод**). Код переопределяет `ProvideSearchSettings` метод в `TestSearch` классе, который необходим для изменения параметров по умолчанию.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Протестируйте новый параметр, перестроив решение и перезапуская отладчик.

     Результаты поиска отображаются каждый раз при вводе символа в поле поиска.

3. В `ProvideSearchSettings` методе добавьте следующую строку, которая включает отображение индикатора выполнения.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     Чтобы индикатор выполнения отображался, необходимо сообщить о ходе выполнения. Чтобы сообщить о ходе выполнения, раскомментируйте следующий код в `OnStartSearch` методе `TestSearchTask` класса:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Для снижения скорости обработки достаточного времени отображения индикатора выполнения раскомментируйте следующую строку в `OnStartSearch` методе `TestSearchTask` класса:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Протестируйте новые параметры, перестроив решение и начав отладку.

     Индикатор выполнения отображается в окне поиска (в виде синей линии под текстовым полем поиска) при каждом выполнении поиска.

## <a name="to-enable-users-to-refine-their-searches"></a>Предоставление пользователям возможности уточнения поиска
 Можно разрешить пользователям уточнять поиск с помощью таких параметров, как **соответствие регистру** или **слово целиком**. Параметры могут быть логическими, которые отображаются в виде кнопок в виде флажков или команд. В этом пошаговом руководстве вы создадите логический параметр.

1. В файле *тестсеарч. CS* добавьте в класс следующий код `TestSearch` . Код переопределяет `SearchOptionsEnum` метод, который позволяет реализации поиска определить, включен ли данный параметр. Код в `SearchOptionsEnum` добавляет параметр для сопоставления регистра с <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> перечислителем. Параметр для сопоставления регистра также становится доступным в качестве `MatchCaseOption` Свойства.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. В `TestSearchTask` классе раскомментируйте следующую строку в `OnStartSearch` методе:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Проверьте параметр:

    1. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

    2. В окне инструментов выберите стрелку вниз в правой части текстового поля.

         Появится флажок **учитывать регистр** .

    3. Установите флажок **учитывать регистр** , а затем выполните некоторые операции поиска.

## <a name="to-add-a-search-filter"></a>Добавление фильтра поиска
 Можно добавить фильтры поиска, позволяющие пользователям уточнить набор целевых объектов поиска. Например, можно фильтровать файлы в проводнике по датам, в которых они были изменены последними, и расширениями имен файлов. В этом пошаговом руководстве вы добавите фильтр только для четных строк. Когда пользователь выбирает этот фильтр, узел поиска добавляет строки, указанные в поисковом запросе. Затем можно найти эти строки в методе поиска и соответствующим образом фильтровать целевые объекты поиска.

1. В файле *тестсеарч. CS* добавьте в класс следующий код `TestSearch` . Код реализуется `SearchFiltersEnum` путем добавления <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> , который задает фильтрацию результатов поиска таким образом, чтобы отображались только четные линии.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Теперь элемент управления поиском отображает фильтр поиска `Search even lines only` . Когда пользователь выбирает фильтр, строка `lines:"even"` появляется в поле поиска. Другие условия поиска могут отображаться одновременно с фильтром. Строки поиска могут располагаться перед фильтром, после фильтра или обоими.

2. В файле *тестсеарч. CS* добавьте следующие методы в `TestSearchTask` класс, который находится в `TestSearch` классе. Эти методы поддерживают `OnStartSearch` метод, который вы измените на следующем шаге.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. В `TestSearchTask` классе Обновите метод, `OnStartSearch` используя следующий код. Это изменение обновляет код для поддержки фильтра.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. Протестируйте код.

5. Выполните сборку решения и запустите отладку. В экспериментальном экземпляре Visual Studio откройте окно инструментов, а затем щелкните стрелку вниз на элементе управления Поиск.

     Флажок **учитывать регистр** и отображать только фильтр **Искать даже строки** .

6. Выберите фильтр.

     Поле поиска содержит **строки «четные»**, и отображаются следующие результаты.

     2 хороший

     4 хороший

     6

7. Удалить `lines:"even"` из поля поиска установите флажок **учитывать регистр** , а затем введите `g` в поле поиска.

     Отобразятся следующие результаты:

     1 Go

     2 хороший

     5 не в наличии

8. Выберите X в правой части поля поиска.

     Поиск будет сброшен, и отобразится исходное содержимое. Однако флажок **учитывать регистр** по-прежнему будет установлен.
