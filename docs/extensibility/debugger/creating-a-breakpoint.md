---
title: Создание точки останова | Документация Майкрософт
description: Сведения о вызовах методов, которые диспетчер отладки сеансов создает при загрузке модуля, необходимого для привязки точки останова.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 719a003e3dd46f46a0bf30642bed4b428d0956f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068002"
---
# <a name="create-a-breakpoint"></a>Создание точки останова
Ниже описывается процесс создания точки останова.

## <a name="methods-in-breakpoint-creation"></a>Методы в создании точки останова
 Когда загружается модуль, необходимый для привязки точки останова, диспетчер отладки сеансов (SDM) вызывает следующие методы:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **Канбинд** вызывается только в том случае, если пользователь создает точку останова из окна **точек останова** .

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>См. также
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
