---
description: Задает сведения, которые необходимо получить о запросе точки останова.
title: BPREQI_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f7ee5d8dbf48ad8d1b07512727b1b91635ab990
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162463"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Задает сведения, которые необходимо получить о запросе точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>Поля
`BPREQI_BPLOCATION`\
Инициализируйте или используйте `bpLocation` поле (расположение точки останова) структуры [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) или [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI_LANGUAGE`\
Инициализируйте или используйте `guidLanguage` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI_PROGRAM`\
Инициализируйте или используйте `pProgram` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI_PROGRAMNAME`\
Инициализируйте или используйте `bstrProgramName` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI_THREAD`\
Инициализируйте или используйте `pThread` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI_THREADNAME`\
Инициализируйте или используйте `bstrThreadName` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI_PASSCOUNT`\
Инициализируйте или используйте `bpPassCount` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI_CONDITION`\
Инициализируйте или используйте `bpCondition` поле (условие точки останова) `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI_FLAGS`\
Инициализируйте или используйте `dwFlags` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI_ALLOLDFIELDS`\
Инициализация/использование всех полей для `BP_REQUEST_INFO` структуры.

`BPREQI_VENDOR`\
Инициализируйте или используйте `guidVendor` поле `BP_REQUEST_INFO2` структуры.

`BPREQI_CONSTRAINT`\
Инициализируйте или используйте `bstrConstraint` поле `BP_REQUEST_INFO2` структуры.

`BPREQI_TRACEPOINT`\
Инициализируйте или используйте `bstrTracepoint` поле `BP_REQUEST_INFO2` структуры.

`BPREQI_ALLFIELDS`\
Задает все поля для `BP_REQUEST_INFO2` структуры.

## <a name="remarks"></a>Комментарии
Передается в качестве аргумента методам [жетрекуестинфо](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) и [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , чтобы указать, какие поля структур [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) должны быть инициализированы.

Эти флаги также используются для указания того, какие поля `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры и используются и являются допустимыми при возврате каждой структуры.

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
