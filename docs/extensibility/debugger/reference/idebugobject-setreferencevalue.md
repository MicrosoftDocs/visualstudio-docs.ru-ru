---
description: Задает значение ссылки для этого объекта.
title: 'Идебугобжект:: Сетреференцевалуе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb376e4399157f9f9fe393086cca8fcf94c3b9de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161428"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Задает значение ссылки для этого объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Параметры
`pObject`\
окне Объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий новое значение ссылки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод делает этот объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) ссылкой на значение объекта, указанного в `pObject` параметре, вызывая предыдущую ссылку. Обратите внимание, что этот `IDebugObject` объект уже должен быть ссылочным типом.

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
