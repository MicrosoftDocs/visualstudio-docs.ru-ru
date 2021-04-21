---
title: Программирование надстроек VSTO
description: Узнайте, как можно использовать класс ThisAddIn для выполнения таких задач, как доступ к объектной модели Microsoft Office ведущего приложения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2ee62f35b0626139a8080649076d2ac941366a26
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828713"
---
# <a name="program-vsto-add-ins"></a>Программирование надстроек VSTO
  Если приложение Microsoft Office расширяется путем создания надстройки VSTO, код создается непосредственно для класса `ThisAddIn` соответствующего проекта. Этот класс можно использовать для выполнения таких задач, как получение доступа к объектной модели ведущего приложения Microsoft Office, настройка пользовательского интерфейса приложения, а также предоставление объектов созданной надстройки VSTO другим решениям Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Создание кода для надстроек VSTO несколько отличается от работы над другими типами проектов в Visual Studio. Многие отличия связаны с тем, каким образом объектные модели Office предоставляются управляемому коду. Дополнительные сведения см. [в статье написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md).

 Общие сведения о надстройках VSTO и других типах решений, которые можно создать с помощью средств разработки Office в Visual Studio, см. в статье [Общие сведения о разработке решений office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Использование класса ThisAddIn
 Создание кода надстройки VSTO начинается в классе `ThisAddIn` . Visual Studio автоматически создает этот класс в файле кода *ThisAddIn. vb* (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) или *ThisAddIn. CS* (в C#) в проекте надстройки VSTO. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] автоматически создает экземпляр этого класса при загрузке надстройки VSTO приложением Microsoft Office.

 В классе `ThisAddIn` существует два обработчика событий по умолчанию. Для выполнения кода при загрузке надстройки VSTO следует добавить код в обработчик событий `ThisAddIn_Startup` . Для выполнения кода непосредственно перед выгрузкой надстройки VSTO следует добавить код в обработчик событий `ThisAddIn_Shutdown` . Дополнительные сведения об этих обработчиках событий см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> В Outlook обработчик событий `ThisAddIn_Shutdown` не вызывается при каждой выгрузке надстройки VSTO по умолчанию. Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Доступ к объектной модели ведущего приложения
 Доступ к объектной модели ведущего приложения можно получить с помощью поля `Application` класса `ThisAddIn` . Это поле возвращает объект, представляющий текущий экземпляр ведущего приложения. В приведенной ниже таблице представлены типы возвращаемых значений для поля `Application` в каждом проекте надстройки VSTO.

|Ведущее приложение|Тип возвращаемого значения|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Приложение](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 В следующем примере кода показано, как использовать `Application` поле для создания новой книги в надстройке VSTO для Microsoft Office Excel. Код в примере должен выполняться из класса `ThisAddIn` .

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Чтобы выполнить это же действие без использования класса `ThisAddIn` , используйте для получения доступа к классу `Globals` объект `ThisAddIn` . Дополнительные сведения об `Globals` объекте см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Дополнительные сведения об объектных моделях конкретных приложений Microsoft Office см. в следующих статьях:

- [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)

- [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)

- [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)

- [Решения InfoPath](../vsto/infopath-solutions.md)

- [Решения PowerPoint](../vsto/powerpoint-solutions.md)

- [Решения проекта](../vsto/project-solutions.md)

- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a> Доступ к документу при запуске приложения Office
 Многие приложения [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] и ни одно приложение [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] не открывают какой-либо документ при своем запуске автоматически. Поэтому не добавляйте код в `ThisAdd-In_Startup` обработчик событий, если для кода требуется открыть документ. Добавьте код в событие, которое создает приложение Office, когда пользователь создает или открывает документ. В этом случае документ точно будет открыт, прежде чем созданный вами код проведет с ним какие-то операции.

 В приведенном ниже примере код работает с документом Word только в том случае, если пользователь создает новый или открывает существующий документ.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet3":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet3":::

### <a name="thisaddin-members-to-use-for-other-tasks"></a>Участники ThisAddIn, используемые для других задач
 В приведенной ниже таблице описаны наиболее распространенные задачи и члены класса `ThisAddIn` , которые можно использовать для выполнения этих задач.

|Задача|Используемый член|
|----------|-------------------|
|Выполнение кода для инициализации надстройки VSTO при ее загрузке.|Добавьте код в метод `ThisAddIn_Startup` . Этот метод является обработчиком событий по умолчанию для события <xref:Microsoft.Office.Tools.AddInBase.Startup> . Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).|
|Выполнение кода для очистки используемых надстройкой VSTO ресурсов перед выгрузкой надстройки VSTO.|Добавьте код в метод `ThisAddIn_Shutdown` . Этот метод является обработчиком событий по умолчанию для события <xref:Microsoft.Office.Tools.AddInBase.Shutdown> . Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md). **Примечание.**  В Outlook по умолчанию `ThisAddIn_Shutdown` обработчик событий не всегда вызывается при выгрузке надстройки VSTO. Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).|
|Отображение настраиваемой области задач.|Используйте поле `CustomTaskPanes` . Дополнительные сведения см. в разделе [настраиваемые области задач](../vsto/custom-task-panes.md).|
|Предоставление доступа к объектам в надстройке VSTO другим решениям Microsoft Office.|Переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Дополнительные сведения см. [в разделе вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Настройка функции в системе Microsoft Office путем реализации интерфейса расширяемости.|Переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> для возврата экземпляра класса, который реализует интерфейс. Дополнительные сведения см. в разделе [Настройка функций пользовательского интерфейса с помощью интерфейсов расширения](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Примечание.**  Чтобы настроить Ribbon, можно также переопределить <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> метод.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Общие сведения о проектировании класса ThisAddIn
 В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], интерфейсом является <xref:Microsoft.Office.Tools.AddIn> . Класс `ThisAddIn` является производным от класса <xref:Microsoft.Office.Tools.AddInBase> . Этот базовый класс перенаправляет все вызовы к членам внутренней реализации интерфейса <xref:Microsoft.Office.Tools.AddIn> в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

 В проектах надстроек VSTO для Outlook класс `ThisAddIn` является производным от класса `Microsoft.Office.Tools.Outlook.OutlookAddIn` в проектах, предназначенных для .NET Framework 3.5, или от класса <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Эти базовые классы предоставляют дополнительные функции для поддержки областей форм. Дополнительные сведения о регионах форм см. в разделе [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Настройка пользовательского интерфейса Microsoft Office приложений
 Используя надстройку VSTO, можно настроить пользовательский интерфейс для приложений Microsoft Office программными средствами. Например, можно настроить ленту таким образом, чтобы в ней отображалась настраиваемая панель задач, или создать настраиваемую область формы в Outlook. Дополнительные сведения см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

 Visual Studio предоставляет конструкторы и классы, которые можно использовать для создания настраиваемых областей задач, настроек ленты и областей формы Outlook. Такие конструкторы и классы упрощают процесс настройки этих функций. Дополнительные сведения см. в статьях [пользовательские области задач](../vsto/custom-task-panes.md), [конструктор лент](../vsto/ribbon-designer.md)и [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md).

 Если какую-то из этих функций необходимо настроить способом, который не поддерживается классами и конструкторами, можно реализовать эти функции в надстройке VSTO *интерфейса расширяемости* . Дополнительные сведения см. в разделе [Настройка функций пользовательского интерфейса с помощью интерфейсов расширения](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 Кроме того, можно изменить пользовательский интерфейс документов Word и книг Excel, создавая ведущие элементы, которые расширяют поведение документов и книг. Это позволяет добавлять управляемые элементы управления в документы и листы. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Вызов кода в надстройках VSTO из других решений
 Доступ к объектам в надстройке VSTO можно предоставлять другим решениям, включая решения Office. Это полезно, если надстройка VSTO предоставляет службу, доступ к которой нужно предоставить другим решениям. Например, если у вас есть Надстройка VSTO для Microsoft Office Excel, которая выполняет вычисления с финансовыми данными из веб-службы, другие решения могут выполнять эти вычисления, вызывая надстройку VSTO для Excel во время выполнения.

 Дополнительные сведения см. [в разделе вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>См. также статью
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Пошаговое руководство. вызов кода в надстройке VSTO из VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Настройка функций пользовательского интерфейса с помощью интерфейсов расширяемости](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
