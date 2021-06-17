---
title: Как создать модель BDC | Документация Майкрософт
description: Создайте модель подключения к бизнес-данным с помощью шаблона Visual Studio для этого типа элемента, а затем добавьте модель в любой проект SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd5184f87cf3895e1519a91e6f7e6661702f1181
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112409"
---
# <a name="how-to-create-a-bdc-model"></a>Практическое руководство. Создание модели подключения к бизнес-данным

  Вы можете создать модель подключения к бизнес-данным, используя шаблон для этого типа элементов, а затем добавив модель в любой проект SharePoint. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md). Дополнительные сведения о проектировании модели см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="to-create-a-bdc-project"></a>Создание проекта BDC

1. В строке меню выберите **Файл** > **Создать** > **Проект**.
::: moniker range="=vs-2017"
   > [!NOTE]
   > Если в интегрированной среде разработки настроено использование параметров Visual Basic разработки, выберите **файл**  >  **создать проект**.

  Откроется диалоговое окно **Новый проект** .

2. В **Visual Basic** или **Visual C#** выберите **Office/SharePoint**, **решения SharePoint**.

3. В области **шаблоны** выберите **SharePoint 2013 — пустой элемент проекта** , а затем нажмите кнопку **ОК** .

     Откроется **Мастер настройки SharePoint** .
::: moniker-end
::: moniker range=">=vs-2019"
2. В диалоговом окне **Создание нового проекта** выберите *пустой проект SharePoint** для определенной версии SharePoint, которую вы установили. Например, если установлен SharePoint 2019, выберите шаблон **проекта sharepoint 2019-Empty** .
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Измените имя проекта, если хотите, а затем нажмите кнопку **создать** .

::: moniker-end
4. На странице **Укажите сайт и уровень безопасности для отладки** укажите URL-адрес сайта SharePoint на локальном компьютере, выберите параметр **Развернуть как решение фермы** , а затем нажмите кнопку **Готово** .

     Вы проверите модель на указанном сайте SharePoint.

    > [!IMPORTANT]
    > Необходимо развернуть проект как решение фермы, так как модели BDC поддерживают только решения фермы.

     Создается пустой проект SharePoint.

5. В строке меню выберите **Проект** > **Добавить новый элемент**.

6. В диалоговом окне **Добавление нового элемента** выберите узел **Office/SharePoint** .

7. В списке шаблонов SharePoint выберите **модель подключения к бизнес-данным (только для решения фермы)**.

8. В поле **имя** укажите имя модели BDC, а затем нажмите кнопку **Добавить** .

     В проект добавляется элемент **модели подключения к бизнес-данным** . По умолчанию модель отображается в конструкторе BDC. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>См. также раздел

- [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Практическое руководство. Добавление существующего файла модели подключения к бизнес-данным в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Как включить пользовательскую сборку в компонент BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
