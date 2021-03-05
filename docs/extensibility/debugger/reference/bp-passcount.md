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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c1e44ede0f39b3d1b33967311365508da6a701d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144160"
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

## <a name="members"></a>Члены
`dwPassCount`\
Количество проходов через точку останова перед ее срабатыванием.

`stylePassCount`\
Значение из перечисления [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) , указывающее стиль числа проходов точки останова.

## <a name="remarks"></a>Комментарии
Эта структура является членом структуры [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) .

Эта структура также передается в качестве параметра методам[сетпасскаунт](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) и[сетпасскаунт](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
