---
title: Вход в режим приостановки | Документация Майкрософт
description: Сведения о процессе, который выполняется для точки останова, обнаруженной в функции, выполнении до строки исходного кода в курсоре или выполнении до точки останова.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e8af8aa2765e199e8e278982669f68b3019b6c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097218"
---
# <a name="enter-break-mode"></a>Переход в режим приостановки выполнения
Следующая информация описывает процесс, возникающий при обнаружении точки останова после пошаговой обработки в функции, выполнения до строки исходного кода, в которой находится курсор, или при выполнении в точке останова.

## <a name="break-mode-process"></a>Процесс режима приостановки выполнения

1. Модуль отладки (DE) отправляет [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)или любое другое событие остановки, чтобы среда IDE переводила в режим приостановки.

2. Модель SDM получает сведения о стеке вызовов из потока следующим образом:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2:: жетдокументконтекст](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) , чтобы получить сведения о исходном коде

    - [IDebugDocumentContext2:: Name](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) для получения имени файла

    - [IDebugDocumentContext2:: жетстатементранже](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) для получения диапазона инструкций

    - [IDebugStackFrame2:: жеткодеконтекст](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) , чтобы получить сведения о памяти

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
