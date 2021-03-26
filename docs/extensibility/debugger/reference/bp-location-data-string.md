---
description: Используется для установки точек останова по данным, основанных на строке, которую пользователь может вводить из интегрированной среды разработки (IDE).
title: BP_LOCATION_DATA_STRING | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 98cfb12649fe85ce9e5f6b6a51a8c61243b5e9da
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096763"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Используется для установки точек останова по данным, основанных на строке, которую пользователь может вводить из интегрированной среды разработки (IDE).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Участники
`pThread`\
Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором происходит точка останова.

`bstrContext`\
Контекст точки останова в коде, обычно это имя метода или функции, как показано в стеке вызовов.

`bstrDataExpr`\
Строка данных, которую пользователь вводит для задания точки останова.

`dwNumElements`\
Количество элементов в строке данных, в которой происходит точка останова.

## <a name="remarks"></a>Remarks
Эта структура является членом структуры [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) в составе объединения.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
