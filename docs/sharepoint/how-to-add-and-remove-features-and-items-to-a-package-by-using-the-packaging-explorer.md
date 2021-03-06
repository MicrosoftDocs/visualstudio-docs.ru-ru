---
title: 'Обозреватель пакетов: Добавление & удаление компонентов & элементов в пакет'
titleSuffix: ''
description: Добавление и удаление компонентов и элементов в пакете SharePoint с помощью обозревателя пакетов в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eec1468fc2e0c51d7dea7aa5f3ffa808b484ec87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923563"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Пошаговое руководство. Добавление и удаление компонентов и элементов в пакет с помощью обозревателя пакетов
  Чтобы настроить пакет для развертывания элементов и компонентов SharePoint, можно использовать обозреватель пакетов. Можно настроить элементы и компоненты проекта SharePoint в файле. wsp.

 Кроме того, можно использовать конструктор пакетов для просмотра и изменения порядка компонентов, чтобы изменить порядок активации. Дополнительные сведения см. в разделе [инструкции. Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Открытие обозревателя пакетов
 Можно использовать следующую процедуру, чтобы открыть Обозреватель пакетов, если в решении Visual Studio есть по крайней мере один проект SharePoint. Кроме того, обозреватель пакетов открывается автоматически при просмотре конструктора компонентов или пакетов. После закрытия всех конструкторов компонентов и пакетов Обозреватель пакетов также закроется.

#### <a name="to-open-the-packaging-explorer"></a>Открытие обозревателя пакетов

1. В строке меню выберите пункт **Просмотреть**  >  **другой**  >  **проводник пакетов** Windows.

     **Обозреватель пакетов** появится на **панели элементов**.

## <a name="adding-a-feature-to-a-package"></a>Добавление компонента в пакет
 В пакет можно добавлять новые и существующие компоненты с помощью обозревателя пакетов.

#### <a name="to-add-a-sharepoint-feature"></a>Добавление компонента SharePoint

1. Откройте **Обозреватель пакетов**, откройте контекстное меню проекта и выберите пункт **Добавить компонент**.

#### <a name="to-move-an-existing-sharepoint-feature"></a>Перемещение существующей функции SharePoint

1. Откройте **Обозреватель пакетов** и выполните одно из следующих действий.

    - Перетащите **компонент** из одного проекта в другой проект.

    - Откройте контекстное меню для компонента, выберите **Вырезать**, откройте контекстное меню проекта, для которого требуется переместить компонент, и выберите **Вставить**.

    > [!NOTE]
    > Эта процедура используется в случае, если в решении имеется несколько проектов SharePoint.

## <a name="validate-a-feature-or-package"></a>Проверка компонента или пакета
 Можно выявление потенциальных проблем в компонентах и пакетах SharePoint путем проверки файлов. Предупреждения и ошибки отображаются в окне вывода и список ошибок окне.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Проверка компонента или пакета SharePoint

1. Откройте **Обозреватель пакетов**.

2. Откройте контекстное меню для компонента или пакета, а затем выберите **проверить**.

## <a name="see-also"></a>См. также раздел
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
