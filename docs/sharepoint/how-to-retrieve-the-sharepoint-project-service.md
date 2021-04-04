---
title: Как получить службу проекта SharePoint | Документация Майкрософт
description: Узнайте, как получить доступ к службе проектов SharePoint в расширениях системы проектов, обозреватель сервера расширениях или других расширениях Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ef53a0328fe8427b356132fe878b52a3e504ea9a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214464"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Как получить службу проекта SharePoint
  Доступ к службе проектов SharePoint можно получить с помощью следующих типов решений:

- Расширение системы проектов SharePoint, например расширение проекта, расширение элемента проекта или определение типа элемента проекта. Дополнительные сведения об этих типах расширений см. в разделе [расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Расширение узла **подключений SharePoint** в **Обозреватель сервера**. Дополнительные сведения об этих типах расширений см. в разделе [расширение узла подключений SharePoint в обозреватель сервера](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- Другой тип расширения Visual Studio, например VSPackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Получение службы в расширениях системы проектов
 В любом расширении системы проектов SharePoint можно получить доступ к службе проекта с помощью <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объекта.

 Вы также можете получить службу проекта, выполнив следующие процедуры.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Получение службы в расширении проекта

1. В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейса нахождение <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метода.

2. Используйте параметр *прожектсервице* для доступа к службе.

     В следующем примере кода показано, как использовать службу проекта для записи сообщения в окно **вывода** и **Список ошибок** окно в простом расширении проекта.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     Дополнительные сведения о создании расширений проектов см. [в разделе инструкции. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Получение службы в расширении элемента проекта

1. В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> интерфейса нахождение <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метода.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A>Чтобы получить службу, используйте свойство параметра *прожектитемтипе* .

     В следующем примере кода показано, как использовать службу проекта для записи сообщения в окно **вывода** и **Список ошибок** окно в простое расширение элемента проекта **определения списка** .

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet2":::

     Дополнительные сведения о создании расширений элементов проектов см. [в разделе инструкции. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Получение службы в определении типа элемента проекта

1. В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейса нахождение <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метода.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A>Чтобы получить службу, используйте свойство параметра *типедефинитион* .

     В следующем примере кода показано, как использовать службу проекта для записи сообщения в окно **вывода** и **Список ошибок** окно в простом определении типа элемента проекта.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet3":::

     Дополнительные сведения об определении типов элементов проектов см. [в разделе инструкции. определение типа элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Получение службы в расширениях обозреватель сервера
 В расширении узла **подключения SharePoint** в **Обозреватель сервера** можно получить доступ к службе проекта с помощью <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> свойства <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> объекта.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Получение службы в обозреватель сервераном расширении

1. Получите <xref:System.IServiceProvider> объект из <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> свойства <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> объекта в расширении.

2. Используйте <xref:System.IServiceProvider.GetService%2A> метод для запроса <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта.

     В следующем примере кода показано, как использовать службу проекта для записи сообщения в окно **вывода** и **Список ошибок** окно из контекстного меню, добавляемое расширением для вывода списка узлов в **Обозреватель сервера**.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     Дополнительные сведения о расширении узла **подключений SharePoint** в **Обозреватель сервера** см. в разделе [как расширить узел SharePoint в обозреватель сервера](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Получение службы в других расширениях Visual Studio
 Службу проекта можно получить в VSPackage или в любом расширении Visual Studio, имеющем доступ к <xref:EnvDTE80.DTE2> объекту в объектной модели автоматизации, например в мастере шаблонов проектов, который реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс.

 В VSPackage объект можно запросить с <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> помощью одного из следующих методов:

- <xref:System.IServiceProvider.GetService%2A>Метод управляемого пакета VSPackage, производного от <xref:Microsoft.VisualStudio.Shell.Package> класса. Дополнительные сведения см. [в разделе руководство. Получение службы](../extensibility/how-to-get-a-service.md).

- Статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод. Дополнительные сведения см. в разделе [use GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  В расширении Visual Studio, имеющем доступ к <xref:EnvDTE80.DTE2> объекту, можно запросить <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объект с помощью <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> метода <xref:Microsoft.VisualStudio.Shell.ServiceProvider> объекта. Дополнительные сведения см. в разделе [Получение службы из объекта DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>См. также раздел
- [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Руководство. Получение службы](../extensibility/how-to-get-a-service.md)
- [Руководство. Использование мастеров с шаблонами проектов](../extensibility/how-to-use-wizards-with-project-templates.md)
