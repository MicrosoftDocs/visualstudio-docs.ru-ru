---
description: Этот метод отменяет асинхронную оценку выражений, как это началось вызовом метода Евалуатеасинк).
title: 'IDebugExpression2:: Abort | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6c355d2c4ee3cf63551f54b050b0ea42f4fdddc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092453"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Этот метод отменяет асинхронную оценку выражений, как это было начато вызовом метода [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) .

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 При отмене асинхронного вычисления выражения не отправляют событие [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) обратному вызову события, переданному методам [attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) или [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="see-also"></a>См. также
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
