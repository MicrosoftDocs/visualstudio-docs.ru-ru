---
description: Используется для задания точек останова в коде на основе строки, которую пользователь может вводить из интегрированной среды разработки (IDE).
title: BP_LOCATION_CODE_STRING | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 9508a4a83894757fb47e35d8db7334bfb144ff59
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144381"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
Используется для задания точек останова в коде на основе строки, которую пользователь может вводить из интегрированной среды разработки (IDE).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>Члены
`bstrContext`\
Контекст точки останова в коде, обычно это имя метода или функции, как показано в стеке вызовов.

`bstrCodeExpr`\
Строка, которую пользователь вводит в для описания точки останова в коде.

## <a name="remarks"></a>Комментарии
Эта структура является членом структуры [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) в составе объединения.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
