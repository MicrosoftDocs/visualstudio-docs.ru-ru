---
description: Получает запрос точки останова, который использовался для создания этой ожидающей точки останова.
title: 'IDebugPendingBreakpoint2:: Жетбреакпоинтрекуест | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest
helpviewer_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest method
- GetBreakpointRequest method
ms.assetid: cb1e36aa-4302-455c-98fb-6638a1ef5c46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b6ead0a48147b999b83fa3ccc8062ff767920fa5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072680"
---
# <a name="idebugpendingbreakpoint2getbreakpointrequest"></a>IDebugPendingBreakpoint2::GetBreakpointRequest
Получает запрос точки останова, который использовался для создания этой ожидающей точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetBreakpointRequest( 
   IDebugBreakpointRequest2** ppBPRequest
);
```

```csharp
int GetBreakpointRequest( 
   out IDebugBreakpointRequest2 ppBPRequest
);
```

## <a name="parameters"></a>Параметры
`ppBPRequest`\
заполняет Возвращает объект [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) , представляющий запрос точки останова, который использовался для создания этой ожидающей точки останова.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает значение `E_BP_DELETED` , если точка останова была удалена.

## <a name="see-also"></a>См. также
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
