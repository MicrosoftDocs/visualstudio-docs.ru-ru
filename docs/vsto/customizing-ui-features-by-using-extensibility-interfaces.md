---
title: Настройка функций пользовательского интерфейса с помощью интерфейсов расширяемости
description: Узнайте, что средства разработки Office в Visual Studio предоставляют интерфейсы расширения, помогающие настраивать функции пользовательского интерфейса.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 86f4e5f286d817fb3f657e40399eccd3a2b4de73
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828037"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Настройка функций пользовательского интерфейса с помощью интерфейсов расширяемости
  Средства разработки Office в Visual Studio предоставляют классы и конструкторы, которые обрабатывают многие сведения о реализации, когда вы используете их для создания настраиваемых панелей задач, настроек ленты и областей форм Outlook в надстройке VSTO. Однако при наличии особых потребностей вы также можете реализовать *интерфейс расширения* для каждого компонента.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Общие сведения о интерфейсах расширяемости
 Microsoft Office определяет набор интерфейсов расширения, реализуемых надстройками VSTO модели COM для настройки определенных компонентов, таких как лента. Эти интерфейсы обеспечивают полный контроль над компонентами, к которым они предоставляют доступ. Тем не менее реализация этих интерфейсов требует некоторого знания принципов взаимодействия с COM в управляемом коде. В некоторых случаях модель программирования этих интерфейсов может быть непонятной для разработчиков, привыкших к .NET Framework.

 При создании надстройки VSTO с помощью шаблонов проектов Office в Visual Studio нет необходимости реализовывать интерфейсы расширения для настройки таких компонентов, как лента. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] реализует эти интерфейсы без вашего вмешательства. Кроме того, вы можете использовать более понятные классы и конструкторы, предоставляемые Visual Studio. Однако при желании интерфейсы расширения можно реализовать прямо в надстройке VSTO.

 Дополнительные сведения о классах и конструкторах, предоставляемых Visual Studio для этих функций, см. в разделе [пользовательские области задач](../vsto/custom-task-panes.md), [конструктор лент](../vsto/ribbon-designer.md)и [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Интерфейсы расширяемости, которые можно реализовать в надстройке VSTO
 В таблице ниже перечислены интерфейсы расширения, которые можно реализовать, а также поддерживающие их приложения.

|Интерфейс|Описание|Приложения|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Реализуйте этот интерфейс для настройки пользовательского интерфейса ленты. **Примечание.**  В проект можно добавить элемент **Лента (XML)** для создания реализации по умолчанию <xref:Microsoft.Office.Core.IRibbonExtensibility> в надстройке VSTO. Дополнительные сведения см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Реализуйте этот интерфейс для создания настраиваемой панели задач.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Реализуйте этот интерфейс для создания области формы Outlook.|Outlook|

 Существуют другие интерфейсы расширения, которые определены Microsoft Office, такие как <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>и <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio не поддерживает реализацию этих интерфейсов в надстройке VSTO, созданной с помощью шаблонов проектов Office.

## <a name="use-extensibility-interfaces"></a>Использование интерфейсов расширяемости
 Чтобы настроить компонент пользовательского интерфейса с помощью интерфейса расширения, реализуйте соответствующий интерфейс в проекте надстройки VSTO. Затем переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> для возврата экземпляра класса, который реализует интерфейс.

 Пример приложения, демонстрирующий способы реализации <xref:Microsoft.Office.Core.IRibbonExtensibility> <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> интерфейсов, и в надстройке VSTO для Outlook, см. в примере диспетчера пользовательского интерфейса в примерах [разработки для Office](../vsto/office-development-samples.md).

### <a name="example-of-implementing-an-extensibility-interface"></a>Пример реализации интерфейса расширяемости
 В следующем примере кода показан пример простой реализации интерфейса <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> для создания настраиваемой панели задач. В данном примере определяются два класса.

- Класс `TaskPaneHelper` реализует <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> для создания и отображения настраиваемой панели задач.

- Класс `TaskPaneUI` предоставляет пользовательский интерфейс панели задач. Атрибуты класса `TaskPaneUI` делают его доступным для COM, что позволяет приложениям Microsoft Office обнаруживать класс. В этом примере пользовательский интерфейс представляет собой пустой интерфейс <xref:System.Windows.Forms.UserControl>, однако вы можете добавить элементы управления, изменив код.

  > [!NOTE]
  > Чтобы предоставить класс `TaskPaneUI` COM, для проекта необходимо также задать свойство **Регистрация для COM-взаимодействия** .

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet1":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet1":::

  Дополнительные сведения о реализации см <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> . в разделе [Создание настраиваемых областей задач в системе 2007 Office](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) в документации по Microsoft Office.

### <a name="example-of-overriding-the-requestservice-method"></a>Пример переопределения метода RequestService
 Следующий пример кода демонстрирует переопределение метода <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> для возврата экземпляра класса `TaskPaneHelper` из предыдущего примера кода. Он проверяет значение параметра *serviceGuid* , чтобы определить, какой интерфейс запрашивается, а затем возвращает объект, который реализует интерфейс.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet2":::

## <a name="see-also"></a>См. также статью
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
