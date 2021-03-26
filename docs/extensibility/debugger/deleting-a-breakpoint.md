---
title: Удаление точки останова | Документация Майкрософт
description: Узнайте, как диспетчер отладки сеансов удаляет отложенную точку останова и все привязанные точки останова, привязанные к ней при удалении ожидающей точки останова.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1d8e0d68f32ece7760805c05fd281b0e62a70003
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097283"
---
# <a name="deleting-a-breakpoint"></a>Удаление точки останова
Ниже описан процесс удаления ожидающей точки останова.

## <a name="deletion-process"></a>Процесс удаления
 Диспетчер отладки сеансов (SDM) вызывает метод [IDebugPendingBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) для удаления ожидающей точки останова и всех привязанных к ним точек останова.

> [!NOTE]
> Можно также удалить одну привязанную точку останова с помощью вызова [IDebugBoundBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>См. также
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
