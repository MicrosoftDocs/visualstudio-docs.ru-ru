---
title: Когда точка останова привязывается или перестанет быть несвязанной | Документация Майкрософт
description: Дополнительные сведения о несвязанных точках останова. Если точка останова не может быть привязана во время вызова, время привязки и время создания точки останова различаются.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b6e1a6acdee89be293ab4a6dc72a3d4fd4336d88
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091413"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Когда точка останова привязывается или перестанет быть несвязанной
Если точка останова не может быть привязана во время вызова метода [IDebugPendingBreakpoint2:: канбинд](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , время привязки и время создания точки останова различаются.

## <a name="methods-called"></a>Вызываемые методы
 Диспетчер отладки сеансов (SDM) вызывает следующие методы:

1. [IDebugEngine2:: креатепендингбреакпоинт](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). Метод DE возвращает [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).

2. [IDebugPendingBreakpoint2:: enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2:: виртуализировать](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. Метод [IDebugPendingBreakpoint2:: BIND](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) и возвращает S_OK. Параметр DE отправляет [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) или [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. Методы [IDebugBreakpointBoundEvent2:: жетпендингбреакпоинт](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) и [IDebugBreakpointBoundEvent2:: енумбаундбреакпоинтс](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) для проверки и получения связанных точек останова.

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
