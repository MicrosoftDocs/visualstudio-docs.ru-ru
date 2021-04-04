---
title: Связывание пользовательских данных с расширениями инструментов SharePoint | Документация Майкрософт
description: Связывание пользовательских данных с помощью расширений инструментов SharePoint. См. список объектов, которые могут содержать пользовательские данные. Добавление и извлечение пользовательских данных.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5665fc28bacb76c6887cb7dcb1820ec9dc0d2b3a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215322"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Связывание пользовательских данных с помощью расширений инструментов SharePoint
  Можно добавить пользовательские данные в определенные объекты в расширениях инструментов SharePoint. Это полезно при наличии данных в одной части расширения, доступ к которой будет осуществляться позже из другого кода расширения. Вместо реализации пользовательского способа хранения данных и доступа к ним можно связать данные с объектом в расширении, а затем извлечь данные из этого объекта позже.

 Добавление пользовательских данных в объекты также полезно, если требуется сохранить данные, относящиеся к конкретному элементу в Visual Studio. Расширения инструментов SharePoint загружаются в Visual Studio только один раз, поэтому расширение может работать с несколькими различными элементами (например, проектами, элементами проектов или **Обозреватель сервера** узлами) в любое время. Если имеются пользовательские данные, относящиеся только к определенному элементу, можно добавить данные в объект, представляющий этот элемент.

 При добавлении пользовательских данных в объекты в расширениях инструментов SharePoint данные не сохраняются. Данные доступны только в течение срока существования объекта. После освобождения объекта при сборке мусора данные теряются.

 В расширениях системы проектов SharePoint можно также сохранять строковые данные, которые сохраняются после выгрузки расширения. Дополнительные сведения см. [в разделе Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Объекты, которые могут содержать пользовательские данные
 Можно добавить пользовательские данные в любой объект в объектной модели инструментов SharePoint, реализующей <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> интерфейс. Этот интерфейс определяет только одно свойство, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> которое является коллекцией пользовательских объектов данных. Следующие типы реализуют <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>Добавление и извлечение пользовательских данных
 Чтобы добавить пользовательские данные в объект в расширении инструментов SharePoint, получите <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство объекта, в который необходимо добавить данные, а затем используйте <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> метод, чтобы добавить данные в объект.

 Чтобы получить пользовательские данные из объекта в расширении инструментов SharePoint, получите <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство объекта и используйте один из следующих методов:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Этот метод возвращает **значение true** , если объект данных существует, или **значение false** , если он не существует. Этот метод можно использовать для получения экземпляров типов значений или ссылочных типов.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Этот метод возвращает объект данных, если он завершает работу, или **значение NULL** , если он не существует. Этот метод можно использовать только для получения экземпляров ссылочных типов.

  В следующем примере кода определяется, связан ли определенный объект данных с элементом проекта. Если объект данных еще не связан с элементом проекта, код добавляет объект в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство элемента проекта. Чтобы увидеть этот пример в контексте более крупного примера, см. раздел [как добавить свойство в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet13":::
  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet13":::

## <a name="see-also"></a>См. также раздел
- [Концепции и функции программирования для расширений инструментов SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Пошаговое руководство. расширение обозреватель сервера для показа веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Как добавить свойство в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Как добавить свойство в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
