---
description: Вычитает указанное значение из текущего контекста и возвращает новый контекст.
title: 'IDebugMemoryContext2:: Subtract | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1007a50ca42164cfc4e4f58c8d2c877cbba20f5c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058590"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Вычитает указанное значение из текущего контекста и возвращает новый контекст.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Параметры
`dwCount`\
окне Число байтов памяти для уменьшения.

`ppMemCxt`\
заполняет Возвращает новый объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Контекст памяти — это адрес, поэтому при вычитании значения из адреса создается новый адрес, для которого требуется новый интерфейс контекста.

 Этот метод всегда должен создавать новый контекст, даже если полученный адрес находится вне области памяти, связанной с этим контекстом. Единственным исключением является то, что память не может быть выделена для нового контекста или если `ppMemCxt` является значением NULL (это ошибка).

## <a name="see-also"></a>См. также
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
