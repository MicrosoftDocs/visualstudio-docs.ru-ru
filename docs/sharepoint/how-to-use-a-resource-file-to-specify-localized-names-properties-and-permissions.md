---
title: Использование файла ресурсов в проекте SharePoint | Документация Майкрософт
titleSuffix: ''
description: Используйте файл ресурсов в проекте SharePoint, чтобы можно было указать локализованные имена, определить свойства и применить разрешения для объектов, определенных в модели BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 49546d11dbf4f19bb2fd826ace2850468f780d13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851560"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Использование файла ресурсов в проекте SharePoint

  С помощью файла ресурсов можно предоставлять локализованные имена, определять свойства и применять разрешения к объектам, определенным в модели подключения к бизнес-данным (BDC). Чтобы указать эти сведения, добавьте элемент **ресурса подключения к бизнес-данным** в проект, содержащий элемент **модели подключения к бизнес-данным** . Затем задайте имена, свойства и разрешения, редактируя XML-код для файла ресурсов.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Добавление файла ресурсов BDC в проект SharePoint

1. В **Обозреватель решений** разверните папку для проекта SharePoint, а затем выберите папку, СОДЕРЖАЩУЮ модель BDC.

2. В строке меню выберите **Проект** > **Добавить новый элемент**.

3. Разверните узел **SharePoint** , а затем выберите узел **2010** .

4. В диалоговом окне **Добавление нового элемента** выберите **элемент ресурса подключения к бизнес-данным**.

5. В поле **имя** укажите имя файла ресурсов, а затем нажмите кнопку **Добавить** .

     Файл ресурсов с расширением .bdcr добавляется в проект и открывается для редактирования.

6. Добавьте XML-код, чтобы определить локализованные имена, свойства и разрешения, которые необходимо применить к модели подключения к бизнес-данным.

     Дополнительные сведения об определении этих элементов см. в разделе [модель и файлы ресурсов](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14)).

## <a name="see-also"></a>См. также раздел
- [Практическое руководство. Добавление существующего файла модели подключения к бизнес-данным в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Практическое руководство. Создание модели подключения к бизнес-данным](../sharepoint/how-to-create-a-bdc-model.md)
- [Как включить пользовательскую сборку в компонент BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
