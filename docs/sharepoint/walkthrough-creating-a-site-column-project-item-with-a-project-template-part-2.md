---
title: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2
titleSuffix: ''
description: Добавьте Мастер в шаблон проекта столбца сайта, чтобы получать данные от пользователей, если они используют шаблон для создания проекта SharePoint, содержащего элемент проекта.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 13a2f2c147bbf175a7601cd465dc8acbba9b5388
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217753"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2
  После определения пользовательского типа элемента проекта SharePoint и связывания его с шаблоном проекта в Visual Studio может также потребоваться создать мастер для шаблона. Мастер можно использовать для получения сведений от пользователей, если они используют шаблон для создания нового проекта, содержащего элемент проекта. Собранные сведения можно использовать для инициализации элемента проекта.

 В этом пошаговом руководстве вы добавите мастер в шаблон проекта столбца сайта, который демонстрируется в [разделе Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Когда пользователь создает проект столбца сайта, мастер собирает сведения о столбце сайта (например, его базовый тип и группу) и добавляет эти сведения в файл *Elements.xml* в новом проекте.

 В этом пошаговом руководстве описаны следующие задачи.

- Создание мастера для пользовательского типа элемента проекта SharePoint, связанного с шаблоном проекта.

- Определение пользовательского пользовательского интерфейса мастера, который напоминает встроенные мастера для проектов SharePoint в Visual Studio.

- Создание двух *команд SharePoint* , которые используются для вызова локального сайта SharePoint во время работы мастера. Команды SharePoint — это методы, которые могут использоваться расширениями Visual Studio для вызова API-интерфейсов в объектной модели сервера SharePoint. Дополнительные сведения см. в разделе [вызов в объектных моделях SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Использование заменяемых параметров для инициализации файлов проектов SharePoint с данными, собранными в мастере.

- Создание нового SNK-файла в каждом новом экземпляре проекта столбца сайта. Этот файл используется для подписания выходных данных проекта, чтобы сборку решения SharePoint можно было развернуть в глобальном кэше сборок.

- Отладка и тестирование мастера.

> [!NOTE]
> Ряд примеров рабочих процессов см. в разделе [примеры рабочих процессов SharePoint](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо сначала создать решение Ситеколумнпрожектитем, выполнив [Пошаговое руководство: создание элемента проекта столбца сайта с шаблоном проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Кроме того, для выполнения этого пошагового руководства на компьютере разработчика потребуются следующие компоненты:

- Поддерживаемые выпуски Windows, SharePoint и Visual Studio.

- Пакет SDK для Visual Studio. В этом пошаговом руководстве используется шаблон **проекта VSIX** в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. [в разделе Расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Знания следующих концепций полезны, но не требуются для выполнения этого пошагового руководства.

- Мастера для шаблонов проектов и элементов в Visual Studio. Дополнительные сведения см. [в разделе руководство. Использование мастеров с шаблонами проектов](../extensibility/how-to-use-wizards-with-project-templates.md) и <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейсом.

- Столбцы сайта в SharePoint. Дополнительные сведения см. в разделе [столбцы](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

## <a name="understand-the-wizard-components"></a>Знакомство с компонентами мастера
 Мастер, продемонстрированный в этом пошаговом руководстве, содержит несколько компонентов. Эти компоненты описаны в следующей таблице.

|Компонент|Описание|
|---------------|-----------------|
|Реализация мастера|Это класс с именем `SiteColumnProjectWizard` , который реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс. Этот интерфейс определяет методы, которые Visual Studio вызывает при запуске и завершении работы мастера, а также в определенные моменты времени при запуске мастера.|
|Пользовательский интерфейс мастера|Это окно на основе WPF с именем `WizardWindow` . Это окно содержит два пользовательских элемента управления с именами `Page1` и `Page2` . Эти пользовательские элементы управления представляют две страницы мастера.<br /><br /> В этом пошаговом руководстве <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> метод реализации мастера отображает пользовательский интерфейс мастера.|
|Модель данных мастера|Это промежуточный класс с именем `SiteColumnWizardModel` , который предоставляет слой между интерфейсом пользователя мастера и реализацией мастера. В этом примере этот класс используется для создания абстрактной реализации мастера и пользовательского интерфейса мастера. Этот класс не является обязательным компонентом всех мастеров.<br /><br /> В этом пошаговом руководстве `SiteColumnWizardModel` при отображении пользовательского интерфейса мастера реализация мастера передает объект в окно мастера. Пользовательский интерфейс мастера использует методы этого объекта для сохранения значений элементов управления в пользовательском интерфейсе и выполнения таких задач, как проверка допустимости URL-адреса входного сайта. После завершения работы мастера мастер использует `SiteColumnWizardModel` объект для определения конечного состояния пользовательского интерфейса.|
|Диспетчер подписывания проекта|Это вспомогательный класс с именем `ProjectSigningManager` , который используется реализацией мастера для создания файла key. snk в каждом новом экземпляре проекта.|
|команды SharePoint|Это методы, которые используются моделью данных мастера для вызова локального сайта SharePoint во время работы мастера. Так как команды SharePoint должны быть нацелены на платформа .NET Framework 3,5, эти команды реализуются в разных сборках, чем в остальной части кода мастера.|

## <a name="create-the-projects"></a>Создание проектов
 Для выполнения этого пошагового руководства необходимо добавить несколько проектов в решение Ситеколумнпрожектитем, созданное в [разделе Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Проект WPF. Будет реализован <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс и определен пользовательский интерфейс мастера в этом проекте.

- Проект библиотеки классов, определяющий команды SharePoint. Этот проект должен ориентироваться на the.NET Framework 3,5.

  Начните пошаговое руководство, создав проекты.

#### <a name="to-create-the-wpf-project"></a>Создание проекта WPF

1. В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] откройте решение ситеколумнпрожектитем.

2. В **Обозреватель решений** откройте контекстное меню узла решения **Ситеколумнпрожектитем** , выберите **Добавить**, а затем выберите **Новый проект**.

3. В верхней части диалогового окна **Добавление нового проекта** убедитесь, что **платформа .NET Framework 4,5** выбран в списке версий платформа .NET Framework.

4. Разверните узел **Visual C#** или узел **Visual Basic** и выберите узел **Windows** .

5. В списке шаблонов проектов выберите **Библиотека пользовательских элементов управления WPF**, присвойте проекту имя **прожекттемплатевизард**, а затем нажмите кнопку **ОК** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет проект **прожекттемплатевизард** в решение и открывает файл UserControl1. XAML по умолчанию.

6. Удалите файл UserControl1. XAML из проекта.

#### <a name="to-create-the-sharepoint-commands-project"></a>Создание проекта команд SharePoint

1. В **Обозреватель решений** откройте контекстное меню узла решения ситеколумнпрожектитем, выберите **Добавить**, а затем выберите **Новый проект**.

2. В верхней части диалогового окна **Добавление нового проекта** выберите **платформа .NET Framework 3,5** в списке версий платформа .NET Framework.

3. Разверните узел **Visual C#** или узел  **Visual Basic** , а затем выберите узел **Windows** .

4. Выберите шаблон проекта **Библиотека классов** , назовите проект **шарепоинткоммандс**, а затем нажмите кнопку **ОК** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет проект **шарепоинткоммандс** в решение и открывает файл кода Class1 по умолчанию.

5. Удалите файл кода Class1 из проекта.

## <a name="configure-the-projects"></a>Настройка проектов
 Перед созданием мастера необходимо добавить в проекты некоторые файлы кода и ссылки на сборки.

#### <a name="to-configure-the-wizard-project"></a>Настройка проекта мастера

1. В **Обозреватель решений** откройте контекстное меню для узла проекта **прожекттемплатевизард** и выберите пункт **Свойства**.

2. В **конструкторе проектов** перейдите на вкладку **приложение** для проекта Visual C# или вкладку **Компиляция** для Visual Basic проекта.

3. Убедитесь, что для целевой платформы задано значение платформа .NET Framework 4,5, а не клиентский профиль платформа .NET Framework 4,5.

     Дополнительные сведения см. в разделе [инструкции. Назначение версии платформа .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

4. Откройте контекстное меню проекта **прожекттемплатевизард** , выберите **Добавить**, а затем выберите **новый элемент**.

5. Выберите элемент **Window (WPF)** , присвойте элементу имя **визардвиндов**, а затем нажмите кнопку **добавить** .

6. Добавьте в проект два **элемента управления пользователя (WPF)** и присвойте им имя «а» **и «** **Page2**».

7. Добавьте в проект четыре файла кода и присвойте им следующие имена:

    - ситеколумнпрожектвизард

    - ситеколумнвизардмодел

    - прожектсигнингманажер

    - коммандидс

8. Откройте контекстное меню для узла проекта **прожекттемплатевизард** и выберите команду **Добавить ссылку**.

9. Разверните узел **сборки** , выберите узел **расширения** , а затем установите флажки рядом со следующими сборками:

    - EnvDTE

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. Shell. Interop. 10.0

    - Microsoft. VisualStudio. Shell. Interop. 11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

10. Нажмите кнопку **ОК** , чтобы добавить сборки в проект.

11. В **Обозреватель решений** в папке **References** для проекта **прожекттемплатевизард** выберите **EnvDTE**.

12. В окне **Свойства** измените значение свойства **Внедрить типы взаимодействия** на **false**.

13. При разработке проекта Visual Basic импортируйте пространство имен Прожекттемплатевизард в проект с помощью **конструктора проектов**.

     Дополнительные сведения см. [в разделе инструкции. Добавление или удаление импортированных пространств имен &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>Настройка проекта Шарепоинткоммандс

1. В **Обозреватель решений** выберите узел проекта **шарепоинткоммандс** .

2. В строке меню выберите **проект**,  **Добавить существующий элемент**.

3. В диалоговом окне **Добавление существующего элемента** перейдите к папке, содержащей файлы кода для проекта прожекттемплатевизард, а затем выберите файл кода **коммандидс** .

4. Нажмите стрелку рядом с кнопкой **Добавить** , а затем выберите параметр **Добавить как ссылку** в появившемся меню.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет файл кода в проект **шарепоинткоммандс** в качестве ссылки. Файл кода находится в проекте **прожекттемплатевизард** , но код в файле также компилируется в проект **шарепоинткоммандс** .

5. В проекте **шарепоинткоммандс** добавьте еще один файл кода с именем Commands.

6. Выберите проект шарепоинткоммандс, а затем в строке меню выберите **проект**  >  **Добавить ссылку**.

7. Разверните узел **сборки** , выберите узел **расширения** , а затем установите флажки рядом со следующими сборками:

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

8. Нажмите кнопку **ОК** , чтобы добавить сборки в проект.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Создание модели мастера, диспетчера подписей и идентификаторов команд SharePoint
 Добавьте код в проект Прожекттемплатевизард для реализации следующих компонентов в примере:

- Идентификаторы команд SharePoint. Эти строки указывают команды SharePoint, используемые мастером. Далее в этом пошаговом руководстве вы добавите код в проект Шарепоинткоммандс, чтобы реализовать команды.

- Модель данных мастера.

- Диспетчер подписывания проекта.

  Дополнительные сведения об этих компонентах см. [в разделе Знакомство с компонентами мастера](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>Определение идентификаторов команд SharePoint

1. В проекте Прожекттемплатевизард откройте файл кода Коммандидс и замените все содержимое этого файла следующим кодом.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb" id="Snippet5":::

#### <a name="to-create-the-wizard-model"></a>Создание модели мастера

1. Откройте файл кода Ситеколумнвизардмодел и замените все содержимое этого файла следующим кодом.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs" id="Snippet6":::

#### <a name="to-create-the-project-signing-manager"></a>Создание диспетчера подписывания проекта

1. Откройте файл кода Прожектсигнингманажер и замените все содержимое этого файла следующим кодом.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb" id="Snippet8":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs" id="Snippet8":::

## <a name="create-the-wizard-ui"></a>Создание пользовательского интерфейса мастера
 Добавьте XAML, чтобы определить пользовательский интерфейс окна мастера и два пользовательских элемента управления, которые предоставляют пользовательский интерфейс для страниц мастера, и добавьте код для определения поведения окна и пользовательских элементов управления. Создаваемый Мастер напоминает встроенный мастер для проектов SharePoint в Visual Studio.

> [!NOTE]
> В следующих шагах в проекте будут обнаружены ошибки компиляции после добавления кода XAML или Code в проект. Эти ошибки исчезнут при добавлении кода в последующих шагах.

#### <a name="to-create-the-wizard-window-ui"></a>Создание пользовательского интерфейса окна мастера

1. В проекте Прожекттемплатевизард откройте контекстное меню для файла Визардвиндов. XAML и выберите **Открыть** , чтобы открыть окно в конструкторе.

2. В представлении XAML конструктора замените текущий код XAML следующим кодом XAML. XAML определяет пользовательский интерфейс, включающий заголовок, объект <xref:System.Windows.Controls.Grid> , содержащий страницы мастера, и кнопки навигации в нижней части окна.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml" id="Snippet10":::

    > [!NOTE]
    > Окно, созданное в этом XAML, является производным от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> базового класса. При добавлении пользовательского диалогового окна WPF в Visual Studio рекомендуется создать производное диалоговое окно от этого класса, чтобы обеспечить единообразное оформление с помощью других диалоговых окон Visual Studio и избежать проблем модального диалогового окна, которые могут возникнуть в противном случае. Дополнительные сведения см. в разделе [Создание модальных диалоговых окон и управление ими](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Если вы занимаетесь разработкой проекта Visual Basic, удалите `ProjectTemplateWizard` пространство имен из `WizardWindow` имени класса в `x:Class` атрибуте `Window` элемента. Этот элемент находится в первой строке XAML. Когда все будет готово, первая строка должна выглядеть, как в следующем примере.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Откройте файл кода программной части для файла Визардвиндов. XAML.

5. Замените содержимое этого файла, за исключением `using` объявлений в верхней части файла, на следующий код.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs" id="Snippet4":::

#### <a name="to-create-the-first-wizard-page-ui"></a>Создание первого пользовательского интерфейса страницы мастера

1. В проекте Прожекттемплатевизард откройте контекстное меню для файла «файл кода. XAML», а затем нажмите кнопку **Открыть** , чтобы открыть пользовательский элемент управления в конструкторе.

2. В представлении XAML конструктора замените текущий код XAML следующим кодом XAML. XAML определяет пользовательский интерфейс, содержащий текстовое поле, в котором пользователи могут ввести URL-адрес локальных сайтов, которые будут использоваться для отладки. Пользовательский интерфейс также включает переключатели, с помощью которых пользователи могут указать, является ли проект изолированным.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml" id="Snippet11":::

3. При разработке проекта Visual Basic удалите `ProjectTemplateWizard` пространство имен из `Page1` имени класса в `x:Class` атрибуте `UserControl` элемента. Он находится в первой строке XAML. По завершении первая строка должна выглядеть следующим образом.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Замените содержимое файла «файл кода. XAML», за исключением `using` объявлений в верхней части файла, следующим кодом.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs" id="Snippet2":::

#### <a name="to-create-the-second-wizard-page-ui"></a>Создание второго пользовательского интерфейса страницы мастера

1. В проекте Прожекттемплатевизард откройте контекстное меню для файла Page2. XAML и выберите **Открыть**.

     Пользовательский элемент управления откроется в конструкторе.

2. В представлении XAML замените текущий код XAML следующим кодом XAML. XAML определяет пользовательский интерфейс, который включает раскрывающийся список для выбора базового типа столбца сайта, поле со списком для указания встроенной или пользовательской группы, в которой будет отображаться столбец сайта в коллекции, и текстовое поле для указания имени столбца сайта.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml" id="Snippet12":::

3. При разработке проекта Visual Basic удалите `ProjectTemplateWizard` пространство имен из `Page2` имени класса в `x:Class` атрибуте `UserControl` элемента. Он находится в первой строке XAML. По завершении первая строка должна выглядеть следующим образом.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Замените содержимое файла кода программной части для файла Page2. XAML, за исключением `using` объявлений в верхней части файла, следующим кодом.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs" id="Snippet3":::

## <a name="implement-the-wizard"></a>Реализация мастера
 Определите основные функциональные возможности мастера, реализовав <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс. Этот интерфейс определяет методы, которые Visual Studio вызывает при запуске и завершении работы мастера, а также в определенные моменты времени при запуске мастера.

#### <a name="to-implement-the-wizard"></a>Реализация мастера

1. В проекте Прожекттемплатевизард откройте файл кода Ситеколумнпрожектвизард.

2. Замените все содержимое этого файла следующим кодом.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs" id="Snippet7":::

## <a name="create-the-sharepoint-commands"></a>Создание команд SharePoint
 Создайте две пользовательские команды, вызывающие объектную модель сервера SharePoint. Одна команда определяет, является ли допустимым URL-адрес сайта, который пользователь вводит в мастере. Вторая команда получает все типы полей с указанного сайта SharePoint, чтобы пользователи могли выбрать, какой из них будет использоваться в качестве базового для нового столбца сайта.

#### <a name="to-define-the-sharepoint-commands"></a>Определение команд SharePoint

1. В проекте **шарепоинткоммандс** откройте файл кода команд.

2. Замените все содержимое этого файла следующим кодом.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb" id="Snippet9":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs" id="Snippet9":::

## <a name="checkpoint"></a>Контрольная точка
 На этом этапе в пошаговом руководстве весь код для мастера теперь находится в проекте. Выполните сборку проекта, чтобы убедиться, что компиляция выполняется без ошибок.

#### <a name="to-build-your-project"></a>Построение проекта

1. В строке меню последовательно выберите **Сборка** > **Собрать решение**.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Удаление файла key. snk из шаблона проекта
 В [разделе Пошаговое руководство. Создание элемента проекта столбца сайта с шаблоном проекта. часть 1.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)созданный шаблон проекта содержит файл key. snk, который используется для подписи каждого экземпляра проекта столбца сайта. Этот файл key. snk больше не нужен, так как мастер теперь создает новый файл key. snk для каждого проекта. Удалите файл key. snk из шаблона проекта и удалите ссылки на этот файл.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Удаление файла key. snk из шаблона проекта

1. В **Обозреватель решений** в узле **ситеколумнпрожекттемплате** откройте контекстное меню для файла **Key. snk** и выберите пункт **Удалить**.

2. В появившемся диалоговом окне подтверждения нажмите кнопку **ОК**.

3. В узле **ситеколумнпрожекттемплате** откройте файл ситеколумнпрожекттемплате. VSTEMPLATE, а затем удалите из него следующий элемент.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Сохраните файл и закройте его.

5. В узле **ситеколумнпрожекттемплате** откройте файл ProjectTemplate. csproj или ProjectTemplate. vbproj, а затем удалите `PropertyGroup` из него следующий элемент.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Удалите следующий `None` элемент.

    ```xml
    <None Include="key.snk" />
    ```

7. Сохраните файл и закройте его.

## <a name="associating-the-wizard-with-the-project-template"></a>Связывание мастера с шаблоном проекта
 После реализации мастера необходимо связать мастер с шаблоном проекта **столбца сайта** . Для этого необходимо выполнить три процедуры.

1. Подпишите сборку мастера строгим именем.

2. Получите маркер открытого ключа для сборки мастера.

3. Добавьте ссылку на сборку мастера в VSTEMPLATE-файл для шаблона проекта **столбца сайта** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Подписывание сборки мастера строгим именем

1. В **Обозреватель решений** откройте контекстное меню проекта **прожекттемплатевизард** и выберите пункт **Свойства**.

2. На вкладке **Подпись** установите флажок **Подписать сборку**.

3. В списке **выберите файл ключа строгого имени** выберите **\<New...>** .

4. В диалоговом окне **Создание ключа строгого имени** введите имя нового файла ключа, снимите флажок **защитить файл ключа паролем** и нажмите кнопку **ОК** .

5. Откройте контекстное меню проекта **прожекттемплатевизард** и выберите **Build (собрать** ), чтобы создать файл ProjectTemplateWizard.dll.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Получение токена открытого ключа для сборки мастера

1. В **меню Пуск** последовательно выберите пункты **все программы**, **Microsoft Visual Studio**, **инструменты Visual Studio**, а затем выберите **Командная строка разработчика**.

     Откроется окно командной строки Visual Studio.

2. Выполните следующую команду, заменив *пастовизардассембли* на полный путь к созданной сборке ProjectTemplateWizard.dll для проекта прожекттемплатевизард на компьютере разработчика:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Токен открытого ключа для сборки ProjectTemplateWizard.dll записывается в окно командной строки Visual Studio.

3. Не закрывайте окно командной строки Visual Studio. Токен открытого ключа потребуется во время следующей процедуры.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Добавление ссылки на сборку мастера в VSTEMPLATE-файле

1. В **Обозреватель решений** разверните узел проекта **ситеколумнпрожекттемплате** и откройте файл ситеколумнпрожекттемплате. vstemplate.

2. Рядом с концом файла добавьте следующий `WizardExtension` элемент между `</TemplateContent>` `</VSTemplate>` тегами и. Замените значение *токена* для атрибута на `PublicKeyToken` маркер открытого ключа, полученный в предыдущей процедуре.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Дополнительные сведения об `WizardExtension` элементе см. в разделе [визардекстенсион element &#40;Visual Studio templates&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Сохраните файл и закройте его.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Добавление заменяемых параметров в файл Elements.xml в шаблоне проекта
 Добавьте несколько заменяемых параметров в файл *Elements.xml* в проекте ситеколумнпрожекттемплате. Эти параметры инициализируются в `RunStarted` методе `SiteColumnProjectWizard` класса, который был определен ранее. Когда пользователь создает проект столбца сайта, Visual Studio автоматически заменяет эти параметры в файле *Elements.xml* в новом проекте значениями, указанными в мастере.

 Заменяемый параметр — это маркер, который начинается и заканчивается знаком доллара ($). В дополнение к определению собственных заменяемых параметров можно использовать встроенные параметры, которые определяются и инициализируются системой проектов SharePoint. Дополнительные сведения см. в разделе [Заменяемые параметры](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Добавление заменяемых параметров в файл Elements.xml

1. В проекте Ситеколумнпрожекттемплате замените содержимое файла *Elements.xml* следующим XML-кодом.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     Новый XML изменяет значения `Name` `DisplayName` атрибутов,, `Type` и `Group` на настраиваемые заменяемые параметры.

2. Сохраните файл и закройте его.

## <a name="add-the-wizard-to-the-vsix-package"></a>Добавление мастера в пакет VSIX
 Чтобы развернуть мастер с помощью пакета VSIX, содержащего шаблон проекта столбца сайта, добавьте ссылки на проект мастера и проект команд SharePoint в файл Source. extension. vsixmanifest в проекте VSIX.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Добавление мастера в пакет VSIX

1. В **Обозреватель решений** в проекте **ситеколумнпрожектитем** откройте контекстное меню для файла **source. extension. vsixmanifest** и выберите **Открыть**.

     Visual Studio откроет файл в редакторе манифестов.

2. На вкладке **ресурсы** редактора нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление нового ресурса** .

3. В списке **тип** выберите **Microsoft. VisualStudio. Assembly**.

4. В списке **источник** выберите **проект в текущем решении**.

5. В списке **проект** выберите **прожекттемплатевизард**, а затем нажмите кнопку **ОК** .

6. На вкладке **активы** редактора нажмите кнопку **создать** еще раз.

     Откроется диалоговое окно **Добавление нового ресурса** .

7. В списке **тип** введите **SharePoint. Commands. v4**.

8. В списке **источник** выберите **проект в текущем решении**.

9. В списке **проект** выберите проект **шарепоинткоммандс** , а затем нажмите кнопку **ОК** .

10. В строке меню выберите **Сборка**  >  **сборка решения** и убедитесь, что решение выполняется без ошибок.

## <a name="test-the-wizard"></a>Тестирование мастера
 Теперь все готово для тестирования мастера. Сначала начните отладку решения Ситеколумнпрожектитем в экспериментальном экземпляре Visual Studio. Затем проверьте работу мастера проекта столбца сайта в экспериментальном экземпляре Visual Studio. Наконец, создайте и запустите проект, чтобы убедиться, что столбец сайта работает должным образом.

#### <a name="to-start-debugging-the-solution"></a>Запуск отладки решения

1. Перезапустите Visual Studio с учетными данными администратора, а затем откройте решение Ситеколумнпрожектитем.

2. В проекте Прожекттемплатевизард откройте файл кода Ситеколумнпрожектвизард, а затем добавьте точку останова в первую строку кода в `RunStarted` методе.

3. В строке меню выберите **Отладка**  >  **исключений**.

4. В диалоговом окне **исключения** убедитесь, что сняты **порождаемые** и **необработанные** флажки для **исключений среды** CLR, а затем нажмите кнопку **ОК** .

5. Запустите отладку, нажав клавишу **F5** , или в строке меню выберите **Отладка**  >  **начать отладку**.

     Visual Studio устанавливает расширение в%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 и запускает экспериментальный экземпляр Visual Studio. Вы протестируете элемент проекта в этом экземпляре Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Тестирование мастера в Visual Studio

1. В экспериментальном экземпляре Visual Studio в строке меню выберите **файл**  >  **создать**  >  **проект**.

2. Разверните узел **Visual C#** или узел **Visual Basic** (в зависимости от языка, поддерживаемого шаблоном проекта) разверните узел **SharePoint** , а затем выберите узел **2010** .

3. В списке шаблонов проектов выберите **столбец сайта**, назовите проект **ситеколумнвизардтест**, а затем нажмите кнопку **ОК** .

4. Убедитесь, что код в другом экземпляре Visual Studio остановлен в точке останова, заданной ранее в `RunStarted` методе.

5. Продолжайте отладку проекта, нажав клавишу **F5** , или в строке меню выберите пункт **Отладка**  >  **продолжить**.

6. В **мастере настройки SharePoint** введите URL-адрес сайта, который требуется использовать для отладки, а затем нажмите кнопку **Далее** .

7. На второй странице **мастера настройки SharePoint** сделайте следующее:

   - В списке **тип** выберите **логическое значение**.

   - В списке **Группа** выберите **пользовательские столбцы да/нет**.

   - В поле **имя** введите **Мои столбцы да и нет**, а затем нажмите кнопку **Готово** .

     В **Обозреватель решений** появится новый проект, содержащий элемент проекта с именем **field1**, а Visual Studio откроет файл *Elements.xml* проекта в редакторе.

8. Убедитесь, что *Elements.xml* содержит значения, указанные в мастере.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Тестирование столбца сайта в SharePoint

1. В экспериментальном экземпляре Visual Studio нажмите клавишу **F5** .

     Столбец сайта упаковывается и развертывается на сайте SharePoint, который указывается свойством **URL-адреса сайта** проекта. В веб-браузере откроется страница по умолчанию этого сайта.

    > [!NOTE]
    > Если откроется диалоговое окно **Отладка скрипта отключено** , нажмите кнопку **Да** , чтобы продолжить отладку проекта.

2. В меню **действия сайта** выберите пункт **Параметры сайта**.

3. На странице Параметры сайта в разделе **коллекции** выберите ссылку **столбцы сайта** .

4. Убедитесь, что в списке столбцов сайта **Пользовательская группа "да/нет столбцов"** содержит столбец с именем **"да/нет"**, а затем закройте веб-браузер.

## <a name="clean-up-the-development-computer"></a>Очистка компьютера разработчика
 После завершения тестирования элемента проекта удалите шаблон проекта из экспериментального экземпляра Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Очистка компьютера разработки

1. В экспериментальном экземпляре Visual Studio в строке меню выберите **инструменты**  >  **расширения и обновления**.

     Появится диалоговое окно **Расширения и обновления**.

2. В списке расширений выберите **столбец сайта**, а затем нажмите кнопку **Удалить** .

3. В появившемся диалоговом окне нажмите кнопку **Да** , чтобы подтвердить удаление расширения, а затем нажмите кнопку **Перезагрузить сейчас** для завершения удаления.

4. Закройте как экспериментальный экземпляр Visual Studio, так и экземпляр, в котором открыто решение Кустомактионпрожектитем.

     Дополнительные сведения о развертывании [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] расширений см. в [разделе Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Практическое руководство. Использование мастеров для шаблонов проекта](../extensibility/how-to-use-wizards-with-project-templates.md)
