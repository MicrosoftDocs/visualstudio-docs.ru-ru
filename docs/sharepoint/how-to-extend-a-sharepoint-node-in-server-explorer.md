---
title: Руководство. расширение узла SharePoint в обозреватель сервера | Документация Майкрософт
description: Сведения о том, как расширить узел SharePoint в обозреватель сервера с помощью узла "подключения SharePoint".
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e38f1d18736c18f5273eb2e202de52af81e73f85
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217454"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Руководство. расширение узла SharePoint в обозреватель сервера
  Вы можете расширить узлы в узле " **подключения SharePoint** " в **Обозреватель сервера**. Это полезно, если требуется добавить в существующий узел новые дочерние узлы, элементы контекстного меню или свойства. Дополнительные сведения см. в разделе [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Расширение узла SharePoint в обозреватель сервера

1. Создайте проект библиотеки классов.

2. Добавьте ссылки на следующие сборки:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System.ComponentModel.Composition

3. Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.

4. Добавьте к классу атрибут <xref:System.ComponentModel.Composition.ExportAttribute> . Этот атрибут позволяет Visual Studio обнаруживать и загружать <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> реализацию. Передайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> тип в конструктор атрибута.

5. Добавьте к классу атрибут <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> . Этот атрибут задает идентификатор строки для типа узла, который требуется расширить.

     Чтобы указать встроенные типы узлов, предоставляемые Visual Studio, передайте в конструктор атрибутов одно из следующих значений перечисления:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Используйте эти значения, чтобы указать узлы подключения к сайту (узлы, отображающие URL-адреса сайтов), узлы сайта или все другие родительские узлы в **Обозреватель сервера**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Используйте эти значения, чтобы указать один из встроенных узлов, представляющих отдельный компонент на сайте SharePoint, например узел, представляющий список, поле или тип содержимого.

6. В реализации <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> метода используйте члены параметра *NodeType* для добавления компонентов к узлу. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> объектом, предоставляющим доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> интерфейсе. Например, можно выполнять следующие события:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Обрабатывает это событие, чтобы добавить в узел новые дочерние узлы. Дополнительные сведения см. в разделе [как добавить пользовательский узел SharePoint к обозреватель сервера](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Обрабатывает это событие, чтобы добавить настраиваемый элемент контекстного меню в узел.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Обрабатывает это событие, чтобы добавить пользовательские свойства в узел. Свойства отображаются в окне **Свойства** при выборе узла.

## <a name="example"></a>Пример
 В следующем примере кода показано, как создать два различных типа расширений узлов:

- Расширение, добавляющее пункт контекстного меню к узлам сайта SharePoint. При щелчке пункта меню отображается имя узла, который был выбран.

- Расширение, добавляющее пользовательское свойство с именем **контосоексамплепроперти** к каждому узлу, представляющему поле с именем **Body**.

  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs" id="Snippet9":::
  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb" id="Snippet9":::

  Это расширение добавляет редактируемое строковое свойство к узлам. Можно также создавать пользовательские свойства, отображающие данные только для чтения с сервера SharePoint. Пример, демонстрирующий это, см. в разделе [Пошаговое руководство. расширение обозреватель сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System.ComponentModel.Composition

- System.Windows.Forms.

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение **Обозреватель сервера** , создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Как добавить пользовательский узел SharePoint к обозреватель сервера](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Расширение узла подключений SharePoint в обозревателе сервера](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Пошаговое руководство. расширение обозреватель сервера для показа веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
