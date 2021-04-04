---
title: 'Инструкции: выполнение команды SharePoint | Документация Майкрософт'
description: Узнайте, как создать настраиваемую команду SharePoint для вызова API серверной объектной модели из расширения инструментов SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4e22ade9b2414e1d598065bb9e417c4706f75a07
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217181"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Инструкции: выполнение команды SharePoint
  Если вы хотите использовать объектную модель сервера в расширении инструментов SharePoint, необходимо создать пользовательскую *команду SharePoint* для вызова API. После определения команды и ее развертывания с помощью расширения инструментов SharePoint расширение может выполнить команду для вызова серверной объектной модели SharePoint. Чтобы выполнить команду, используйте один из методов ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта.

 Дополнительные сведения о назначении команд SharePoint см. в разделе [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Выполнение команды SharePoint

1. В расширении инструментов SharePoint получите <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объект. Способ получения <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта зависит от типа создаваемого расширения:

    - В расширении системы проектов SharePoint используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> свойство.

         Дополнительные сведения о расширениях системы проектов см. [в разделе расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

    - В расширении узла **подключения SharePoint** в **Обозреватель сервера** используйте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> свойство. Чтобы получить <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> объект, используйте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> свойство.

         Дополнительные сведения о расширениях **Обозреватель сервера** см. [в разделе Расширение узла подключений SharePoint в обозреватель сервера](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - В коде, который не является частью расширения средств SharePoint, таких как мастер шаблонов проектов, используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> свойство.

         Дополнительные сведения о получении службы проекта см. [в разделе Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

2. Вызовите один из методов ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта. Передайте имя команды, которую нужно выполнить, в первый аргумент метода ExecuteCommand. Если команда имеет пользовательский параметр, передайте этот параметр во второй аргумент метода ExecuteCommand.

     Для каждой поддерживаемой сигнатуры команды существует другая перегрузка ExecuteCommand. В следующей таблице перечислены поддерживаемые сигнатуры и перегрузка, используемая для каждой сигнатуры.

    |Сигнатура команды|Перегрузка ExecuteCommand для использования|
    |-----------------------|------------------------------------|
    |Команда имеет только параметр по умолчанию <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> и не возвращает возвращаемое значение.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Команда имеет только параметр по умолчанию <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> и возвращаемое значение.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Команда имеет два параметра (параметр по умолчанию <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> и пользовательский параметр) без возвращаемого значения.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Команда имеет два параметра и возвращаемое значение.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Пример
 В следующем примере кода показано, как использовать <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> перегрузку для вызова `Contoso.Commands.UpgradeSolution` команды, описанной в разделе [инструкции. Создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs" id="Snippet6":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb" id="Snippet6":::

 `Execute`Метод, показанный в этом примере, является реализацией <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> метода <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> интерфейса на настраиваемом шаге развертывания. Чтобы просмотреть этот код в контексте более крупного примера, см. раздел [Пошаговое руководство. Создание настраиваемого шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Обратите внимание на следующие сведения о вызове <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> метода:

- Первый параметр определяет команду, которую требуется вызвать. Эта строка соответствует значению, переданному в в <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> определении команды.

- Вторым параметром является значение, которое необходимо передать пользовательскому второму параметру команды. В этом случае это полный путь к *WSP* -файлу, который обновляется до сайта SharePoint.

- Код не передает неявный <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> параметр команде. Этот параметр передается в команду автоматически при вызове команды из расширения системы проектов SharePoint или расширения узла **подключений SharePoint** в **Обозреватель сервера**. В решениях других типов, например в мастере шаблонов проектов, который реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс, этот параметр имеет **значение NULL**.

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуется ссылка на сборку Microsoft. VisualStudio. SharePoint.

## <a name="see-also"></a>См. также раздел
- [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Как создать команду SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Пошаговое руководство. расширение обозреватель сервера для показа веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
