---
title: Как добавить дескриптор фильтра в метод Finder | Документация Майкрософт
description: Узнайте, как добавить дескриптор фильтра в метод поиска с помощью окна сведения о методе BDC в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 47fcc7e388f240d8b9636a733df4b6b8767f0df4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218013"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Как добавить дескриптор фильтра в метод Finder
  Дескрипторы фильтров позволяют потребителям модели передавать значения методам перед их выполнением. Дополнительные сведения см. в разделе [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

 Один из распространенных сценариев заключается в том, что пользователи в SharePoint хотят получить экземпляры внешнего типа содержимого, соответствующие некоторым критериям. Этот сценарий можно обеспечить, добавив дескриптор фильтра в метод поиска.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Добавление дескриптора фильтра в метод Finder

1. В окне **сведения о методе BDC** разверните узел метода поиска, разверните узел **Параметры** , а затем добавьте входной параметр. Дополнительные сведения см. в разделе [инструкции. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. В окне **сведения о методе** выберите дескриптор типа параметра.

3. В строке меню выберите **вид**  >  **окно свойств**.

4. В окне **Свойства** задайте для свойства **имя типа** тип данных, подходящий для фильтра.

     Например, фильтр может использовать дату заказа для ограничения количества заказов на продажу, возвращаемых методом. Для поддержки этого фильтра свойство **имени типа** дескриптора типа должно иметь значение **System. DateTime**.

5. В окне **сведения о методе** разверните узел **дескрипторы фильтра** .

6. В списке **Добавить дескриптор фильтра** выберите **создать дескриптор фильтра**.

     Под узлом **дескрипторы фильтра** появится новый дескриптор фильтра.

7. В строке меню выберите **вид**  >  **окно свойств**.

8. В окне **Свойства** выберите свойство **тип** .

9. В списке, который отображается для свойства **тип** , выберите нужный шаблон фильтрации.

     Например, чтобы создать фильтр, использующий дату заказа для ограничения количества заказов на продажу, возвращаемых в методе поиска, выберите **Сравнение**. Фильтр сравнения гарантирует, что метод поиска возвращает только те экземпляры, которые соответствуют определенному условию. Дополнительные сведения о каждом шаблоне фильтрации см. [в разделе Типы фильтров, ПОДДЕРЖИВАЕМЫХ BDC](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

10. В окне **Свойства** выберите **связанное свойство дескрипторов типа** .

11. В списке, который отображается для **соответствующего свойства дескрипторов типа** , выберите дескриптор типа, созданный ранее в этой процедуре. Это связывает фильтр с входным параметром метода поиска.

12. Добавьте код в метод Finder, который возвращает данные. Входной параметр можно использовать в качестве условия в запросе SELECT.

     В следующем примере возвращаются заказы на продажу, которые имеют указанную дату заказа.

    > [!NOTE]
    > Замените значение `ServerName` поля именем сервера.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet11":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet11":::

## <a name="see-also"></a>См. также раздел
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить дескриптор типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
