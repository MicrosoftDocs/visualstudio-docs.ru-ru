---
description: Задает атрибуты события.
title: ЕВЕНТАТТРИБУТЕС | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6b56e815d8145e3f870468751a0978475245c86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150891"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Задает атрибуты события.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Поля
`EVENT_ASYNCHRONOUS`\
Указывает, что событие является асинхронным и ответ на событие не требуется.

`EVENT_SYNCHRONOUS`\
Указывает, что событие является синхронным; ответ — с помощью [континуефромсинчронаусевент](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Указывает, что это событие остановки. Необходимо сочетать с `EVENT_ASYNCHRONOUS` или `EVENT_SYNCHRONOUS` .

`EVENT_ASYNC_STOP`\
Указывает на асинхронное событие остановки. В настоящее время такого события нет. Этот флаг является только заполнителем.

`EVENT_SYNC_STOP`\
Указывает на синхронную остановку события (сочетание `EVENT_SYNCHRONOUS` и `EVENT_STOPPING` ). Это значение используется модулем отладки (DE) при отправке события остановки. Ответ делается с помощью вызова метода [EXECUTE](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)или [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Указывает на событие, которое отправляется в интегрированную среду разработки немедленно и синхронно. Этот флаг сочетается с другими флагами `EVENT_ASYNCHRONOUS` , например, `EVENT_SYNCHRONOUS` или, `EVENT_SYNC_STOP` чтобы указать тип события и тот факт, что известен механизм ответа (если таковой имеется).

`EVENT_EXPRESSION_EVALUATION`\
Событие является результатом вычисления выражения.

## <a name="remarks"></a>Комментарии
Эти значения передаются в `dwAttrib` параметре метода [события](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
