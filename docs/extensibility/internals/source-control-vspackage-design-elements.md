---
title: Элементы проектирования VSPackage в системе управления версиями | Документация Майкрософт
description: Сведения о структуре, которую должен реализовать пакет VSPackage системы управления версиями, а также интерфейсы и службы, которые может реализовать пакет VSPackage системы управления версиями.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e3e8d70d721e77e0ed7b93dda3be5defdbf7dd9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064080"
---
# <a name="source-control-vspackage-design-elements"></a>Элементы проектирования пакета VSPackage системы управления версиями
В подразделах этого раздела описывается структура, которую должен реализовать пакет VSPackage системы управления версиями для глубокой интеграции. В нем также перечислены интерфейсы и службы, которые может реализовать пакет VSPackage системы управления версиями, а также интерфейсы и службы, которые пакет VSPackage может использовать из других [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компонентов для поддержки модели и функциональности системы управления версиями.

## <a name="in-this-section"></a>в этом разделе
- [Структура VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Определяет структуру пакета VSPackage системы управления версиями.

- [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Содержит список интерфейсов и служб, связанных с пакетом управления версиями.

- [Предоставленные службы](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Описывает службу управления версиями, предоставляемую пакетом VSPackage системы управления версиями.

## <a name="related-sections"></a>Связанные разделы
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Описывает, как создать пакет VSPackage системы управления версиями, который не только обеспечивает функциональность управления версиями, но и может использоваться для настройки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса системы управления версиями.
