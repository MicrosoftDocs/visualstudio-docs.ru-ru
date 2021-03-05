---
description: Описывает разрешение точки останова по ошибке, включая расположение, программу и поток.
title: BP_ERROR_RESOLUTION_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 730ab3558f1e0b466ec22f5966735257b70ccfbd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144420"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Описывает разрешение точки останова по ошибке, включая расположение, программу и поток.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Члены
`dwFields`\
Сочетание значений перечисления [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) , указывающее, какие поля этой структуры заполнены.

`bpResLocation`\
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) объединение, которое указывает расположение разрешения точки останова.

`pProgram`\
Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий приложение, в котором произошла ошибка точки останова.

`pThread`\
Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором работает приложение, создавшее ошибку точки останова.

`bstrMessage`\
Строка, содержащая любое предупреждение или сообщение об ошибке, полученное при этом разрешении ошибки.

`dwType`\
Значение из перечисления [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) , указывающее тип ошибки точки останова.

## <a name="remarks"></a>Комментарии
Эта структура возвращается методом [жетресолутионинфо](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
