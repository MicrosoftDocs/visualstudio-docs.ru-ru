---
description: Задает значение, на которое указывает последовательность последовательных байтов.
title: 'Идебугпоинтеробжект:: SetBytes | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31feb63e4f9d246161ced3483f487b2877ee5e1e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169669"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Задает значение, на которое указывает последовательность последовательных байтов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Параметры
`dwStart`\
окне Смещение в байтах от начала объекта, на который указывает.

`dwCount`\
окне Число байтов, которое необходимо задать.

`pBytes`\
окне Массив байтов, представляющий новое значение. Это значение сохраняется в объект, начиная с заданного смещения.

`pdwBytes`\
заполняет Возвращает число фактически установленных байтов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод используется, если указатель, представленный этим [идебугпоинтеробжект](../../../extensibility/debugger/reference/idebugpointerobject.md) , указывает на примитивный тип или простой массив типов-примитивов (то есть массив, который может быть представлен простой последовательностью байтов). Этот `IDebugPointerObject` объект не может быть пустой ссылкой (он должен указывать на адрес в памяти).

## <a name="see-also"></a>См. также раздел
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
