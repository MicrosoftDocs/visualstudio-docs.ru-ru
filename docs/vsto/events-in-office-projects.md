---
title: События в проектах Office
description: Узнайте, как каждый шаблон проекта Office создает несколько обработчиков событий, и как эти обработчики событий слегка отличаются от обработчиков событий для надстроек VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: be1625be3d8c3fce409562be948c83a34d40d7b1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825684"
---
# <a name="events-in-office-projects"></a>События в проектах Office
  Каждый шаблон проекта Office автоматически создает несколько обработчиков событий. Обработчики событий для настроек на уровне документа несколько отличаются от обработчиков событий для надстроек VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Проекты уровня документа
 Visual Studio предоставляет сформированный код для новых или существующих документов или листов в настройках на уровне документа. Этот код создает два различных события: **Startup** и **Shutdown**.

### <a name="startup-event"></a>Startup - событие
 Событие **Startup** возникает для каждого ведущего элемента (документа, книги или листа) после запуска документа и всех кодов инициализации в сборке. Это самая последняя операция, запускаемая в конструкторе класса, в котором выполняется ваш код. Дополнительные сведения о ведущих элементах см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

 При создании проекта на уровне документа Visual Studio создает обработчики событий для события **Startup** в созданных файлах кода:

- Для проектов Microsoft Office Word обработчик событий имеет имя `ThisDocument_Startup`.

- Для проектов Microsoft Office Excel обработчики событий имеют следующие имена:

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown - событие
 Событие **Shutdown** возникает для каждого ведущего элемента (документа или листа), когда домен приложения, в который загружен ваш код, готов к выгрузке. Это самая последняя операция, которая должна быть вызвана в классе при выгрузке.

 При создании проекта на уровне документа Visual Studio создает обработчики событий для события **Shutdown** в созданных файлах кода:

- Для проектов Microsoft Office Word обработчик событий имеет имя `ThisDocument_Shutdown`.

- Для проектов Microsoft Office Excel обработчики событий имеют следующие имена:

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> Не удаляйте программным образом элементы управления во время работы обработчика событий **Shutdown** документа. Если возникает событие **Shutdown** , элементы пользовательского интерфейса документа становятся недоступными. Если элементы управления необходимо удалить до закрытия приложения, добавьте свой код в другой обработчик событий, например, **BeforeClose** или **BeforeSave**.

### <a name="event-handler-method-declarations"></a>Объявления методов обработчиков событий
 В каждое объявление метода обработчика событий передаются одни и те же аргументы: *sender* и *e*. В Excel аргумент *sender* ссылается на лист, например, `Sheet1` или `Sheet2`. В Microsoft Word аргумент *sender* ссылается на документ. Аргумент *e* ссылается на стандартные аргументы для события, которые не используются в этом случае.

 В следующем примере кода показаны обработчики событий по умолчанию в проектах на уровне документа для Word.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet121":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet121":::

 В следующем примере кода показаны обработчики событий по умолчанию в проектах на уровне документа для Excel.

> [!NOTE]
> В следующем примере кода показаны обработчики событий в классе `Sheet1` . Имена обработчиков событий в других классах ведущих элементов соответствуют имени класса. Например, в классе `Sheet2` обработчик событий **Startup** имеет имя `Sheet2_Startup`. В классе `ThisWorkbook` обработчик событий **Startup** имеет имя `ThisWorkbook_Startup`.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet83":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet83":::

### <a name="order-of-events-in-document-level-excel-projects"></a>Порядок событий в проектах Excel на уровне документа
 Обработчики **Startup** событий в проектах Excel вызываются в следующем порядке:

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Другие листы по порядку.

   Обработчики событий **Shutdown** в решении книги вызываются в следующем порядке:

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Другие листы по порядку.

    Порядок определяется при компиляции проекта. Если пользователь изменяет порядок листов во время выполнения, это не приводит к изменению порядка, в котором появляются события при очередном открытии или закрытии книги.

## <a name="vsto-add-in-projects"></a>Проекты надстроек VSTO
 Visual Studio предоставляет код, созданный в надстройках VSTO. Этот код вызывает два разных события: <xref:Microsoft.Office.Tools.AddInBase.Startup> и <xref:Microsoft.Office.Tools.AddInBase.Shutdown> .

### <a name="startup-event"></a>Startup - событие
 Событие <xref:Microsoft.Office.Tools.AddIn.Startup> возникает после загрузки надстройки VSTO и запуска всего кода инициализации в сборке. Это событие обрабатывается методом `ThisAddIn_Startup` в файле сформированного кода.

 Код в обработчике событий `ThisAddIn_Startup` — это первый код пользователя, подлежащий выполнению, если надстройка VSTO не переопределяет метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . В этом случае обработчик событий `ThisAddIn_Startup` вызывается после <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.

 Не добавляйте код в `ThisAdd-In_Startup` обработчик событий, если для кода требуется открыть документ. Добавьте код в событие, которое создает приложение Office, когда пользователь создает или открывает документ. Дополнительные сведения см. в разделе [доступ к документу при запуске приложения Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Дополнительные сведения о последовательности запуска надстроек VSTO см. в разделе [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="shutdown-event"></a>Shutdown - событие
 Событие <xref:Microsoft.Office.Tools.AddInBase.Shutdown> возникает, когда домен приложения, в котором загружен ваш код, готов к выгрузке. Это событие обрабатывается методом `ThisAddIn_Shutdown` в файле сформированного кода. Этот обработчик событий — последний код пользователя, выполняемый при выгрузке надстройки VSTO.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Событие завершения работы в надстройках VSTO для Outlook
 Событие <xref:Microsoft.Office.Tools.AddInBase.Shutdown> возникает только в том случае, когда пользователь отключает надстройку VSTO с помощью диалогового окна надстроек COM в Outlook. Оно не возникает при завершении работы Outlook. Если у вас есть код, который должен выполняться при завершении работы Outlook, обработайте одно из следующих событий:

- Событие <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> объекта <xref:Microsoft.Office.Interop.Outlook.Application> .

- Событие <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> объекта <xref:Microsoft.Office.Interop.Outlook.Explorer> .

> [!NOTE]
> Чтобы Outlook принудительно создавал событие <xref:Microsoft.Office.Tools.AddInBase.Shutdown> при выходе, можно изменить реестр. Однако, если администратор отменяет эту настройку, любой код, добавленный в метод `ThisAddIn_Shutdown` , больше не будет выполняться при завершении работы Outlook. Дополнительные сведения см. в разделе [изменения завершения работы Outlook 2010](/previous-versions/office/developer/office-2010/ee720183(v=office.14)).

## <a name="see-also"></a>См. также статью
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)
