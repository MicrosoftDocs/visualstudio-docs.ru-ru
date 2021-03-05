---
description: Этот метод определяет тип времени выполнения объекта.
title: 'Идебугбиндер:: Ресолверунтиметипе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19e7285dd25009e7fe4aeb92974c70ce4109502c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143640"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Этот метод определяет тип времени выполнения объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>Параметры
`pObject`\
окне [Идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , который необходимо разрешить.

`ppResolved`\
заполняет Возвращает тип объекта в виде [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Тип времени выполнения объекта не всегда известен во время компиляции. Например, с помощью полиморфизма аргумент может быть передан в функцию в качестве базового класса, например класса Button. Фактический аргумент может быть производным классом, например классом переключателя.

## <a name="see-also"></a>См. также раздел
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
