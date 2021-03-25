---
title: Достижение точки останова | Документация Майкрософт
description: В этой статье описывается процесс, который происходит при попадании отладчика в точку останова во время работы или пошагового выполнения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e093437fcc8b3e1e2663c2a46ebb3b70d32efbec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059955"
---
# <a name="hit-a-breakpoint"></a>Попадание в точку останова
В следующем разделе описывается процесс, когда модуль отладки (DE) достигает точки останова при выполнении или пошаговом выполнении.

## <a name="troubleshoot-a-hit-breakpoint"></a>Устранение неполадок в точке останова

1. Параметр DE отправляет интерфейс [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) в качестве **EVENT_SYNC_STOP**.

2. Диспетчер отладки сеансов (SDM) вызывает [IDebugBreakpointEvent2::: енумбреакпоинтс](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) для получения точки останова, которая была достигнута.

## <a name="see-also"></a>См. также
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
