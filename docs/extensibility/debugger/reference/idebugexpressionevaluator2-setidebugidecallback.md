---
description: Позволяет модулю отладки передавать обратный вызов средству оценки выражений во время инициализации.
title: 'IDebugExpressionEvaluator2:: Сетидебугидекаллбакк | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetIDebugIDECallback
- SetIDebugIDECallback
ms.assetid: f01c40ad-ef4b-477b-8304-602c6972bc88
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3793fbcf19b87d6aed1df81d6739ae6529c2ba14
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077334"
---
# <a name="idebugexpressionevaluator2setidebugidecallback"></a>IDebugExpressionEvaluator2::SetIDebugIDECallback
Позволяет модулю отладки передавать обратный вызов средству оценки выражений во время инициализации.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetIDebugIDECallback (
   IDebugIDECallback * pCallback
);
```

```csharp
int SetIDebugIDECallback (
   IDebugIDECallback pCallback
);
```

## <a name="parameters"></a>Параметры
`pCallback`\
окне Интерфейс для обратного вызова.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
