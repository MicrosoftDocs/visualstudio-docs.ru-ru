---
description: Этот интерфейс представляет точку останова, привязанную к расположению кода.
title: IDebugBoundBreakpoint2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2726a2422c49335d9c95e7d500381ad1fdc0108
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167481"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Этот интерфейс представляет точку останова, привязанную к расположению кода.

## <a name="syntax"></a>Синтаксис

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки точек останова.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создает этот интерфейс. Вызовы метода [](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) [GetNext и Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) могут также получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBoundBreakpoint2` .

|Метод|Описание|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Возвращает ожидающую точку останова, из которой была создана указанная связанная точка останова.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Возвращает состояние этой привязанной точки останова.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Возвращает текущее число попаданий для этой привязанной точки останова.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Возвращает разрешение точки останова, которое описывает эту точку останова.|
|[Разрешить](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Включает или отключает точку останова.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Задает число попаданий для этой привязанной точки останова.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Задает или изменяет условие, связанное с этой привязанной точкой останова.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Задает или изменяет число проходов, связанных с этой привязанной точкой останова.|
|[Удаление](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет точку останова.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Выполняется](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
