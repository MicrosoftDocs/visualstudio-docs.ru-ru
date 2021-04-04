---
title: Сохранение данных в расширениях системы проектов SharePoint | Документация Майкрософт
titleSuffix: ''
description: Узнайте, как сохранить строковые данные, которые сохраняются после закрытия проекта SharePoint, содержащего расширение.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 87e05ba763095a818cc5db6f92828e6259d30e73
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217441"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Сохранение данных в расширениях системы проектов SharePoint
  При расширении системы проектов SharePoint можно сохранить строковые данные, которые сохраняются после закрытия проекта SharePoint. Данные обычно связаны с определенным элементом проекта или с самим проектом.

 Если имеются данные, которые не нужно сохранять, можно добавить данные в любой объект в объектной модели инструментов SharePoint, реализующей <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> интерфейс. Дополнительные сведения см. в разделе [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Сохранение данных, связанных с элементом проекта
 При наличии данных, связанных с определенным элементом проекта SharePoint, например со значением свойства, добавляемого в элемент проекта, можно сохранить данные в файл *. данных* для элемента проекта. Для этого используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> объекта. Данные, добавляемые в это свойство, сохраняются в элементе **ExtensionData** в файле *данных.* DataItem для элемента проекта. Дополнительные сведения см. в разделе [элемент ExtensionData](../sharepoint/extensiondata-element.md).

 В следующем примере кода показано, как использовать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> свойство для сохранения значения строкового свойства, определенного в пользовательском типе элемента проекта SharePoint. Чтобы увидеть этот пример в контексте более крупного примера, см. раздел [как добавить свойство в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet14":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet14":::

## <a name="save-data-that-is-associated-with-a-project"></a>Сохранение данных, связанных с проектом
 При наличии данных на уровне проекта, например значения свойства, добавляемого в проекты SharePoint, данные можно сохранить в файл проекта (файл *. csproj* или *. vbproj* ) или в файл пользовательских параметров проекта (файл *csproj. User* или *. vbproj. User* ). Файл, выбранный для сохранения данных, зависит от того, как вы хотите использовать данные:

- Если требуется, чтобы данные были доступны всем разработчикам, которые открывают проект SharePoint, сохраните данные в файл проекта. Этот файл всегда возвращается в базу данных системы управления версиями, поэтому данные в этом файле доступны другим разработчикам, которые извлеки проект.

- Если требуется, чтобы данные были доступны только текущему разработчику, который открыл проект SharePoint в Visual Studio, сохраните данные в файл параметров пользователя проекта. Этот файл обычно не возвращается в базу данных системы управления версиями, поэтому данные в этом файле недоступны другим разработчикам, которые извлеки проект.

### <a name="save-data-to-the-project-file"></a>Сохранение данных в файле проекта
 Чтобы сохранить данные в файл проекта, преобразуйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объект в <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> объект, а затем используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> метод. В следующем примере кода показано, как использовать этот метод, чтобы сохранить значение свойства проекта в файле проекта. Чтобы увидеть этот пример в контексте более крупного примера, см. раздел [как добавить свойство в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet3":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet3":::

 Дополнительные сведения о преобразовании <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объектов в другие типы в объектной модели автоматизации Visual Studio или объектной модели интеграции см. в разделе [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Сохранение данных в файле пользовательских параметров проекта
 Чтобы сохранить данные в файле пользовательских параметров проекта, используйте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объекта. В следующем примере кода показано, как использовать это свойство для сохранения значения свойства проекта в файле пользовательских параметров проекта. Чтобы увидеть этот пример в контексте более крупного примера, см. раздел [как добавить свойство в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet2":::

## <a name="see-also"></a>См. также раздел
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Связывание пользовательских данных с помощью расширений инструментов SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
