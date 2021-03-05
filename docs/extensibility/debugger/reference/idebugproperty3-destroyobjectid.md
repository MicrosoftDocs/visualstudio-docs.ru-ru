---
description: Уничтожает уникальный идентификатор, связанный с этим свойством, который указывает, что вызывающий объект более не должен идентифицировать это свойство, уникально на основе всех остальных свойств.
title: IDebugProperty3::D Естройобжектид | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa3712a12440f5d177f54544110bc8fa5d2e03ac
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166701"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Уничтожает уникальный идентификатор, связанный с этим свойством, который указывает, что вызывающий объект более не должен идентифицировать это свойство, уникально на основе всех остальных свойств.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Если модулю отладки не требуется поддерживать уникальные идентификаторы для свойства (поскольку он уже отслеживает их уникальным образом), то он может просто вернуться `E_NOTIMPL` для этого метода.

 Уникальные идентификаторы создаются с помощью вызова метода [креатеобжектид](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) , когда вызывающему объекту нужно убедиться, что это свойство однозначно идентифицируется всеми другими свойствами.

## <a name="see-also"></a>См. также раздел
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
