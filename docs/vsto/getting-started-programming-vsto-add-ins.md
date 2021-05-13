---
title: Приступая к программированию надстроек VSTO
description: Узнайте, как можно использовать надстройки VSTO для автоматизации Microsoft Office приложений, расширения функций приложения и настройки пользовательского интерфейса приложения.
ms.custom: SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1757dd6042536b6a042e67a8b3dcd9b12a2ea758
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848296"
---
# <a name="get-started-programming-vsto-add-ins"></a>Приступая к программированию надстроек VSTO
> [!IMPORTANT]
> VSTO полагается на [платформа .NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Надстройки COM также можно записать с помощью платформа .NET Framework. Надстройки Office нельзя создавать с помощью [.NET Core и .NET 5 +](https://docs.microsoft.com/dotnet/core/dotnet-five), последних версий .NET. Это связано с тем, что .NET Core/. NET 5 + не может работать вместе с платформа .NET Framework в одном процессе и может привести к сбоям при загрузке надстройки. Вы можете продолжить использовать платформа .NET Framework для написания надстроек VSTO и COM для Office. Корпорация Майкрософт не будет обновлять VSTO или платформу надстройки COM для использования .NET Core или .NET 5 +. Для создания серверной части веб-надстроек [Office](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)можно воспользоваться преимуществами .NET Core и .NET 5 +, включая ASP.NET Core.

  Надстройки VSTO можно использовать для автоматизации приложений Microsoft Office, расширения функциональных возможностей приложения и настройки пользовательского интерфейса приложения. Сведения о сравнении надстроек VSTO с другими типами решений Office, которые можно создать с помощью Visual Studio, см. в статье [Общие сведения о разработке решений office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Создание проектов надстроек VSTO
 Создание проектов надстроек VSTO с помощью одного из шаблонов проектов надстроек VSTO в диалоговом окне " **Создание проекта** ". Эти шаблоны включают в себя необходимые ссылки на сборки и файлы проекта. Visual Studio предоставляет шаблоны проектов надстроек VSTO для большинства приложений Office.

 Дополнительные сведения о создании проекта надстройки VSTO см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).

## <a name="develop-vsto-add-in-projects"></a>Разработка проектов надстроек VSTO
 При создании проекта надстройки VSTO Visual Studio автоматически создает файл кода *ThisAddIn. vb* (в [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) или *ThisAddIn. CS* (в C#). Этот файл содержит `ThisAddIn` класс, предоставляющий основу для надстройки VSTO. Члены этого класса можно использовать для выполнения кода при загрузке или выгрузке надстройки VSTO, при доступе к объектной модели ведущего приложения, а также при расширении функциональных возможностей приложения. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Автоматизация приложений с помощью объектных моделей
 Объектные модели приложений Microsoft Office предоставляют множество типов, которые можно использовать в надстройке VSTO. Эти типы можно использовать для автоматизации приложения. Например, можно программным образом создавать и отправлять сообщение электронной почты в Outlook или можно открыть документ и добавить контент в Word. Дополнительные сведения о том, как получить доступ к объектной модели ведущего приложения в коде, см. в разделе [программирование VSTO-надстроек](../vsto/programming-vsto-add-ins.md).

 Дополнительные сведения об объектных моделях конкретных приложений Microsoft Office см. в следующих статьях:

- [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)

- [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)

- [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)

- [Решения InfoPath](../vsto/infopath-solutions.md)

- [Решения PowerPoint](../vsto/powerpoint-solutions.md)

- [Решения проекта](../vsto/project-solutions.md)

- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Настройка пользовательского интерфейса приложений
 Существует несколько различных способов настройки пользовательского интерфейса ведущего приложения с помощью надстройки VSTO.

- Для Excel и Word в документы можно добавлять управляемые элементы управления. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

- Можно настроить ленту, если ее поддерживает приложение. Дополнительные сведения см. в статье [Общие сведения о ленте](../vsto/ribbon-overview.md).

- Можно создать настраиваемую область задач, если ее поддерживает приложение. Дополнительные сведения см. в разделе [настраиваемые области задач](../vsto/custom-task-panes.md).

- Для Outlook можно создать пользовательскую область формы. Дополнительные сведения см. в разделе [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md).

- Для всех приложений Microsoft Office формы Windows Forms можно отображать в надстройке VSTO.

  Дополнительные сведения о настройке пользовательского интерфейса Microsoft Office приложений см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения о создании надстроек VSTO см. в следующих пошаговых руководствах.

- [Пошаговое руководство. Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Пошаговое руководство. Создание первого Add-In VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Пошаговое руководство. Создание первой надстройки VSTO для Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Пошаговое руководство. Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  В этих пошаговых руководствах рассматриваются средства разработки решений на базе Office в Visual Studio и модель программирования для надстроек VSTO.

  Список разделов, в которых описаны некоторые распространенные задачи в проектах Office, см. в разделе [Общие задачи в программировании Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>См. также раздел
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Приступая к работе &#40;разработке решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
