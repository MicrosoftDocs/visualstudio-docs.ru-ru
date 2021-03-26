---
title: События элемента управления | Документация Майкрософт
description: Сведения об отправке событий во время управляемого выполнения программы с помощью интерфейса IDebugEvent2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aeee5ed91eca7666d08dfd08ec02b850a7739db9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085537"
---
# <a name="control-events"></a>События элемента управления
События необходимо отправить во время управляемого выполнения программы. Все события отправляются с помощью интерфейса [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) и имеют атрибуты, требующие реализации метода [IDebugEvent2:: OutAttribute](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .

## <a name="additional-methods"></a>Дополнительные методы
 Для некоторых событий требуется реализация дополнительных методов, как показано ниже.

- Отправка интерфейса [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) при инициализации модуля отладки (de) требует реализации метода [IDebugEngineCreateEvent2::-Engine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .

- Управление выполнением требует реализации таких событий элемента управления, как интерфейсы [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) и[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) . **IDebugBreakEvent2** требуется только для асинхронных прерываний.

- Для пошагового выполнения функций требуется реализация интерфейса [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) и его методов.

  События, производные от точек останова, должны быть реализованы в интерфейсах [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)и [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) , а также в методах [IDebugBreakpointBoundEvent2:: жетпендингбреакпоинт](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) и [енумбаундбреакпоинтс](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

  Асинхронное вычисление выражений требует реализации интерфейса [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) и его методов [IDebugExpressionEvaluationCompleteEvent2:: Express](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[и](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .

  Для синхронных событий требуется реализация метода [IDebugEngine2:: континуефромсинчронаусевент](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

  Чтобы обработчик написал выходные данные в стиле строки, необходимо реализовать метод [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) .

## <a name="see-also"></a>См. также
- [Контроль выполнения и оценка состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
