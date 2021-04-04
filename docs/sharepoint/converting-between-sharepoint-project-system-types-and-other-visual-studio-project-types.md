---
title: 'Преобразовать: типы системы проектов SharePoint в другие типы и из них'
titleSuffix: ''
description: Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio. См. список типов, которые можно преобразовать.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 973c3d4b3c4fa2dc602e45736dc3a2d2f23c7616
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215296"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio
  В некоторых случаях у вас может быть объект в системе проектов SharePoint, и вы хотите использовать функции соответствующего объекта в объектной модели автоматизации Visual Studio или объектной модели интеграции, или наоборот. В таких случаях можно использовать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> метод службы проектов SharePoint для преобразования объекта в другую объектную модель.

 Например, у вас может быть <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объект, но вы хотите использовать методы, которые доступны только для <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> объекта или. В этом случае можно использовать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> метод для преобразования в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Дополнительные сведения об объектной модели автоматизации Visual Studio и объектной модели интеграции Visual Studio см. [в разделе Общие сведения о модели программирования расширений инструментов SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Типы преобразований
 В следующей таблице перечислены типы, которые этот метод может преобразовывать между системой проектов SharePoint и другими объектными моделями Visual Studio.

|Тип системы проектов SharePoint|Соответствующие типы в объектных моделях автоматизации и интеграции|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> или<br /><br /> Любой интерфейс в объектной модели интеграции Visual Studio, реализуемый базовым COM-объектом для проекта. К этим интерфейсам относятся <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (или производный интерфейс) и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Список основных интерфейсов, реализованных в проектах, см. в разделе [основные компоненты модели проекта](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> или<br /><br /> <xref:System.UInt32>Значение (также называемое вситемид), идентифицирующее элемент проекта в элементе <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , содержащем его. Это значение может быть передано параметру *ItemId* некоторых <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> методов.|

## <a name="example"></a>Пример
 В следующем примере кода показано, как использовать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> метод для преобразования <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объекта в <xref:EnvDTE.Project> .

:::code language="csharp" source="../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs" id="Snippet2":::
:::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb" id="Snippet2":::

 Для этого примера требуются:

- Расширение системы проектов SharePoint, имеющее ссылку на сборку *EnvDTE.dll* . Дополнительные сведения см. в разделе [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Код, регистрирующий `projectService_ProjectAdded` метод для управления <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> событием <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта. Пример см. в разделе [руководство. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>См. также раздел

- [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Как получить службу проекта SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Обзор модели программирования расширений инструментов SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
