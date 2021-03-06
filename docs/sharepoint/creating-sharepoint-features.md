---
title: Создание компонентов SharePoint | Документация Майкрософт
description: Создайте компонент SharePoint для группировки связанных элементов проектов SharePoint для упрощения развертывания. Добавление компонентов в решение SharePoint. Используйте конструктор компонентов.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fc572f6fc5c0444fda619af5af49c6c2e52ac5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949120"
---
# <a name="create-sharepoint-features"></a>Создание компонентов SharePoint
  Для упрощения развертывания можно сгруппировать связанные элементы проекта SharePoint с помощью функции SharePoint. Можно создавать компоненты, задавать области и помечать другие функции как зависимости с помощью конструктора компонентов SharePoint. Конструктор также создает манифест, который представляет собой XML-файл с описанием каждого компонента.

## <a name="add-features-to-the-sharepoint-solution"></a>Добавление компонентов в решение SharePoint
 Компонент можно добавить в решение SharePoint с помощью обозреватель решений или обозревателя пакетов. Для добавления функции можно использовать один из следующих методов.

- В **Обозреватель решений** откройте контекстное меню **компонентов** и выберите пункт **Добавить компонент**.

- В **обозревателе пакетов** откройте контекстное меню пакета и выберите пункт **Добавить компонент**.

## <a name="using-the-feature-designer"></a>Использование конструктора компонентов
 Решение SharePoint может содержать одну или несколько функций SharePoint, которые группируются в узле "компонент" в обозреватель решений. У каждого компонента есть собственный **конструктор компонентов** , который можно использовать для настройки свойств компонента. Дополнительные сведения см. в разделе [Практическое руководство. Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Чтобы отличить компоненты друг от друга, можно настроить такие свойства компонентов, как заголовок, описание, версия и область.

### <a name="feature-designer-options"></a>Параметры конструктора компонентов
 После создания функции можно настроить ее с помощью конструктора компонентов.

 В следующей таблице описаны свойства компонентов, которые отображаются в конструкторе компонентов.

|Свойство|Описание|
|--------------|-----------------|
|Название|Необязательный элемент. Заголовок компонента по умолчанию имеет значение *имя_решения* *FeatureName*.|
|Описание|Необязательный элемент. Описание компонента SharePoint.|
|Область|Обязательный элемент. Если компонент создается с помощью **Обозреватель решений**, по умолчанию для области задано значение Web.<br /><br /> -Ферма: Активация компонента для всей фермы серверов.<br /><br /> -Site: Активация компонента для всех веб-сайтов в семействе веб-сайтов.<br /><br /> -Web: Активация компонента для конкретного веб-сайта.<br /><br /> — Веб-приложение. активируйте компонент для всех веб-сайтов в приложении.|
|Элементы в решении|Все элементы SharePoint, которые могут быть добавлены к компоненту.|
|Элементы в компоненте|Элементы проекта SharePoint, добавленные в компонент.|

## <a name="add-and-remove-sharepoint-project-items"></a>Добавление и удаление элементов проектов SharePoint
 Вы можете выбрать элементы проекта SharePoint, в которые требуется добавить компонент SharePoint для развертывания. Используйте **конструктор компонентов** для добавления и удаления элементов в компонентах и просмотра манифеста компонентов. Дополнительные сведения см. [в разделе инструкции. Добавление и удаление элементов в функциях SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Добавить зависимости компонентов
 Манифест компонента можно настроить таким образом, чтобы сервер SharePoint активировал определенные функции перед активацией компонента. Например, если функция SharePoint зависит от других функций для функциональности или данных, сервер SharePoint может сначала попытаться активировать любую из функций, от которых зависит компонент. Дополнительные сведения см. [в разделе инструкции. Добавление и удаление зависимостей компонентов](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>См. также раздел
- [Руководство. Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Как добавлять и удалять элементы в функциях SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Как добавлять и удалять зависимости компонентов](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
