---
description: Извлекает структуру CONTEXT_INFO, описывающую контекст.
title: IDebugMemoryContext2::/info | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87f5dbf14d714f4915e99c23a56b8c9490dd23
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058629"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
Извлекает структуру [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) , описывающую контекст.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetInfo( 
   CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO*       pInfo
);
```

```csharp
int GetInfo(
   enum_CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO[]           pinfo
);
```

## <a name="parameters"></a>Параметры
`dwFields`\
окне Сочетание флагов из перечисления [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) , которое указывает, какие поля структуры [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) должны заполняться.

`pInfo`\
[вход, выход] `CONTEXT_INFO` Заполненная структура.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
