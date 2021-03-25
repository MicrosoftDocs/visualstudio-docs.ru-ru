---
description: Задает число попаданий для привязанной точки останова.
title: 'IDebugBoundBreakpoint2:: Сеситкаунт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63284fea43c283ad291e0207946fe6f5d36f5a4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095775"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Задает число попаданий для привязанной точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

## <a name="parameters"></a>Параметры
`dwHitCount`\
окне Заданное число попаданий.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` значение, если состояние привязанного объекта точки останова равно `BPS_DELETED` (часть перечисления [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Remarks
 Число попаданий — это количество срабатываний этой точки останова во время текущего выполнения сеанса.

 Этот метод обычно вызывается модулем отладки для обновления текущего числа попаданий в этой точке останова.

## <a name="see-also"></a>См. также
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
