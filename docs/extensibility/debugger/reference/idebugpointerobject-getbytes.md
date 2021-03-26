---
description: Возвращает значение, которое указывает на последовательность последовательных байтов.
title: 'Идебугпоинтеробжект:: GetBytes | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a150f819610de97ee292302d89e2007c6235aae
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087630"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Возвращает значение, которое указывает на последовательность последовательных байтов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Параметры
`dwStart`\
окне Смещение в байтах от начала объекта, на который указывает.

`dwCount`\
окне Число извлекаемых байтов.

`pBytes`\
[вход, выход] Массив, который заполняется значением в виде последовательности последовательных байтов, начиная с заданного смещения от объекта, на который указывает.

`pdwBytes`\
заполняет Возвращает число фактически извлеченных байтов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод используется, если указатель, представленный этим [идебугпоинтеробжект](../../../extensibility/debugger/reference/idebugpointerobject.md) , указывает на примитивный тип или простой массив типов-примитивов (то есть массив, который может быть представлен простой последовательностью байтов).

## <a name="see-also"></a>См. также
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
