---
title: Пошаговое руководство. Создание первой надстройки VSTO для Outlook
description: Создание надстройки уровня приложения для Microsoft Outlook. Эта функция доступна для самого приложения, независимо от того, какой элемент Outlook открыт.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Outlook [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a6bcc134096284579e1097edf0e958105f48cfcb
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824293"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Пошаговое руководство. Создание первой надстройки VSTO для Outlook
  В этом пошаговом руководстве показано, как создать надстройку VSTO для Microsoft Office Outlook. Функции, создаваемые в подобном решении, доступны для приложения независимо от того, какой элемент Outlook открыт. Дополнительные сведения см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- создание проекта надстройки VSTO для Outlook;

- написание кода, использующего объектную модель Outlook для добавления текста в поле темы и текст нового электронного сообщения;

- Построение и запуск проекта для тестирования.

- Удаление завершенного проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-the-project"></a>Создание проекта

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Создание проекта Outlook в Visual Studio

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.

4. В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .

5. В списке шаблонов проектов выберите шаблон проекта надстройки VSTO Outlook.

6. В поле **Имя** введите **FirstOutlookAddIn**.

7. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **FirstOutlookAddIn** и открывает файл кода **ThisAddIn** в редакторе.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Написание кода, добавляющего текст в каждое новое сообщение электронной почты
 Затем добавьте код в файл ThisAddIn. Новый код использует объектную модель Outlook для добавления текста к каждому новому почтовому сообщению. По умолчанию файл кода ThisAddIn содержит следующий созданный код:

- Частичное определение класса `ThisAddIn` . Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели Outlook. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Оставшаяся часть `ThisAddIn` класса определяется в скрытом файле кода, который не следует изменять.

- Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown` . Эти обработчики событий вызываются, когда Outlook загружает и выгружает надстройку VSTO. Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения ресурсов, используемых вашей надстройкой VSTO при ее выгрузке. Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Добавление текста в поле темы и текст каждого нового электронного сообщения

1. В файле кода ThisAddIn объявите поле с именем `inspectors` в классе `ThisAddIn` . Поле `inspectors` содержит ссылку на коллекцию окон инспектора в текущем экземпляре Outlook. Эта ссылка не позволит сборщику мусора освободить память, содержащую обработчик событий для <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. Замените метод `ThisAddIn_Startup` приведенным ниже кодом. Этот код присоединяет обработчик событий к <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb" id="Snippet2":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs" id="Snippet2":::

3. В файл кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код. Он присоединяет обработчик событий к <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    Когда пользователь создает сообщение, этот обработчик событий добавляет текст в строку темы и текст сообщения.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb" id="Snippet3":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs" id="Snippet3":::

   Для изменения каждого нового сообщения в приведенных выше примерах кода используются следующие объекты.

- Поле `Application` класса `ThisAddIn` . Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.Outlook.Application> , который представляет текущий экземпляр Outlook.

- Параметр `Inspector` обработчика событий для события <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> . Параметр `Inspector` — это объект <xref:Microsoft.Office.Interop.Outlook.Inspector> , представляющий окно инспектора нового почтового сообщения. Дополнительные сведения см. в разделе [решения Outlook](../vsto/outlook-solutions.md).

## <a name="test-the-project"></a>Тестирование проекта
 При построении и запуске проекта убедитесь, что текст отображается в строке темы и тексте нового почтового сообщения.

### <a name="to-test-the-project"></a>Тестирование проекта

1. Нажмите клавишу **F5** для построения и запуска проекта.

     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта. Visual Studio также создает ряд записей реестра, которые позволяют Outlook обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO. Дополнительные сведения см. в статье [Обзор процесса сборки решения Office](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).

2. В Outlook создайте новое почтовое сообщение.

3. Убедитесь, что следующий текст добавляется в строку темы и текст сообщения.

     **Этот текст добавляется с помощью кода.**

4. Закройте Outlook.

## <a name="clean-up-the-project"></a>Очистить проект
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности. В противном случае надстройка VSTO будет запускаться при каждом открытии Outlook на компьютере разработчика.

### <a name="to-clean-up-your-project"></a>Очистка проекта

1. В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.

## <a name="next-steps"></a>Дальнейшие действия
 Теперь, когда вы создали базовую надстройку VSTO для Outlook, изучите более подробную информацию о разработке надстроек VSTO в следующих разделах.

- Общие задачи программирования, которые можно выполнять с помощью надстроек VSTO для Outlook. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Использование объектной модели Outlook. Дополнительные сведения см. в разделе [решения Outlook](../vsto/outlook-solutions.md).

- Настройка пользовательского интерфейса Outlook, например путем добавления настраиваемой вкладки на ленту или создания собственной настраиваемой области задач. Дополнительные сведения см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

- Построение и отладка надстроек VSTO для Outlook. Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).

- Развертывание надстроек VSTO для Outlook. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>См. также статью
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Решения Outlook](../vsto/outlook-solutions.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Создание решений Office](../vsto/building-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)
