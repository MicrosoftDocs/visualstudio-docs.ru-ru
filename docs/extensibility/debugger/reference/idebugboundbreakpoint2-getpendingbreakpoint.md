---
description: Возвращает ожидающую точку останова, из которой была создана указанная связанная точка останова.
title: 'IDebugBoundBreakpoint2:: Жетпендингбреакпоинт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint method
- GetPendingBreakpoint method
ms.assetid: 22f94f81-f8d9-46de-96e9-fae6f3c24903
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15b053515268c16bfacdeee08e40390950542e38
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095840"
---
# <a name="idebugboundbreakpoint2getpendingbreakpoint"></a>IDebugBoundBreakpoint2::GetPendingBreakpoint
Возвращает ожидающую точку останова, из которой была создана указанная связанная точка останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPendingBreakpoint( 
    IDebugPendingBreakpoint2** ppPendingBreakpoint
);
```

```csharp
int GetPendingBreakpoint( 
    out IDebugPendingBreakpoint2 ppPendingBreakpoint
);
```

## <a name="parameters"></a>Параметры
`ppPendingBreakpoint`\
заполняет Возвращает объект [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , представляющий отложенную точку останова, которая использовалась для создания этой привязанной точки останова.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
Отложенная точка останова может рассматриваться как коллекция всех необходимых сведений, необходимых для привязки точки останова к коду, который может быть применен к одной или нескольким программам.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CBoundBreakpoint` объекта, предоставляющего интерфейс [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

```
HRESULT CBoundBreakpoint::GetPendingBreakpoint(
    IDebugPendingBreakpoint2** ppPendingBreakpoint)
{
    HRESULT hr;

    // Check for valid IDebugPendingBreakpoint2 interface pointer.
    if (ppPendingBreakpoint)
    {
        // Be sure that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugPendingBreakpoint2 interface.
            hr = m_pPendingBP->QueryInterface(IID_IDebugPendingBreakpoint2,
                                              (void**)ppPendingBreakpoint);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
