---
description: Добавляет указанное значение в текущий контекст и возвращает новый контекст.
title: 'IDebugMemoryContext2:: Add | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59daddd38daff2f04f12bc0d1be4e06ec90cf723
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166428"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Добавляет указанное значение в текущий контекст и возвращает новый контекст.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Параметры
`dwCount`\
окне Значение, добавляемое в текущий контекст.

`ppMemCxt`\
заполняет Возвращает новый объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Контекст памяти — это адрес, поэтому при добавлении значения в адрес создается новый адрес, для которого требуется новый интерфейс контекста.

 Этот метод всегда должен создавать новый контекст, даже если полученный адрес находится вне области памяти, связанной с этим контекстом. Единственным исключением является то, что память не может быть выделена для нового контекста или если `ppMemCxt` является значением NULL (это ошибка).

## <a name="see-also"></a>См. также раздел
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
