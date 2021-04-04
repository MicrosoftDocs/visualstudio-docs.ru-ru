---
title: Как добавить пользовательский узел SharePoint к обозреватель сервера | Документация Майкрософт
titleSuffix: ''
description: Добавьте пользовательский узел SharePoint для обозреватель сервера в Visual Studio. Отображение дополнительных компонентов SharePoint, которые не отображаются в обозреватель сервера по умолчанию.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e7c0a13879850bbd31112ddcb3193d027abeb5d1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216362"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Как добавить пользовательский узел SharePoint к обозреватель сервера
  В **Обозреватель сервера** можно добавить пользовательские узлы в узле " **подключения SharePoint** ". Это полезно, если требуется отобразить дополнительные компоненты SharePoint, которые не отображаются в **Обозреватель сервера** по умолчанию. Дополнительные сведения см. в разделе [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Чтобы добавить пользовательский узел, сначала создайте класс, определяющий новый узел. Затем создайте расширение, добавляющее узел в качестве дочернего узла для существующего узла.

### <a name="to-define-the-new-node"></a>Определение нового узла

1. Создайте проект библиотеки классов.

2. Добавьте ссылки на следующие сборки:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System.ComponentModel.Composition

    - System.Drawing;

3. Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.

4. Добавьте в класс следующие атрибуты:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Этот атрибут позволяет Visual Studio обнаруживать и загружать <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> реализацию. Передайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> тип в конструктор атрибута.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. В определении узла этот атрибут указывает идентификатор строки для нового узла. Рекомендуется использовать формат *названия компании*. *имя узла* , чтобы убедиться, что все узлы имеют уникальный идентификатор.

5. В реализации <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> метода используйте члены параметра *типедефинитион* для настройки поведения нового узла. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> объектом, предоставляющим доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> интерфейсе.

     В следующем примере кода показано, как определить новый узел. В этом примере предполагается, что проект содержит значок с именем Кустомчилднодеикон в качестве внедренного ресурса.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet6":::

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Добавление нового узла в качестве дочернего для существующего узла

1. В том же проекте, что и определение узла, создайте класс, реализующий <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> интерфейс.

2. Добавьте к классу атрибут <xref:System.ComponentModel.Composition.ExportAttribute> . Этот атрибут позволяет Visual Studio обнаруживать и загружать <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> реализацию. Передайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> тип в конструктор атрибута.

3. Добавьте к классу атрибут <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> . В расширении узла этот атрибут указывает идентификатор строки для типа узла, который требуется расширить.

     Чтобы указать встроенные типы узлов, предоставляемые Visual Studio, передайте в конструктор атрибутов одно из следующих значений перечисления:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Используйте эти значения, чтобы указать узлы подключения к сайту (узлы, отображающие URL-адреса сайтов), узлы сайта или все другие родительские узлы в **Обозреватель сервера**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Используйте эти значения, чтобы указать один из встроенных узлов, представляющих отдельный компонент на сайте SharePoint, например узел, представляющий список, поле или тип содержимого.

4. В реализации <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> метода обработайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> событие <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> параметра.

5. В <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> обработчике событий добавьте новый узел в коллекцию дочерних узлов <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> объекта, предоставляемого параметром аргументы события.

     В следующем примере кода показано, как добавить новый узел в качестве дочернего узла узла сайта SharePoint в **Обозреватель сервера**.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet7":::

## <a name="complete-example"></a>Полный пример
 В следующем примере кода приведен полный код для определения простого узла и добавления его в качестве дочернего узла узла сайта SharePoint в **Обозреватель сервера**.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet5":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet5":::

## <a name="compiling-the-code"></a>Компиляция кода
 В этом примере предполагается, что проект содержит значок с именем Кустомчилднодеикон в качестве внедренного ресурса. Для этого примера также требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

- System.Drawing;

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение **Обозреватель сервера** , создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Расширение узла подключений SharePoint в обозревателе сервера](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Руководство. расширение узла SharePoint в обозреватель сервера](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Пошаговое руководство. расширение обозреватель сервера для показа веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
