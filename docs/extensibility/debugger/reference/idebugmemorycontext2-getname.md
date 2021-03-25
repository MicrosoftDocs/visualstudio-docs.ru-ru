---
description: Возвращает отображаемое пользователем имя для этого контекста.
title: 'IDebugMemoryContext2:: Name | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89d5d3cb1d2bed36a9e15f99644a02bdc308e0ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058616"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
Возвращает отображаемое пользователем имя для этого контекста.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>Параметры
`pbstrName`\
заполняет Возвращает имя контекста памяти.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Имя контекста памяти обычно не используется.

## <a name="see-also"></a>См. также
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
