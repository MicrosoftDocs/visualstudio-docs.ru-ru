---
description: Содержит сведения, необходимые для реализации точки останова, включая GUID поставщика, ограничение и точку трассировки.
title: BP_REQUEST_INFO2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54ab1ec2ad37517a7a7fbfd7059022e1c5a26f82
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078205"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Содержит сведения, необходимые для реализации точки останова, включая GUID поставщика, ограничение и точку трассировки.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>Участники
`dwFields`\
Сочетание флагов из перечисления [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) , которое указывает, какие поля заполняются.

`guidLanguage`\
GUID языка.

`bpLocation`\
Структура [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) , указывающая тип расположения точки останова.

`pProgram`\
Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий приложение, в котором находится точка останова.

`bstrProgramName`\
Имя приложения, в котором происходит точка останова.

`pThread`\
Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором происходит точка останова.

`bstrThreadName`\
Имя потока, в котором происходит точка останова.

`bpCondition`\
Структура [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) , описывающая условия, при которых будет срабатывать точка останова.

`bpPassCount`\
Структура [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) , содержащая сведения о количестве проходов точки останова.

`dwFlags`\
Сочетание флагов из перечисления [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) , которое указывает флаги для запрошенной точки останова.

`guidVendor`\
Идентификатор GUID поставщика. Может иметь значение null.

`bstrConstraint`\
Имя ограничения точки останова. Может иметь значение null.

`bstrTracepoint`\
Имя точки трассировки. Может иметь значение null.

## <a name="remarks"></a>Remarks
Эта структура возвращается методом [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
