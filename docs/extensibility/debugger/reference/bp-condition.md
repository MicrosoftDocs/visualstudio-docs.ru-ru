---
description: Описывает условия, при которых срабатывает точка останова.
title: BP_CONDITION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10b360dfa6d811834ea9564e5f73c80f6eeea722
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144459"
---
# <a name="bp_condition"></a>BP_CONDITION
Описывает условия, при которых срабатывает точка останова.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Члены
`pThread`\
Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий активный поток для приложения, содержащего точку останова.

`styleCondition`\
Значение из перечисления [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) , описывающее стиль условия этой точки останова.

`bstrContext`\
Расположение точки останова.

`bstrCondition`\
Условие срабатывания точки останова.

`nRadix`\
Основание системы счисления, используемое при вычислении любых числовых данных.

## <a name="remarks"></a>Комментарии
Эта структура является членом структур [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

Эта структура также передается в качестве параметра методам [сеткондитион](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) и [сеткондитион](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
