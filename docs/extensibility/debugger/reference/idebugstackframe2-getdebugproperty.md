---
description: Возвращает описание свойств кадра стека.
title: 'IDebugStackFrame2:: Жетдебугпроперти | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c4017e5a14619c2ab5e3f98de65d7d2295e8586
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053481"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
Возвращает описание свойств кадра стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppDebugProp
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppDebugProp
);
```

## <a name="parameters"></a>Параметры
`ppDebugProp`\
заполняет Возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , описывающий свойства этого кадра стека.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Вызов метода [енумчилдрен](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) с соответствующими фильтрами может получить локальные переменные, параметры метода, регистры и указатель "this", связанный с кадром стека.

## <a name="see-also"></a>См. также
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
