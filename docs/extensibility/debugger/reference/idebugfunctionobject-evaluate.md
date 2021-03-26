---
description: 'Идебугфунктионобжект:: Evaluate вызывает функцию и возвращает результирующее значение в виде объекта.'
title: 'Идебугфунктионобжект:: Evaluate | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9770878040422d96c31fab8d57df468af614e8e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063595"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Вызывает функцию и возвращает результирующее значение в виде объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Параметры
`ppParams`\
окне Массив объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющих входные параметры. Каждый из этих параметров был создан с помощью одного из `Create` методов в интерфейсе [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

`dwParams`\
окне Число параметров в `ppParams` массиве.

`dwTimeout`\
окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.

`ppResult`\
заполняет Возвращает [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий значение функции в виде объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод настраивает и выполняет вызов функции, представленной объектом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>См. также
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
