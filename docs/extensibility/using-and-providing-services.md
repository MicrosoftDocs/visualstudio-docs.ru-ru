---
title: Использование и предоставление служб | Документация Майкрософт
description: Узнайте о службах, которые интегрированная среда разработки Visual Studio предлагает пакету VSPackage для предоставления и использования. В этих статьях описывается, как получить и предоставить службы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3f5e99b946514ebd3064441e9d2265be31e968a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060202"
---
# <a name="using-and-providing-services"></a>Использование и предоставление служб
Служба — это контракт между двумя пакетами VSPackage. Один пакет VSPackage предлагает конкретный набор интерфейсов для использования другим пакетом VSPackage. Например, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службу для любого пакета VSPackage, который она загружает. Эта служба предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который можно использовать для записи в журнал действий. Дополнительные сведения см. в разделе [инструкции. Использование журнала действий](../extensibility/how-to-use-the-activity-log.md).

 Пакеты VSPackage могут предоставлять собственные службы с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> интерфейса.

 Visual Studio предлагает следующие важные службы:

|Служба IDE|Описание|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Предоставляет доступ к службам IDE, которые работают с базовой функциональностью, пакеты VSPackage и реестр.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет основные функциональные возможности для работы с окнами и интерфейсом пользователя в интегрированной среде разработки, например возможность создания средств и окон документов.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Предоставляет базовые функции, связанные с решениями, такие как возможность перечисления проектов, создания новых проектов и наблюдения за изменениями проекта.|

## <a name="in-this-section"></a>в этом разделе
- [Основные компоненты службы](../extensibility/internals/service-essentials.md) Представляет важные элементы службы Visual Studio.

- [Руководство. Получение службы](../extensibility/how-to-get-a-service.md) Описывает, как запросить (использовать) службу.

- [Руководство. предоставление службы](../extensibility/how-to-provide-a-service.md) Описывает, как предоставить службу.

- [Как предоставить асинхронную службу Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Описывает, как предоставить асинхронную службу.

- [Руководство. Устранение неполадок служб](../extensibility/how-to-troubleshoot-services.md) Обсуждаются распространенные проблемы и предоставляются их решения.

## <a name="related-sections"></a>Связанные разделы
- [SDK для Visual Studio](../extensibility/visual-studio-sdk.md)
