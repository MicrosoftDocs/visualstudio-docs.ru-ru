---
title: Выполнение кода при развертывании или отзыве проекта SharePoint
titleSuffix: ''
description: Узнайте, как выполнять код при развертывании или отзыве проекта SharePoint, чтобы можно было выполнять обработку событий, создаваемых Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4645d0b2cf1670a3834c4ac09cd66d56b48fbf27
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214477"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Как выполнить код при развертывании или отзыве проекта SharePoint
  Если требуется выполнить дополнительные задачи при развертывании или отзыве проекта SharePoint, можно выполнять обработку событий, создаваемых Visual Studio. Дополнительные сведения см. в разделе [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Выполнение кода при развертывании или отзыве проекта SharePoint

1. Создайте расширение элемента проекта, расширение проекта или определение нового типа элемента проекта. Дополнительные сведения см. в следующих разделах:

   - [Как создать расширение элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Как создать расширение проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Как определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. В расширении получите доступ к <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекту. Дополнительные сведения см. [в разделе как получить службу проекта SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Обрабатывает <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> события и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> службы проекта.

4. В обработчиках событий используйте <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> параметр для получения сведений о текущем сеансе развертывания. Например, можно определить, какой проект находится в текущем сеансе развертывания, а также определить, выполняется ли его развертывание или отзыв.

   В следующем примере кода показано, как выполнять обработку <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> событий и в расширении проекта. Это расширение записывает дополнительное сообщение в окно **вывода** при запуске и завершении развертывания для проекта SharePoint.

   :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs" id="Snippet12":::
   :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Инструкции. выполнение кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
