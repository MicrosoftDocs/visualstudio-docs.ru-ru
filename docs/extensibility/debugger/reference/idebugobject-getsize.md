---
description: Возвращает размер объекта в байтах.
title: 'Идебугобжект:: DataSize | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69d644cb86c0df592218a5f6c90b8c2b62339718
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159982"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
Возвращает размер объекта в байтах.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSize( 
   UINT* pnSize
);
```

```csharp
int GetSize(
   out uint pnSize
);
```

## <a name="parameters"></a>Параметры
`pnSize`\
заполняет Возвращает размер в байтах.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Используйте метод [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) , чтобы получить значение в виде последовательности байтов.

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
