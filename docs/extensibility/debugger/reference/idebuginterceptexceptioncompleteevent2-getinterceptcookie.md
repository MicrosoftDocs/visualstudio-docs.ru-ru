---
description: Вызывается при завершении обработки перехваченного исключения.
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52c0cdf514f606287386c68713371d112cb97e79
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091920"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Вызывается при завершении обработки перехваченного исключения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetInterceptCookie(
   UINT64* pqwCookie
);
```

```csharp
int GetInterceptCookie(
   out ulong pqwCookie
);
```

## <a name="parameters"></a>Параметры
`pqwCookie`\
заполняет Уникальное значение, связанное с перехваченным исключением.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 После того как метод [интерцепткуррентексцептион](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) завершает обработку перехваченного исключения, он отправляет событие [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) . Обработчик может использовать `GetInterceptCookie` метод для получения уникального значения, связанного с исключением (то же значение, которое было передано в `InterceptCurrentException` метод).

## <a name="see-also"></a>См. также
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
