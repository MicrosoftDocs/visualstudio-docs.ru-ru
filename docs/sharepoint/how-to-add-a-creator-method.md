---
title: Как добавить метод Creator | Документация Майкрософт
description: Узнайте, как добавить метод Creator, который добавляет новые данные в источник данных сущности в службе подключения к бизнес-данным (BDC) в SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 950745a533fbea8d360c8bea6d839a304dd6e0d7
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216414"
---
# <a name="how-to-add-a-creator-method"></a>Как добавить метод Creator
  Метод Creator добавляет новые данные в источник данных сущности. Служба подключения к бизнес-данным (BDC) вызывает этот метод, когда пользователь наберет кнопку **создать элемент** на **ленте** списка, основанного на модели. Дополнительные сведения см. в разделе [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-add-a-creator-method"></a>Добавление метода Creator

1. В **конструкторе BDC** выберите сущность.

2. В строке меню выберите **Просмотреть**  >  **другие**  > **сведения о методе BDC** Windows.

    Откроется окно **сведения о методе BDC** . Дополнительные сведения об этом окне см. в разделе Общие сведения о [средствах проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В списке **Добавить метод** выберите **создать метод создания**.

    Visual Studio добавляет в модель следующие элементы, и эти элементы отображаются в окне **сведения о методе BDC** .

   - Метод с именем **CREATE**.

   - Входной параметр для метода.

   - Возвращаемый параметр для метода.

   - Дескрипторы типов для параметров.

   - Экземпляр метода для метода.

     Дополнительные сведения см. в разделе [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

4. В **Обозреватель решений** откройте контекстное меню файла кода службы, созданного для сущности, и выберите пункт **Просмотреть код**.

    Файл кода службы сущности откроется в редакторе кода. Дополнительные сведения о файле кода службы сущности см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Добавьте код в метод Creator, который добавляет данные в источник данных. В следующем примере к образцу базы данных AdventureWorks добавляется контакт для SQL Server.

   > [!NOTE]
   > Замените значение `ServerName` поля именем сервера.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet4":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet4":::

## <a name="see-also"></a>См. также раздел
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить экземпляр метода](../sharepoint/how-to-define-a-method-instance.md)
