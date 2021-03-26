---
description: Извлекает объект службы по заданному уникальному идентификатору.
title: 'IDebugExpressionEvaluator2:: "Услуга" | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a9c595d2a3a4551920e17a9ad8d8a13b5ae4ab0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092011"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Извлекает объект службы по заданному уникальному идентификатору.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Параметры
`uid`\
окне Уникальный идентификатор получаемой службы.

`ppService`\
заполняет Возвращает объект, представляющий службу.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот механизм может использоваться сторонним средством оценки выражений для получения служб от другого средства оценки выражений. Например, этот метод можно использовать для получения интерфейса для службы визуализатора из вычислителя выражений по умолчанию. Средствам оценки выражений сторонних производителей вряд ли придется реализовывать этот интерфейс.

## <a name="see-also"></a>См. также
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
