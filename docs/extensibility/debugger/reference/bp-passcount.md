---
description: Описывает количество и условия срабатывания условной точки останова.
title: BP_PASSCOUNT | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afb94436897224bc9c6896a601447e9d9a1c8b6f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096737"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Описывает количество и условия срабатывания условной точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Участники
`dwPassCount`\
Количество проходов через точку останова перед ее срабатыванием.

`stylePassCount`\
Значение из перечисления [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) , указывающее стиль числа проходов точки останова.

## <a name="remarks"></a>Remarks
Эта структура является членом структуры [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) .

Эта структура также передается в качестве параметра методам[сетпасскаунт](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) и[сетпасскаунт](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
