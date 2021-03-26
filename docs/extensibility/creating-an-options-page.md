---
title: Создание страницы параметров | Документация Майкрософт
description: Узнайте, как создать простую страницу «инструменты/параметры», которая использует сетку свойств для проверки и установки свойств.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb94554b4ac1af30d8187a8ab75aa83f65dccc72
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055808"
---
# <a name="create-an-options-page"></a>Создание страницы параметров

В этом пошаговом руководстве создается простая страница «Сервис/параметры», использующая сетку свойств для проверки и установки свойств.

 Чтобы сохранить эти свойства и восстановить их из файла параметров, выполните следующие действия, а затем см. раздел [Создание категории параметров](../extensibility/creating-a-settings-category.md).

 MPF предоставляет два класса, помогающие создавать страницы параметров инструментов, <xref:Microsoft.VisualStudio.Shell.Package> класс и <xref:Microsoft.VisualStudio.Shell.DialogPage> класс. Создайте пакет VSPackage, чтобы предоставить контейнер для этих страниц, подклассом `Package` класса. Все страницы параметров инструментов создаются путем наследования от `DialogPage` класса.

## <a name="prerequisites"></a>Предварительные требования

 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Создание страницы параметров инструментов в сетке

 В этом разделе вы создадите простую сетку свойств Сервис параметры. Эта сетка используется для вывода и изменения значения свойства.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Создание проекта VSIX и добавление VSPackage

1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать ресурсы расширения. Создайте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `MyToolsOptionsExtension` . Шаблон проекта VSIX можно найти в диалоговом окне " **Новый проект** ", выполнив поиск по слову "VSIX".

2. Добавьте пакет VSPackage, добавив шаблон элемента пакета Visual Studio с именем `MyToolsOptionsPackage` . В **Обозреватель решений** щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить**  >  **новый элемент**. В **диалоговом окне Добавление нового элемента** перейдите в раздел **Visual C# элементы**  >  **расширяемость** и выберите **пакет Visual Studio**. В поле **имя** в нижней части диалогового окна измените имя файла на `MyToolsOptionsPackage.cs` . Дополнительные сведения о создании пакета VSPackage см. в разделе [Создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Создание сетки свойств «Сервис параметры»

1. Откройте файл *митулсоптионспаккаже* в редакторе кода.

2. Добавьте следующую инструкцию using.

   ```csharp
   using System.ComponentModel;
   ```

3. Объявите `OptionPageGrid` класс и наследует его от <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Примените <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> к `VSPackage` классу, чтобы назначить классу категорию параметров и имя страницы параметров для оптионпажегрид. Результат должен выглядеть следующим образом:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Добавьте `OptionInteger` свойство в `OptionPageGrid` класс.

    - Примените <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> к категории свойства сетки свойств.

    - Примените, <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> чтобы присвоить свойству имя.

    - Примените, <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> чтобы назначить свойству описание.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> поддерживает свойства с подходящими преобразователями или структурами или массивами, которые можно разворачивать в свойствах с подходящими преобразователями. Список преобразователей см. в разделе <xref:System.ComponentModel> пространство имен.

6. Выполните сборку решения и запустите отладку.

7. В экспериментальном экземпляре Visual Studio в меню **Сервис** выберите пункт **Параметры**.

     В левой области вы должны увидеть **мою категорию**. (Категории параметров перечислены в алфавитном порядке, поэтому они должны отображаться примерно на середине списка.) Откройте **раздел "Моя Категория** " и щелкните **страницу "Моя сетка**". Сетка параметры появится в правой области. Категорией свойств является " **Мои параметры**", а имя свойства — **"мое целое число**". В нижней части панели отображается параметр описание свойства, **число моих целых чисел**. Измените значение из его начального значения 256 на другое. Нажмите кнопку **ОК**, а затем снова откройте **страницу "Сетка**". Вы видите, что новое значение сохраняется.

     Страница параметров также доступна в поле поиска Visual Studio. В поле поиска, расположенном в верхней части интегрированной среды разработки, введите **Моя Категория** , и вы увидите **страницу моя Категория-> моя страница сетки** в списке результатов.

## <a name="create-a-tools-options-custom-page"></a>Создание настраиваемой страницы параметров инструментов

 В этом разделе вы создадите страницу параметров средств с настраиваемым пользовательским ИНТЕРФЕЙСом. Эта страница используется для просмотра и изменения значения свойства.

1. Откройте файл *митулсоптионспаккаже* в редакторе кода.

2. Добавьте следующую инструкцию using.

    ```csharp
    using System.Windows.Forms;
    ```

3. Добавьте `OptionPageCustom` класс непосредственно перед `OptionPageGrid` классом. Создайте класс, производный от `DialogPage` .

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. Добавьте атрибут GUID. Добавьте свойство Оптионстринг:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. Примените секунду <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> к классу VSPackage. Этот атрибут присваивает классу категорию параметров и имя страницы параметров.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. Добавьте в проект новый **Пользовательский элемент управления** с именем MyUserControl.

7. Добавьте элемент управления **TextBox** в пользовательский элемент управления.

     В окне **Свойства** на панели инструментов нажмите кнопку **события** , а затем дважды щелкните событие **покинуть** . Новый обработчик событий появится в коде *MyUserControl. CS* .

8. Добавьте открытое `OptionsPage` поле, `Initialize` метод в класс Control и обновите обработчик событий, чтобы задать значение параметра для содержимого текстового поля:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     `optionsPage`Поле содержит ссылку на родительский `OptionPageCustom` экземпляр. `Initialize`Метод отображается `OptionString` в **текстовом поле**. Обработчик событий записывает текущее значение **текстового поля** в, `OptionString` когда фокус покидает **текстовое поле**.

9. В файле кода пакета добавьте переопределение для `OptionPageCustom.Window` свойства в `OptionPageCustom` класс для создания, инициализации и возврата экземпляра `MyUserControl` . Теперь класс должен выглядеть следующим образом:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. Постройте и запустите проект.

11. В экспериментальном экземпляре щелкните **Сервис**  >  **Параметры**.

12. Найти **мою категорию** , а затем **мою пользовательскую страницу**.

13. Измените значение **оптионстринг**. Нажмите кнопку **ОК**, а затем снова откройте **мою пользовательскую страницу**. Вы видите, что новое значение сохранено.

## <a name="access-options"></a>Параметры доступа

 В этом разделе вы получите значение параметра из пакета VSPackage, в котором размещена соответствующая страница параметров средств. Тот же метод можно использовать для получения значения любого открытого свойства.

1. В файле кода пакета добавьте открытое свойство с именем **оптионинтежер** в класс **митулсоптионспаккаже** .

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Этот код вызывает метод <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> для создания или получения `OptionPageGrid` экземпляра. `OptionPageGrid` вызывает метод <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> для загрузки параметров, которые являются открытыми свойствами.

2. Теперь добавьте пользовательский шаблон элемента команды с именем **митулсоптионскомманд** для вывода значения. В диалоговом окне **Добавление нового элемента** перейдите в раздел расширяемость **Visual C#**  >   и выберите пункт **пользовательская команда**. В поле **имя** в нижней части окна измените имя файла команд на *митулсоптионскомманд. CS*.

3. В файле *митулсоптионскомманд* замените текст `ShowMessageBox` метода команды следующим:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Выполните сборку решения и запустите отладку.

5. В экспериментальном экземпляре в меню **Сервис** выберите команду **вызвать митулсоптионскомманд**.

     В окне сообщения отображается текущее значение `OptionInteger` .

## <a name="see-also"></a>См. также

- [Страницы параметров и параметров](../extensibility/internals/options-and-options-pages.md)
