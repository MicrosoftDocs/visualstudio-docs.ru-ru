---
description: Описывает положение смещения точки останова в функции в коде.
title: BP_LOCATION_CODE_FUNC_OFFSET | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 83a5a27601ab6d7498394d6723b86ad3e66aceb5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144368"
---
# <a name="bp_location_code_func_offset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Описывает положение смещения точки останова в функции в коде.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>Члены
`bstrContext`\
Контекст точки останова, обычно имя метода или функции, как показано в стеке вызовов.

`pFuncPos`\
Объект [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) , описывающий имя функции и относительное расположение от начала функции.

## <a name="remarks"></a>Комментарии
Эта структура является членом структуры [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) в составе объединения.

`pFuncPos`Элемент указывает, где следует задать точку останова функции.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
