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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7832dd89ddfbdb15908934ff3ba36ab309d08fa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153967"
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

## <a name="remarks"></a>Комментарии
 Исключения, удаленные этим методом, были заданы предыдущими вызовами метода [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Чтобы удалить конкретное исключение, вызовите метод [ремовесетексцептион](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
