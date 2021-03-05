---
description: Возвращает контекст оценки для вычисления выражения в текущем контексте кадра стека и потока.
title: 'IDebugStackFrame2:: Жетекспрессионконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4780b979102ee2ada499e2cd2e0f8ca728cadd91
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145941"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Возвращает контекст оценки для вычисления выражения в текущем контексте кадра стека и потока.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetExpressionContext ( 
   IDebugExpressionContext2** ppExprCxt
);
```

```csharp
int GetExpressionContext ( 
   out IDebugExpressionContext2 ppExprCxt
);
```

## <a name="parameters"></a>Параметры
`ppExprCxt`\
заполняет Возвращает объект [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) , представляющий контекст для вычисления выражения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Как правило, контекст вычисления выражения можно рассматривать как область для вычисления выражений. Вызовите метод [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , чтобы проанализировать выражение, а затем вызвать результирующие методы [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для вычисления проанализированного выражения.

## <a name="see-also"></a>См. также раздел
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
