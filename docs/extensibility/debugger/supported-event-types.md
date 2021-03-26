---
title: Поддерживаемые типы событий | Документация Майкрософт
description: Сведения о типах событий, поддерживаемых отладкой Visual Studio, включая асинхронные события, синхронные события и события остановки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 883c9fd51cc4dfc4f2cc2f996d24c0722478505f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079414"
---
# <a name="supported-event-types"></a>Поддерживаемые типы событий
В настоящее время отладка Visual Studio поддерживает следующие типы событий:

- Асинхронные события

   Уведомлять диспетчер отладки сеанса (SDM) и IDE о том, что состояние отлаживаемого приложения изменяется. Эти события обрабатываются в свободное время SDM и интегрированной среды разработки. Ответ не отправляется в модуль отладки (DE) после обработки события. Интерфейсы [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) и [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) являются примерами асинхронных событий.

- Синхронные события

   Уведомлять SDM и IDE о том, что состояние отлаживаемого приложения изменяется. Единственное различие между этими событиями и асинхронными событиями заключается в том, что ответ отправляется с помощью метода [континуефромсинчронаусевент](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

   Отправка синхронного события полезна, если требуется продолжить обработку после того, как интегрированная среда разработки получит и обработает событие.

- Синхронная остановка событий или остановка событий

   Уведомлять SDM и интегрированную среду разработки, что отлаживаемый приложение остановило выполнение кода. При отправке события остановки с помощью [события](../../extensibility/debugger/reference/idebugeventcallback2-event.md)метода параметр [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) является обязательным. Остановка событий продолжается вызовом одного из следующих методов:

  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Продолжить](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Интерфейсы [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) и [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) являются примерами остановки событий.

  > [!NOTE]
  > Асинхронные события остановки не поддерживаются. Отправка события асинхронной остановки не является ошибкой.

## <a name="discussion"></a>Разговор
 Фактическая реализация событий зависит от структуры вашего DE. Тип каждого отправленного события определяется его атрибутами, которые устанавливаются при проектировании DE. Например, один из них может отправить [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) как асинхронное событие, а другой может отправить его как событие остановки.

 В следующей таблице указано, какие параметры программы и потока требуются для событий, а также для типов событий. Любое событие может быть синхронным. Ни одно событие не должно быть синхронным.

> [!NOTE]
> Интерфейс [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) является обязательным для всех событий.

|Событие|IDebugProgram2|IDebugThread2|Остановка событий|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Нет|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Обязательно|Обязательно|Да|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Нет|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Нет|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Нет|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Обязательно|Обязательно|Да|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Обязательно|Обязательно|Нет|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Нельзя использовать|Нельзя использовать|Нет|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Нельзя использовать|Нельзя использовать|Нет|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Обязательно|Обязательно|Да|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Может быть|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Обязательно|Обязательно|Да|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Может быть|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Обязательно|Обязательно|Да|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Обязательно|Обязательно|Да|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Может быть|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Обязательно|Разрешено, но не требуется|Нет|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Нет|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Обязательно|Разрешено, но не требуется|Нет|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Обязательно|Разрешено, но не требуется|Нет|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Обязательно|Разрешено, но не требуется|Нет|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Обязательно|Разрешено, но не требуется|Нет|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Нет|
|IDebugStopCompleteEvent2|Обязательно|Обязательно|Да|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Обязательно|Обязательно|Да|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Нет|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Обязательно|Обязательно|Нет|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Обязательно|Обязательно|Нет|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Нет|

## <a name="see-also"></a>См. также раздел
- [Отправка событий](../../extensibility/debugger/sending-events.md)
