---
title: Методы Breakpoint-Related | Документация Майкрософт
description: Отладка Visual Studio поддерживает привязанные точки останова, которые успешно привязаны к расположению в коде, и ожидающие точки останова, которые еще не привязаны.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec218cea05dffc1c558cabdef47895da9ad7ba9c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901504"
---
# <a name="breakpoint-related-methods"></a>Методы, связанные с точкой останова
Модуль отладки (DE) должен поддерживать настройку точек останова. Отладка Visual Studio поддерживает следующие типы точек останова:

- Bound

     Запрашивается через пользовательский интерфейс и успешно привязан к указанному расположению кода

- Не завершен

     Запрашивается через пользовательский интерфейс, но еще не привязан к фактическим инструкциям

## <a name="discussion"></a>Разговор
 Например, ожидающая точка останова возникает, когда инструкции еще не загружены. При загрузке кода ожидающие точки останова пытаются выполнить привязку к коду в указанном расположении, то есть вставить инструкции break в код. События отправляются в Диспетчер отладки сеансов (SDM) для обозначения успешной привязки или уведомления о возникновении ошибок привязки.

 Ожидающая точка останова также управляет собственным внутренним списком соответствующих связанных точек останова. Одна из ожидающих точек останова может привести к вставке множества точек останова в коде. В пользовательском интерфейсе отладки Visual Studio отображается древовидное представление ожидающих точек останова и соответствующих им связанных точек останова.

 Создание и использование ожидающих точек останова требует реализации метода [IDebugEngine2:: креатепендингбреакпоинт](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) , а также следующих методов интерфейсов [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

|Метод|Описание|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет, может ли заданная ожидающая точка останова быть привязана к расположению кода.|
|[Выполняется](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Привязывает указанную отложенную точку останова к одному или нескольким расположениям кода.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Возвращает состояние ожидающей точки останова.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Получает запрос точки останова, используемый для создания ожидающей точки останова.|
|[Разрешить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает включенное состояние ожидающей точки останова.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки останова, привязанные к ожидающей точке останова.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Перечисляет все точки останова, являющиеся результатом ожидающей точки останова.|
|[Удалить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Удаляет отложенную точку останова и все точки останова, привязанные к ней.|

 Чтобы перечислить привязанные точки останова и точки останова с ошибками, необходимо реализовать все методы [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) и [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Ожидающие точки останова, привязанные к расположению кода, должны реализовать следующие методы [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

|Метод|Описание|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Возвращает ожидающую точку останова, содержащую точку останова.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Возвращает состояние привязанной точки останова.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Возвращает разрешение точки останова, описывающее точку останова.|
|[Разрешить](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Включает или отключает точку останова.|
|[Удалить](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет связанную точку останова.|

 Для разрешения и сведений о запросе требуется реализация следующих методов [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .

|Метод|Описание|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Возвращает тип точки останова, представленной разрешением.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешении точки останова, описывающие точку останова.|

 Разрешение ошибок, которые могут возникнуть во время привязки, требует реализации следующих методов [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

|Метод|Описание|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Возвращает ожидающую точку останова, содержащую точку останова.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Возвращает разрешение ошибки точки останова, описывающее точку останова.|

 Разрешение ошибок, которые могут возникнуть во время привязки, также требует использования следующих методов [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Метод|Описание|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Возвращает тип точки останова.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешении точки останова.|

 Для просмотра исходного кода в точке останова необходимо реализовать методы [IDebugStackFrame2:: жетдокументконтекст](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) и/или методов [IDebugStackFrame2:: жеткодеконтекст](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>См. также
- [Контроль выполнения и оценка состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
