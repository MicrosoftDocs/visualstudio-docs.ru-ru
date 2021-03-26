---
description: Удаляет список исключений, установленных интегрированной средой разработки для определенной архитектуры или языка среды выполнения.
title: 'IDebugEngine2:: Ремовеаллсетексцептионс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b40da7391fc360b68da70f02f4d32afb92e83a58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087942"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Удаляет список исключений, установленных интегрированной средой разработки для определенной архитектуры или языка среды выполнения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT RemoveAllSetExceptions( 
   REFGUID guidType
);
```

```csharp
int RemoveAllSetExceptions( 
   ref Guid guidType
);
```

## <a name="parameters"></a>Параметры
`guidType`\
окне Идентификатор GUID для языка или GUID для модуля отладки, характерный для архитектуры времени выполнения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Исключения, удаленные этим методом, были заданы предыдущими вызовами метода [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Чтобы удалить конкретное исключение, вызовите метод [ремовесетексцептион](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) .

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
