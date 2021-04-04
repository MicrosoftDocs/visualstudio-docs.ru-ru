---
title: Как справиться с конфликтами развертывания | Документация Майкрософт
description: См. Пример реализации собственного кода для управления конфликтами развертывания для элемента проекта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b09db3fecde5d4b87b24963930b2783b0c68052c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213983"
---
# <a name="how-to-handle-deployment-conflicts"></a>Как справляться с конфликтами развертывания
  Можно предоставить собственный код для управления конфликтами развертывания для элемента проекта SharePoint. Например, можно определить, существуют ли уже какие-либо файлы текущего элемента проекта в расположении развертывания, а затем удалить развернутые файлы перед развертыванием текущего элемента проекта. Дополнительные сведения о конфликтах развертывания см. в разделе [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Для решения конфликта развертывания

1. Создайте расширение элемента проекта, расширение проекта или определение нового типа элемента проекта. Дополнительные сведения см. в следующих разделах:

    - [Как создать расширение элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Как создать расширение проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Как определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. В расширении обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> объекта (в расширении элемента проекта или в расширении проекта) или <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> объект (в определении нового типа элемента проекта).

3. В обработчике событий определите, существует ли конфликт между развертываемым элементом проекта и развернутым решением на сайте SharePoint на основе критериев, которые применяются к вашему сценарию. Можно использовать <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> свойство параметра аргументы события для анализа развертываемого элемента проекта, а также анализировать файлы в расположении развертывания, вызвав команду SharePoint, определенную для этой цели.

     Для многих типов конфликтов, возможно, сначала нужно определить, какой шаг развертывания выполняется. Это можно сделать с помощью <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> Свойства параметра аргументы события. Хотя обычно имеет смысл обнаружить конфликты во время встроенного <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> шага развертывания, можно проверить наличие конфликтов на этапе развертывания.

4. Если существует конфликт, используйте <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> метод <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> Свойства аргументов события для создания нового <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> объекта. Этот объект представляет конфликт развертывания. При вызове <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> метода также укажите метод, который вызывается для разрешения конфликта.

## <a name="example"></a>Пример
 В следующем примере кода показан базовый процесс обработки конфликта развертывания в расширении элемента проекта для элементов проекта определения списка. Чтобы обрабатывать конфликт развертывания для другого типа элемента проекта, передайте в объект другую строку <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Дополнительные сведения см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).

 Для простоты в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> обработчике событий в этом примере предполагается, что существует конфликт развертывания (то есть всегда добавляется новый <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> объект), а `Resolve` метод просто возвращает **значение true** , чтобы указать, что конфликт был разрешен. В реальной ситуации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> обработчик событий сначала определит, существует ли конфликт между файлом в текущем элементе проекта и файлом в расположении развертывания, а затем добавить <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> объект, только если существует конфликт. Например, можно использовать `e.ProjectItem.Files` свойство в обработчике событий для анализа файлов в элементе проекта, а для анализа файлов в расположении развертывания можно вызвать команду SharePoint. Аналогично, в реальной ситуации `Resolve` метод может вызвать команду SharePoint для разрешения конфликта на сайте SharePoint. Дополнительные сведения о создании команд SharePoint см. [в разделе инструкции. Создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Инструкции. выполнение кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Как создать команду SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
