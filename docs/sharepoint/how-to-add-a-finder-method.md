---
title: Как добавить метод Finder | Документация Майкрософт
description: Добавление метода поиска в Visual Studio, который позволяет службе подключения к бизнес-данным (BDC) отображать список сущностей в веб-части или списке SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6bd75c94e2f0f557b85d945d141f952950abb2eb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216349"
---
# <a name="how-to-add-a-finder-method"></a>Как добавить метод Finder
  Чтобы служба подключения к бизнес-данным (BDC) отображала список сущностей в веб-части или списке, необходимо создать метод *поиска* . Метод поиска — это специальный метод, который возвращает коллекцию экземпляров сущности. Дополнительные сведения см. [в разделе Разработка модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Создание метода Finder

1. В **конструкторе BDC** выберите сущность.

    Дополнительные сведения см. [в разделе инструкции. Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. В строке меню выберите **Просмотреть**  >  **другие**  >  **сведения о методе BDC** Windows.

    Откроется окно **сведения о методе BDC** . Дополнительные сведения о окне **сведения о методе BDC** см. в разделе Общие сведения о [средствах проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В списке **Добавить метод** выберите **создать метод поиска**.

    Visual Studio добавляет метод, возвращаемый параметр и дескриптор типа.

4. Настройте дескриптор типа в качестве дескриптора типа коллекции сущностей. Дополнительные сведения о создании дескриптора типа коллекции сущностей см. в разделе [инструкции. определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Вам не нужно выполнять этот шаг, если вы добавили в сущность конкретный метод поиска. Visual Studio использует дескриптор типа, определенный в конкретном методе поиска.

5. В **Обозреватель решений** откройте контекстное меню файла кода службы, созданного для сущности, и выберите пункт **Просмотреть код**. Дополнительные сведения о файле кода службы см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Добавьте код в метод Finder. Этот код выполняет следующие задачи:

   - Извлекает данные из источника данных.

   - Возвращает список сущностей для службы BDC.

     В следующем примере возвращается коллекция `Contact` сущностей с использованием данных из образца базы данных AdventureWorks для SQL Server.

   > [!NOTE]
   > Замените значение `ServerName` поля именем сервера.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet2":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet2":::

## <a name="see-also"></a>См. также раздел
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить метод Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить экземпляр метода](../sharepoint/how-to-define-a-method-instance.md)
