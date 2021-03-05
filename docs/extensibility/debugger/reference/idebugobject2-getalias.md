---
description: Возвращает псевдоним, связанный с этим объектом, если он есть.
title: IDebugObject2::/Alias | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c2ac683a5fb4d694b7cf3ab84849b9d7c7df7a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143133"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Возвращает псевдоним, связанный с этим объектом, если он есть.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Параметры
`ppAlias`\
заполняет Возвращает объект [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md) , представляющий псевдоним для данного объекта. в противном случае возвращает значение null.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Псевдоним для объекта создается с помощью вызова метода [креатеалиас](../../../extensibility/debugger/reference/idebugobject2-createalias.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
