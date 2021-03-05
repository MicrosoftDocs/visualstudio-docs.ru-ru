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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 658da43471f483e80a1e77bd61f69dbc454a141e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159891"
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

## <a name="remarks"></a>Комментарии
 Вызов метода [енумчилдрен](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) с соответствующими фильтрами может получить локальные переменные, параметры метода, регистры и указатель "this", связанный с кадром стека.

## <a name="see-also"></a>См. также раздел
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
