---
description: Возвращает текущее число попаданий для этой привязанной точки останова.
title: 'IDebugBoundBreakpoint2:: Жеситкаунт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eec08d34f74ad1f91b7c9cbabd4b3982f270bf09
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167611"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
Возвращает текущее число попаданий для этой привязанной точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetHitCount( 
   DWORD* pdwHitCount
);
```

```csharp
int GetHitCount( 
   out uint pdwHitCount
);
```

## <a name="parameters"></a>Параметры
`pdwHitCount`\
заполняет Возвращает число попаданий.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` значение, если состояние привязанного объекта точки останова равно `BPS_DELETED` (часть перечисления [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Комментарии
 Число попаданий — это количество срабатываний этой точки останова во время текущего выполнения сеанса.

## <a name="see-also"></a>См. также раздел
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
