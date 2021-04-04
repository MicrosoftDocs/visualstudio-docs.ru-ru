---
title: Расширение узла подключений SharePoint в обозреватель сервера | Документация Майкрософт
titleSuffix: ''
description: Расширьте узел подключения SharePoint в окне обозреватель сервера в Visual Studio. Добавление пользовательских свойств в узлы. Получение данных для встроенных узлов.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1f77e0044b8ae3c7456a31bb9c9153ba9e9f4c99
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218039"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Расширение узла подключений SharePoint в обозревателе сервера
  В Visual Studio можно подключаться к локальным сайтам SharePoint на компьютере разработчика с помощью узла " **подключения SharePoint** " в окне **Обозреватель сервера** . Этот узел отображает многие компоненты локальных сайтов SharePoint в иерархическом древовидном представлении. Например, можно просматривать списки, библиотеки документов и типы содержимого на локальных сайтах. Дополнительные сведения об использовании **Обозреватель сервера** для подключения к локальным сайтам SharePoint см. в разделе [Просмотр подключений sharepoint с помощью обозреватель сервера](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 Узел **подключения SharePoint** можно расширить, создав расширения для существующих узлов или создав пользовательский тип узла и добавив его в иерархию узлов.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Задачи по расширению узла подключений SharePoint
 Чтобы расширить существующий узел, создайте расширение Visual Studio, которое реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> интерфейс. При расширении узла можно добавить в него функциональные возможности, такие как собственные элементы контекстного меню или пользовательские свойства. Дополнительные сведения см. [в разделе руководство. расширение узла SharePoint в обозреватель сервера](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 Чтобы создать пользовательский тип узла, создайте расширение Visual Studio, которое реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> интерфейс. Создайте пользовательский узел, если требуется отображать компоненты сайтов SharePoint, которые не отображаются в **Обозреватель сервера** по умолчанию. Например, по умолчанию **Обозреватель сервера** не отображает галерею веб-частей сайта SharePoint, но можно добавить настраиваемый узел, который это делает. Дополнительные сведения см. в разделе [Практическое руководство. Добавление пользовательского узла SharePoint к обозреватель сервера](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) и [Пошаговое руководство. расширение обозреватель сервера для отображения веб-части](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Добавление пользовательских свойств в узлы
 При расширении узла или создании пользовательского типа узла можно добавить пользовательские свойства в узел. Свойства отображаются в окне **Свойства** при выборе узла.

 Существует два типа пользовательских свойств, которые можно добавить в узел:

- Свойства, отображающие набор данных, которые доступны только для чтения с сайта SharePoint. Данные описывают компонент SharePoint, представленный этим узлом. Пошаговое руководство, в котором показано, как это сделать, см. в разделе [Пошаговое руководство. расширение обозреватель сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Свойства, отображающие пользовательские данные для чтения и записи. Пример кода, демонстрирующий выполнение этого действия, см. в разделе [как расширить узел SharePoint в обозреватель сервера](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Получение данных для встроенных узлов
 Все встроенные узлы, предоставляемые Visual Studio, включают некоторые данные о компоненте SharePoint, которые они представляют. Например, узел, представляющий список на сайте SharePoint, предоставляет некоторые данные о списке, такие как заголовок и URL-адрес представления по умолчанию для списка.

 Чтобы получить доступ к этим данным, извлеките объект данных из <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> объекта, представляющего интересующий вас узел. Тип объекта данных зависит от типа узла.

 В следующем примере кода показано, как получить объект данных для узла списка. Чтобы увидеть этот пример в контексте более крупного примера, см. раздел [как получить данные для встроенного узла SharePoint в обозреватель сервера](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet11":::

 В следующей таблице перечислены типы объектов данных для каждого встроенного типа узла.

|Тип узла|Тип объекта данных|
|---------------|----------------------|
|Узел сайта SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|Тип содержимого|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Функция|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Поле|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|Список|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Шаблон списка|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Представление списка (Microsoft. SharePoint. View)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|Сопоставление рабочего процесса|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|Шаблон рабочего процесса|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства см. в разделе [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. расширение обозреватель сервера для показа веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Руководство. расширение узла SharePoint в обозреватель сервера](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Как добавить пользовательский узел SharePoint к обозреватель сервера](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Пошаговое руководство. получение данных для встроенного узла SharePoint в обозреватель сервера](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Просмотр подключений SharePoint с помощью обозревателя сервера](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Расширение средств SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
