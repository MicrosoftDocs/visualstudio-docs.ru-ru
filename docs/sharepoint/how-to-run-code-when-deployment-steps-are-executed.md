---
title: Инструкции. выполнение кода при выполнении шагов развертывания | Документация Майкрософт
description: Выполнение кода для управления событиями, которые вызываются элементами проекта SharePoint до и после выполнения шага развертывания Visual Studio.
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
ms.openlocfilehash: 74db1b73dded52ba15ea860873c49c0264f7fea7
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214412"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Инструкции. выполнение кода при выполнении шагов развертывания
  Если требуется выполнить дополнительные задачи для шага развертывания в проекте SharePoint, можно обработать события, вызываемые элементами проекта SharePoint до и после того, как Visual Studio выполнит каждый шаг развертывания. Дополнительные сведения см. в разделе [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-deployment-steps-are-executed"></a>Выполнение кода при выполнении шагов развертывания

1. Создайте расширение элемента проекта, расширение проекта или определение нового типа элемента проекта. Дополнительные сведения см. в следующих разделах:

    - [Как создать расширение элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Как создать расширение проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Как определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. В расширении обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> события и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> объекта (в расширении элемента проекта или расширении проекта) или <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> в объекте (в определении нового типа элемента проекта).

3. В обработчиках событий используйте <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> Параметры и для получения сведений о шаге развертывания. Например, можно определить, какой шаг развертывания выполняется, а также как развертывать или отзывать решение.

## <a name="example"></a>Пример
 В следующем примере кода показано, как управлять <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> событиями и в расширении для элемента проекта экземпляра списка. Это расширение записывает дополнительное сообщение в окно **вывода** , когда Visual Studio перезапускает пул приложений при развертывании и отзыве решения.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb" id="Snippet4":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs" id="Snippet4":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Пошаговое руководство. Создание настраиваемого шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Как выполнить код при развертывании или отзыве проекта SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
