---
title: Добавить пункт контекстного меню в пользовательский тип элемента проекта SharePoint
titleSuffix: ''
description: Сведения о добавлении пункта контекстного меню в пользовательский тип элемента проекта SharePoint. Пункт меню появляется при щелчке правой кнопкой мыши элемента проекта в обозреватель решений.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3e4523d0f992ed72c9af2eb7e542f902578f9338
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215387"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Как добавить пункт контекстного меню в пользовательский тип элемента проекта SharePoint
  При определении пользовательского типа элемента проекта SharePoint можно добавить пункт контекстного меню в элемент проекта. Этот пункт меню появляется, когда пользователь щелкает правой кнопкой мыши элемент проекта в **Обозреватель решений**.

 В следующих шагах предполагается, что вы уже определили собственный тип элемента проекта SharePoint. Дополнительные сведения см. [в разделе инструкции. определение типа элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Добавление пункта контекстного меню в пользовательский тип элемента проекта

1. В <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> методе <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> реализации обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> событие параметра *прожектитемтипедефинитион* .

2. В обработчике событий для <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> события добавьте новый <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объект в <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> коллекцию или параметра аргументов события.

3. В <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> обработчике событий для нового <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> объекта выполните задачи, которые необходимо выполнить, когда пользователь выберет нужный пункт контекстного меню.

## <a name="example"></a>Пример
 В следующем примере кода показано, как добавить элемент контекстного меню в пользовательский тип элемента проекта. Когда пользователь открывает контекстное меню из элемента проекта в **Обозреватель решений** и выбирает пункт « **запись сообщения в окно вывода** », Visual Studio отображает сообщение в окне **вывод** .

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs" id="Snippet4":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb" id="Snippet4":::

 В этом примере используется служба проекта SharePoint для записи сообщения в окно **вывода** . Дополнительные сведения см. [в статье Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуется проект библиотеки классов со ссылками на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Развертывание элемента проекта
 Чтобы позволить другим разработчикам использовать элемент проекта, создайте шаблон проекта или шаблон элемента проекта. Дополнительные сведения см. в разделе [Создание шаблонов элементов и шаблонов проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Чтобы развернуть элемент проекта, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки, шаблона и других файлов, которые необходимо распространить с элементом проекта. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Как определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Как добавить свойство в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
