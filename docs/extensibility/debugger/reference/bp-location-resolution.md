---
description: Описывает разрешение точки останова в определенном месте.
title: BP_LOCATION_RESOLUTION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_RESOLUTION
helpviewer_keywords:
- BP_LOCATION_RESOLUTION structure
ms.assetid: 86ea2c8a-54a3-48e8-83c7-18a515273129
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 80ed7f4f0206542e5f6a4289aba1d833eef5937a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144225"
---
# <a name="bp_location_resolution"></a>BP_LOCATION_RESOLUTION
Описывает разрешение точки останова в определенном месте.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION_RESOLUTION {
    IDebugBreakpointResolution2* pResolution;
} BP_LOCATION_RESOLUTION;
```

## <a name="members"></a>Члены
`pResolution`\
Объект [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) , определяющий тип точки останова и сведения о его разрешении.

## <a name="remarks"></a>Комментарии
Эта структура является членом структуры [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) в составе объединения.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
