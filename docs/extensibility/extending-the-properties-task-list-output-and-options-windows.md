---
title: Расширение свойств, список задач, выходных данных, окон параметров
description: Узнайте, как интегрировать сведения о вашем окне инструментов в Visual Studio на новую страницу параметров и новый параметр на странице свойств.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 970ab167434da4ba9c28eb6bbf9a8ea5f6cc6af0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070145"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Расширение свойств, список задач, вывода и параметров
Вы можете получить доступ к любому окну инструментов в Visual Studio. В этом пошаговом руководстве показано, как интегрировать сведения о вашем окне инструментов в новую страницу **параметров** и новый параметр на странице **свойств** , а также как выполнять запись в окна **список задач** и **вывода** .

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Создание расширения с помощью окна инструментов

1. Создайте проект с именем **TodoList** с помощью шаблона VSIX и добавьте пользовательский шаблон элемента окна инструментов с именем **тодовиндов**.

    > [!NOTE]
    > Дополнительные сведения о создании расширения с помощью окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Настройка окна инструментов
 Добавьте текстовое поле, в которое следует ввести новый элемент ToDo, кнопку для добавления нового элемента в список и список для вывода элементов списка.

1. В *тодовиндов. XAML* удалите элементы управления "Кнопка", "текстовое поле" и "StackPanel" из UserControl.

    > [!NOTE]
    > Это не приводит к удалению обработчика событий **Button1_Click** , который вы будете использовать повторно на следующем шаге.

2. Из раздела **все элементы управления WPF** области **элементов** перетащите элемент управления **Canvas** в сетку.

3. Перетащите на холст **текстовое поле**, **кнопку** и элемент управления **ListBox** . Разместите элементы таким образом, чтобы текстовое поле и кнопка находящиеся на одном уровне, а элемент управления ListBox заполняет оставшуюся часть окна под ними, как показано на рисунке ниже.

     ![Окно завершенных инструментов.](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. В области XAML найдите кнопку и задайте для нее свойство содержимого, которое нужно **Добавить**. Повторно подключите обработчик событий кнопки к элементу управления "Кнопка", добавив `Click="button1_Click"` атрибут. Блок Canvas должен выглядеть следующим образом:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Настройка конструктора

1. В файле *тодовиндовконтрол. XAML. CS* добавьте следующую директиву using:

    ```csharp
    using System;
    ```

2. Добавьте открытую ссылку на Тодовиндов и задавайте конструктор Тодовиндовконтрол в качестве параметра Тодовиндов. Код должен выглядеть следующим образом:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. В *тодовиндов. CS* измените конструктор тодовиндовконтрол, включив в него параметр тодовиндов. Код должен выглядеть следующим образом:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Создание страницы параметров
 Можно указать страницу в диалоговом окне **Параметры** , чтобы пользователи могли изменять параметры окна инструментов. Для создания страницы параметров необходимо как класс, описывающий параметры, так и запись в файле *тодолистпаккаже. CS* или *тодолистпаккаже. vb* .

1. Добавьте класс с именем `ToolsOptions.cs`. Сделайте `ToolsOptions` класс производным от <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Добавьте следующую директиву using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. На странице Параметры в этом пошаговом руководстве представлен только один параметр с именем Дайсахеад. Добавьте в класс закрытое поле с именем **дайсахеад** и свойством с именем **дайсахеад** `ToolsOptions` .

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Теперь необходимо сделать проект осведомленным об этой странице параметров.

### <a name="make-the-options-page-available-to-users"></a>Сделать страницу параметров доступной для пользователей

1. В *тодовиндовпаккаже. CS* добавьте в <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> `TodoWindowPackage` класс:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Первым параметром для конструктора Провидеоптионпаже является тип класса `ToolsOptions` , который был создан ранее. Вторым параметром «ToDo» является имя категории в диалоговом окне « **Параметры** ». Третьим параметром «General» является имя подкатегории в диалоговом окне « **Параметры** », где будет доступна страница «параметры». Следующие два параметра являются идентификаторами ресурсов для строк. Первая — это имя категории, а вторая — Имя подкатегории. Последний параметр определяет, можно ли получить доступ к этой странице с помощью службы автоматизации.

     Когда пользователь открывает страницу параметров, он должен выглядеть примерно так, как показано на следующем рисунке.

     ![Страницы параметров](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Обратите внимание, что категория **TODO** и Подкатегория **Общие**.

## <a name="make-data-available-to-the-properties-window"></a>Предоставление доступа к данным окно свойств
 Сведения о списке задач можно сделать доступными, создав класс с именем `TodoItem` , который хранит сведения об отдельных элементах в списке ToDo.

1. Добавьте класс с именем `TodoItem.cs`.

     Если окно инструментов доступно для пользователей, элементы в списке будут представлены TodoItems. Когда пользователь выбирает один из этих элементов в списке ListBox, в окне **свойств** отображаются сведения об этом элементе.

     Чтобы сделать данные доступными в окне **Свойства** , необходимо преобразовать данные в общие свойства, имеющие два специальных атрибута `Description` и `Category` . `Description` — текст, отображаемый в нижней части окна **Свойства** . `Category` Определяет, где должно отображаться свойство при отображении окна **Свойства** в представлении по **категориям** . На следующем рисунке окно **Свойства** находится в представлении по **категориям** , выбрано свойство **имя** в категории **поля TODO** , а описание свойства **имя** отображается в нижней части окна.

     ![Окно "Свойства"](../extensibility/media/t5properties.png "T5Properties")

2. Добавьте следующую директиву using в файл *TodoItem. CS* .

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Добавьте `public` Модификатор доступа в объявление класса.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Добавьте два свойства, `Name` и `DueDate` . Мы выполним `UpdateList()` и `CheckForErrors()` позже.

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. Добавьте закрытую ссылку на пользовательский элемент управления. Добавьте конструктор, который принимает пользовательский элемент управления и имя для этого элемента ToDo. Чтобы найти значение для `daysAhead` , оно получает свойство страницы Options.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. Поскольку экземпляры `TodoItem` класса будут храниться в ListBox и ListBox будет вызывать `ToString` функцию, необходимо перегрузить `ToString` функцию. Добавьте следующий код в *TodoItem. CS* после конструктора и до конца класса.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. В *тодовиндовконтрол. XAML. CS* добавьте методы-заглушки в `TodoWindowControl` класс для `CheckForError` методов и `UpdateList` . Вставьте их после ProcessDialogChar и до конца файла.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     `CheckForError`Метод вызовет метод, имеющий то же имя в родительском объекте, и этот метод проверяет, произошли ли ошибки и правильно обрабатывает их. `UpdateList`Метод обновит ListBox в родительском элементе управления; метод вызывается при `Name` `DueDate` изменении свойств и в этом классе. Они будут реализованы позже.

## <a name="integrate-into-the-properties-window"></a>Интеграция с окно свойств
 Теперь напишите код, управляющий ListBox, который будет привязан к окну **свойств** .

 Необходимо изменить обработчик нажатия кнопки, чтобы прочитать текстовое поле, создать TodoItem и добавить его в список ListBox.

1. Замените существующую `button1_Click` функцию кодом, который создает новый TodoItem и добавляет его в список ListBox. Он вызывает `TrackSelection()` , который будет определен позже.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. В представление конструирования выберите элемент управления ListBox. В окне **Свойства** нажмите кнопку **обработчики событий** и найдите событие **SelectionChanged** . Заполните текстовое поле **listBox_SelectionChanged**. Это приведет к добавлению заглушки для обработчика SelectionChanged и присвоению его событию.

3. Выполните метод `TrackSelection()`. Поскольку вам потребуется получить <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> службы, вам потребуется сделать их <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> доступными для тодовиндовконтрол. Добавьте в класс `TodoWindow` следующий метод:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Добавьте следующие директивы using в *тодовиндовконтрол. XAML. CS*:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Заполните обработчик SelectionChanged следующим образом:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Теперь заполните функцию Траккселектион, которая обеспечит интеграцию с окном **свойств** . Эта функция вызывается, когда пользователь добавляет элемент в ListBox или щелкает элемент в ListBox. Он добавляет содержимое ListBox в Селектионконтаинер и передает Селектионконтаинер в обработчик событий окна **свойств** <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> . Служба Траккселектион отслеживает выбранные объекты в пользовательском интерфейсе и отображает их свойства.

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     Теперь, когда у вас есть класс, который может использовать окно « **Свойства** », можно интегрировать окно « **свойства** » с окном инструментов. Когда пользователь щелкает элемент в списке в окне инструментов, окно **свойств** должно быть соответствующим образом обновлено. Аналогично, когда пользователь изменяет элемент ToDo в окне **Свойства** , связанный элемент должен быть обновлен.

7. Теперь добавьте оставшуюся часть кода функции Упдателист в *тодовиндовконтрол. XAML. CS*. Он должен удалить и повторно добавить измененный TodoItem из списка.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Протестируйте код. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр.

9. Откройте страницу   >  **Параметры** инструментов. На левой панели отобразится категория ToDo. Категории перечислены в алфавитном порядке, поэтому их следует искать в службах терминалов.

10. На странице Параметры **TODO** вы увидите, что `DaysAhead` свойство имеет значение **0**. Измените его на **2**.

11. В меню **вид/другие окна** откройте **тодовиндов**. В текстовом поле введите **EndDate** и нажмите кнопку **Добавить**.

12. В списке вы увидите дату в два дня позже, чем сегодня.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Добавление текста в окно вывода и элементы в список задач
 Для **список задач** создайте новый объект типа Task, а затем добавьте этот объект task в **список задач** , вызвав его `Add` метод. Для записи в окно **вывода** вызывается его `GetPane` метод для получения объекта панели, а затем вызывается `OutputString` метод объекта панели.

1. В *тодовиндовконтрол. XAML. CS* в `button1_Click` методе добавьте код для получения **общей** панели окна **вывода** (по умолчанию) и записи в него. Метод будет выглядеть так:

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Чтобы добавить элементы в список задач, необходимо добавить вложенный класс в класс Тодовиндовконтрол. Вложенный класс должен быть производным от <xref:Microsoft.VisualStudio.Shell.TaskProvider> . Добавьте следующий код в конец `TodoWindowControl` класса.

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. Затем добавьте в класс закрытую ссылку `TodoTaskProvider` и `CreateProvider()` метод `TodoWindowControl` . Код должен выглядеть следующим образом:

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. Добавьте `ClearError()` , который очищает список задач и `ReportError()` , который добавляет запись в список задач в `TodoWindowControl` класс.

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. Теперь реализуйте `CheckForErrors` метод следующим образом.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>Попробуйте сейчас

1. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

2. Откройте **тодовиндов** (**Просмотрите**  >  **другие окна**  >  **тодовиндов**).

3. Введите что-нибудь в текстовое поле и нажмите кнопку **Добавить**.

     Срок выполнения 2 дня после текущей даты добавляется в список. Ошибки не генерируются, и **список задач** (**View**  >  **список задач**) не должна иметь записей.

4. Теперь измените параметр на странице "Параметры" в **меню "Сервис**"  >    >   с **2** на **0**.

5. Введите что-нибудь еще в **тодовиндов** и нажмите кнопку **Добавить** еще раз. Это вызывает ошибку, а также запись в **список задач**.

     При добавлении элементов в качестве начальной даты устанавливается теперь плюс 2 дня.

6. В меню **вид** выберите пункт **вывод** , чтобы открыть окно **вывод** .

     Обратите внимание, что каждый раз, когда вы добавляете элемент, на панели **список задач** отображается сообщение.

7. Щелкните один из элементов в списке.

     В окне **Свойства** отображаются два свойства элемента.

8. Измените одно из свойств и нажмите клавишу **Ввод**.

     Элемент обновляется в ListBox.
