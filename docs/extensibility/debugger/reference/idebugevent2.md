---
description: Этот интерфейс используется для передачи критически важных отладочных данных, таких как остановка в точке останова, и некритически важных данных, например сообщения об отладке.
title: IDebugEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e162e276fc93c9e2c0d4333ac0f5c2630f75618e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152953"
---
# <a name="idebugevent2"></a>IDebugEvent2
Этот интерфейс используется для передачи критически важных отладочных данных, таких как остановка в точке останова, и некритически важных данных, например сообщения об отладке.

## <a name="syntax"></a>Синтаксис

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) и поставщик пользовательского порта реализуют этот интерфейс на том же объекте, что и все остальные интерфейсы событий.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используя аргумент идентификатора интерфейса (IID), заданный для [события](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) или [события](../../../extensibility/debugger/reference/idebugportevents2-event.md), диспетчер отладки сеансов (SDM) вызывает [QueryInterface](/cpp/atl/queryinterface) в `IDebugEvent2` интерфейсе для получения соответствующего интерфейса событий.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEvent2` .

|Метод|Описание|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Возвращает атрибуты для данного события отладки.|

## <a name="remarks"></a>Комментарии
 Более конкретные интерфейсы событий, такие как [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), не являются производными от интерфейса IDebugEvent2, но реализуются в виде отдельного интерфейса для того же объекта, что и `IDebugEvent2` .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
