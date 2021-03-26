---
description: Возвращает контекст памяти, представляющий адрес значения объекта.
title: 'Идебугобжект:: Жетмемориконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54df34a989d56ac9c1a962943eeda172c90e5554
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081858"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Возвращает контекст памяти, представляющий адрес значения объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>Параметры
`pContext`\
заполняет Возвращает объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , представляющий адрес значения объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Возвращаемый контекст памяти задает адрес значения, представленного этим объектом [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="see-also"></a>См. также
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
