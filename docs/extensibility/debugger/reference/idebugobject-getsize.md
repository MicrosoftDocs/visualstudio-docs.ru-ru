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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f37176d039ede66152f1255dc5a2459525bfe4be
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054157"
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

## <a name="remarks"></a>Remarks
 Используйте метод [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) , чтобы получить значение в виде последовательности байтов.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
