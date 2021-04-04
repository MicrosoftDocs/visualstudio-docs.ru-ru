---
title: Как добавить конкретный метод поиска | Документация Майкрософт
description: Получите экземпляр сущности, добавив метод Finder. Служба BDC вызывает метод, когда пользователь выбирает сущность в веб-части данных или во внешнем списке.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 87f5b0cf86178b88b1611f4b0ce8a4bbacde780e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216804"
---
# <a name="how-to-add-a-specific-finder-method"></a>Как добавить конкретный метод поиска
  Можно вернуть один экземпляр сущности, создав *конкретный метод поиска* . Служба подключения к бизнес-данным (BDC) выполняет конкретный метод поиска, когда пользователь выбирает сущность в веб-части данных или во внешнем списке. Дополнительные сведения см. в разделе [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Создание конкретного метода поиска

1. В **конструкторе BDC** выберите сущность.

    Сведения о добавлении сущности в **конструктор BDC** в Visual Studio см. в разделе [как добавить сущность в модель](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. В строке меню выберите **Просмотр**  >  **других окон**, **сведения о методе BDC**.

    Откроется окно **сведения о методе BDC** . Дополнительные сведения об этом окне см. в разделе Общие сведения о [средствах проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В списке **Добавить метод** выберите **создать конкретный метод поиска**.

    Visual Studio добавляет в модель следующие элементы. Эти элементы отображаются в окне **сведения о методе BDC** .

   - Метод.

   - Входной параметр для метода.

   - Возвращаемый параметр для метода.

   - Дескриптор типа для каждого параметра.

   - Экземпляр метода для метода.

     Дополнительные сведения см. в разделе [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Откройте окно **свойств** Visual Studio.

5. Настройте дескриптор типа возвращаемого параметра в качестве дескриптора типа сущности. Сведения о создании дескриптора типа сущности см. [в разделе инструкции. определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Вам не нужно выполнять этот шаг, если вы добавили в сущность метод поиска. В Visual Studio используется дескриптор типа, определенный в методе Finder.

   > [!NOTE]
   > Если поле идентификатора типа сущности представляет поле в таблице базы данных, которое создается автоматически, задайте свойству "только для **чтения** " поля Идентификатор значение **true**.

6. В окне **сведения о методе** выберите экземпляр метода метода.

7. В **окне Свойства** задайте для свойства **имя возвращаемого параметра** имя возвращаемого параметра метода. Дополнительные сведения о свойствах экземпляра метода см. в разделе [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. В **Обозреватель решений** откройте контекстное меню файла кода службы, созданного для сущности, и выберите пункт **Просмотреть код**.

    Файл кода службы сущности откроется в редакторе кода. Дополнительные сведения о файле кода службы сущности см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Добавьте код в конкретный метод поиска. Этот код выполняет следующие задачи:

   - Извлекает запись из источника данных.

   - Возвращает сущность для службы BDC.

     В следующем примере возвращается контакт из образца базы данных AdventureWorks для SQL Server.

     > [!NOTE]
     > Замените значение `ServerName` поля именем сервера.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet3":::

## <a name="see-also"></a>См. также раздел
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить метод Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить экземпляр метода](../sharepoint/how-to-define-a-method-instance.md)
