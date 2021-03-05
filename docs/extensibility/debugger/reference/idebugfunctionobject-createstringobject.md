---
description: Создает строковый объект.
title: 'Идебугфунктионобжект:: Креатестрингобжект | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78d9d0be09ee8fa6374273ad308616a7d294c8cf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166480"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
Создает строковый объект.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

## <a name="parameters"></a>Параметры
`pcstrString`\
окне Строковое значение для объекта String.

`ppObject`\
заполняет Возвращает объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий только что созданный строковый объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Вызовите этот метод, чтобы создать объект, представляющий строку, которая является параметром функции, представленной интерфейсом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
