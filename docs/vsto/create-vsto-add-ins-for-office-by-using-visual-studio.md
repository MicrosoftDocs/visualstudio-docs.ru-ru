---
title: Создание надстроек VSTO для Office с помощью Visual Studio
description: Узнайте, как можно использовать средства разработчика Microsoft Office в Visual Studio для создания платформа .NET Framework приложений, расширяющих Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 990caeec642a745bec5b6e0f2d29ff5d6213d095
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848322"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Создание надстроек VSTO для Office с помощью Visual Studio
> [!IMPORTANT]
> VSTO полагается на [платформа .NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Надстройки COM также можно записать с помощью платформа .NET Framework. Надстройки Office нельзя создавать с помощью [.NET Core и .NET 5 +](https://docs.microsoft.com/dotnet/core/dotnet-five), последних версий .NET. Это связано с тем, что .NET Core/. NET 5 + не может работать вместе с платформа .NET Framework в одном процессе и может привести к сбоям при загрузке надстройки. Вы можете продолжить использовать платформа .NET Framework для написания надстроек VSTO и COM для Office. Корпорация Майкрософт не будет обновлять VSTO или платформу надстройки COM для использования .NET Core или .NET 5 +. Для создания серверной части веб-надстроек [Office](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)можно воспользоваться преимуществами .NET Core и .NET 5 +, включая ASP.NET Core.

  Вы можете использовать инструменты разработчика Microsoft Office в Visual Studio для создания приложений платформы .NET Framework, которые расширяют возможности Office. Эти приложения также называются *решениями Office*.

 Инструменты разработчика Office предоставляют функции, помогающие создавать решения Office в соответствии с различными бизнес-требованиями. В состав инструментов входят шаблоны проектов, помогающие создавать решения Office, используя язык программирования Visual Basic или Visual C#, и визуальные конструкторы, помогающие создавать настраиваемые пользовательские интерфейсы для решений Office.

[!include[Add-ins note](includes/addinsnote.md)]

 Последние сведения о разработке решений Office см. в [центре разработчиков Microsoft Office](https://developer.microsoft.com/office/docs).

## <a name="in-this-section"></a>Содержание раздела
- [Приступая к работе &#40;разработке решений Office в Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)

 Ссылки на сведения о настройке компьютера разработчика для создания решений Office, первых шагах по созданию решений Office, а также новых возможностях разработки решений Office в Visual Studio.

- [Обновление и перенос решений Office](upgrading-and-migrating-office-solutions.md)

 Ссылки на сведения о процессе обновления для проектов, созданных с помощью предыдущих версий Visual Studio.

- [Архитектура решений Office в Visual Studio](architecture-of-office-solutions-in-visual-studio.md)

 Ссылки на сведения о том, как работают решения Office, в том числе о настройках уровня документа и надстройках VSTO.

- [Разработка и создание решений Office](designing-and-creating-office-solutions.md)

 Сведения о создании проектов Office и их настройке в Visual Studio.

- [Разработка решений Office](developing-office-solutions.md)

 Сведения об использовании управляемого кода в решениях Office, в том числе о настройке пользовательского интерфейса Office, о работе с данными и об устранении неполадок.

- [Решения Excel](excel-solutions.md)

 Сведения об автоматизации работы Excel, о создании решений Excel, а также о характерных для Excel проблемах, связанных с глобализацией.

- [Решения InfoPath](infopath-solutions.md)

 Сведения о способах создания шаблонов форм и надстроек VSTO для InfoPath.

- [Решения Outlook](outlook-solutions.md)

 Сведения об автоматизации работы Outlook и о создании надстроек VSTO и областей форм для Outlook.

- [Решения PowerPoint](powerpoint-solutions.md)

 Сведения об автоматизации работы PowerPoint и о создании надстроек VSTO PowerPoint.

- [Решения проекта](project-solutions.md)

 Содержит сведения о том, как автоматизировать Microsoft Office проекта и создать надстройки VSTO для проекта.

- [Решения Visio](visio-solutions.md)

 Сведения об автоматизации работы Visio и о создании надстроек VSTO Visio.

- [Решения Word](word-solutions.md)

 Сведения об автоматизации работы Word и о создании решений Word.

- [Создание решений Office](building-office-solutions.md)

 Сведения о различиях между созданием проектов Office и других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Отладка проектов Office](debugging-office-projects.md)

 Сведения о различиях между отладкой проектов Office и других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Безопасные решения Office](securing-office-solutions.md)

 Сведения о работе функций обеспечения безопасности в решениях Office.

- [Развертывание решения Office](deploying-an-office-solution.md)

 Сведения о том, как делать решения Office доступными для пользователей, а также об основных аспектах, которые необходимо учитывать при выборе метода развертывания.

- [Примеры и пошаговые руководства по разработке решений Office](office-development-samples-and-walkthroughs.md)

 Ссылки на примеры приложений и разделы с пошаговыми инструкциями по выполнению типовых задач.

- [Общие справочные материалы &#40;разработке решений Office в Visual Studio&#41;](general-reference-office-development-in-visual-studio.md)

 Содержит ссылки на подробные сведения о первичных сборках взаимодействия Office, манифестах, элементах пользовательского интерфейса и сообщениях об ошибках.

- [Управляемый Справочник &#40;разработке решений Office в Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md)

 Ссылки на сведения о пространствах имен API и типах, используемые в проектах Office, который предназначены для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Справочную документацию по API о пространствах имен и типах, используемых в проектах Office, предназначенных для платформа .NET Framework 3,5, см. в следующем разделе справочника по Visual Studio 2008: [2007 Справочник по управляемым системам](managed-reference-office-development-in-visual-studio.md).

- [Справочник по неуправляемым API &#40;разработке решений Office в Visual Studio&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Ссылки на сведения об интерфейсах COM, которые можно использовать для выполнения таких действий, как загрузка и выгрузка управляемых надстроек VSTO в приложениях Office.

## <a name="related-sections"></a>Связанные разделы
- [Разработка решений Office с помощью портала разработчика Visual Studio](https://developer.microsoft.com/office/docs) Предоставляет дополнительные ресурсы, такие как технические статьи, видеоролики и блоги.

- [Центр разработчиков Visual Studio](https://visualstudio.microsoft.com/) Предоставляет дополнительные ресурсы Visual Studio, такие как технические статьи, видеоролики и блоги.

- [Раздел "разработка Microsoft Office" библиотеки MSDN](/previous-versions/office/office-12/bb726434(v=office.12)) Область библиотеки MSDN, в которой можно найти статьи и справочную документацию по разработке решений для нескольких версий Office (не только для разработки Office с помощью Visual Studio).

- [Разработка приложений в Visual Studio](/previous-versions/h8w79z10(v=vs.140)) Содержит ссылки на разделы, в которых объясняется, как можно использовать Visual Studio для проектирования, разработки, отладки и развертывания веб-приложений, веб-служб XML и традиционных клиентских приложений.

- [Платформа .NET Framework программировании в Visual Studio](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Обсуждается разработка приложений с помощью платформа .NET Framework в Visual Basic и Visual C#.
