---
description: Задает структуру расположения разрешения точки останова.
title: BP_RESOLUTION_LOCATION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87fef44d02911e84952f6eb8ab09dd9a1360dea6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162567"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Задает структуру расположения разрешения точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Члены
`bpType`\
Значение из перечисления [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) , указывающее способ интерпретации `bpResLocation` объединения или `unionmemberX` членов.

`bpResLocation.bpresCode`\
[Только C++] Содержит структуру [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) , если `bpType`  =  `BPT_CODE` .

`bpResLocation.bpresData`\
[Только C++] Содержит структуру [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) , если `bpType`  =  `BPT_DATA` .

`bpResLocation.unused`\
[Только C++] Заполнитель.

`unionmember1`\
[Только C#] См. раздел Примечания о том, как интерпретировать.

`unionmember2`\
[Только C#] См. раздел Примечания о том, как интерпретировать.

`unionmember3`\
[Только C#] См. раздел Примечания о том, как интерпретировать.

`unionmember4`\
[Только C#] См. раздел Примечания о том, как интерпретировать.

## <a name="remarks"></a>Комментарии
Эта структура является членом структур [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) и [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .

 [Только C#] Элементы обрабатываются в `unionmemberX` соответствии со следующей таблицей. Загляните в левый столбец для `bpType` значения, чтобы определить, что каждый `unionmemberX` элемент представляет и маршалировать `unionmemberX` соответствующим образом. См. пример для интерпретации этой структуры в C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (выражение данных)|`string` (имя функции)|`string` (имя образа)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Пример
В этом примере показано, как интерпретировать `BP_RESOLUTION_LOCATION` структуру в C#.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
            }
        }
    }
}
```

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
