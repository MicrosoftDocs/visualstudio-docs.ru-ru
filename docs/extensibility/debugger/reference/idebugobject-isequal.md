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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cff388778ea584f589f92b5dc9dab11c060c953c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054092"
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

## <a name="remarks"></a>Remarks
 Как правило, этот метод может сравнивать адреса значений, представленных `pObject` параметром, и этого объекта [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) . Если адреса равны, объекты можно считать равными.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
