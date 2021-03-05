---
description: Перечисляет допустимые значения, указывающие сведения, которые необходимо получить о запросе точки останова.
title: BPREQI_FIELDS90 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5405f728cf979738de5a830421c4306c5e398bb2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151088"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Перечисляет допустимые значения, указывающие сведения, которые необходимо получить о запросе точки останова. Это перечисление расширяет перечисление [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) .

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Поля
`BPREQI90_BPLOCATION`\
Инициализируйте или используйте `bpLocation` поле (расположение точки останова) структуры [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) или [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI90_LANGUAGE`\
Инициализируйте или используйте `guidLanguage` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI90_PROGRAM`\
Инициализируйте или используйте `pProgram` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI90_PROGRAMNAME`\
Инициализируйте или используйте `bstrProgramName` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI90_THREAD`\
Инициализируйте или используйте `pThread` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI90_THREADNAME`\
Инициализируйте или используйте `bstrThreadName` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI90_PASSCOUNT`\
Инициализируйте или используйте `bpPassCount` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI90_CONDITION`\
Инициализируйте или используйте `bpCondition` поле (условие точки останова) `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI90_FLAGS`\
Инициализируйте или используйте `dwFlags` поле `BP_REQUEST_INFO` `BP_REQUEST_INFO2` структуры или.

`BPREQI90_ALLOLDFIELDS`\
Инициализация или использование всех полей для `BP_REQUEST_INFO` структуры.

`BPREQI90_VENDOR`\
Инициализируйте или используйте `guidVendor` поле `BP_REQUEST_INFO2` структуры.

`BPREQI90_CONSTRAINT`\
Инициализируйте или используйте `bstrConstraint` поле `BP_REQUEST_INFO2` структуры.

`BPREQI90_TRACEPOINT`\
Инициализируйте или используйте `bstrTracepoint` поле `BP_REQUEST_INFO2` структуры.

`BPREQI90_MACROTRACEPOINT`\
Инициализируйте или используйте `bstrMacroTracepoint` поле `BP_REQUEST_INFO2` структуры. BPREQI_ALLFIELDS не включает это поле.

`BPREQI90_ALLFIELDS`\
Задает все поля для `BP_REQUEST_INFO2` структуры.

## <a name="requirements"></a>Требования
Заголовок: Msdbg90. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
