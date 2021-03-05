---
description: Сравнивает объект с этим объектом.
title: 'Идебугобжект:: Equals | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0907b72f2a0647fc6ff6181ecdc5c7fd8c2134cb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151666"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Сравнивает объект с этим объектом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Параметры
`pObject`\
окне Объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий объект для сравнения.

`pfIsEqual`\
заполняет Возвращает ненулевое значение ( `TRUE` ), если значения объектов равны; в противном случае возвращает ноль ( `FALSE` ).

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Как правило, этот метод может сравнивать адреса значений, представленных `pObject` параметром, и этого объекта [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) . Если адреса равны, объекты можно считать равными.

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
