---
description: Указывает тип структуры, используемой для описания расположения точки останова.
title: BP_LOCATION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0ee3c9246c25517c2b0bc095c4035400e43d29b5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096724"
---
# <a name="bp_location"></a>BP_LOCATION
Указывает тип структуры, используемой для описания расположения точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Участники
`bpLocationType`\
Значение из перечисления [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) , используемое для интерпретации `bpLocation` объединения или `unionmemberX` членов.

`bpLocation`.`bplocCodeFileLine`\
[Только C++] Содержит структуру [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) , если `bpLocationType`  =  `BPLT_CODE_FILE_LINE` .

`bpLocation.bplocCodeFuncOffset`\
[Только C++] Содержит структуру [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) , если `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET` .

`bpLocation.bplocCodeContext`\
[Только C++] Содержит структуру [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) , если `bpLocationType`  =  `BPLT_CODE_CONTEXT` .

`bpLocation.bplocCodeString`\
[Только C++] Содержит структуру [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) , если `bpLocationType`  =  `BPLT_CODE_STRING` .

`bpLocation.bplocCodeAddress`\
[Только C++] Содержит структуру [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) , если `bpLocationType`  =  `BPLT_CODE_ADDRESS` .

`bpLocation.bplocDataString`\
[Только C++] Содержит структуру [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) , если `bpLocationType`  =  `BPLT_DATA_STRING` .

`bpLocation.bplocResolution`\
[Только C++] Содержит структуру [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) , если `bpLocationType`  =  `BPLT_RESOLUTION` .

`unionmember1`\
[Только C#] См. раздел Примечания о том, как интерпретировать.

`unionmember2`\
[Только C#] См. раздел Примечания о том, как интерпретировать.

`unionmember3`\
[Только C#] См. раздел Примечания о том, как интерпретировать.

`unionmember4`\
[Только C#] См. раздел Примечания о том, как интерпретировать.

## <a name="remarks"></a>Remarks
Эта структура является членом структур [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

 [Только C#] Элементы обрабатываются в `unionmemberX` соответствии со следующей таблицей. Взгляните на левый столбец для `bpLocationType` значения, затем взгляните на другие столбцы, чтобы определить, что каждый `unionmemberX` элемент представляет и маршалировать `unionmemberX` соответствующим образом. См. пример для интерпретации части этой структуры в C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (контекст)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (контекст)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (контекст)|`string` (условное выражение)|-|-|
|`BPLT_CODE_ADDRESS`|`string` (контекст)|`string` (URL-адрес модуля)|`string` (имя функции)|`string` Address|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (контекст)|`string` (выражение данных)|`uint` (число элементов)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Пример
В этом примере показано, как интерпретировать `BP_LOCATION` структуру в C# для `BPLT_DATA_STRING` типа. Этот конкретный тип показывает, как интерпретировать все четыре `unionmemberX` элемента во всех возможных форматах (объект, строка и число).

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
            }
        }
    }
}
```

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
