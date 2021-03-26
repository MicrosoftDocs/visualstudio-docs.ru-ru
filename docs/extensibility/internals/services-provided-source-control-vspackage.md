---
title: Предоставляемые службы (пакет VSPackage системы управления версиями) | Документация Майкрософт
description: Узнайте, как пакеты VSPackage совместно используют функции, включая взаимодействие с интегрированной средой разработки Visual Studio и пакетами VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe1d9ee9805e6e86595f3f7f3cf640114c7030b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080818"
---
# <a name="services-provided-source-control-vspackage"></a>Предоставляемые службы (пакет VSPackage системы управления версиями)
Службы — это основной механизм, с помощью которого совместно используются пакеты VSPackage и между интегрированной средой разработки (IDE) Visual Studio и установленными пакетами VSPackage. Подробное описание служб и их важность в интегрированной среде разработки Visual Studio см. в разделе[использование и предоставление служб](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Служба системы управления версиями
 Visual Studio предоставляет два уровня служб: службы на уровне IDE и службы уровня пакета. Интегрированная среда разработки Visual Studio изначально предоставляет службы уровня IDE. Пакет системы управления версиями использует некоторые из этих служб. Пакет управления версиями в качестве пакета VSPackage использует свои функции управления версиями, предоставляя собственную собственную службу управления версиями. Пакет системы управления версиями инкапсулирует набор связанных с системой управления версиями интерфейсов, реализованных в виде контракта, который может использоваться в интегрированной среде разработки Visual Studio.

## <a name="see-also"></a>См. также
- [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)
