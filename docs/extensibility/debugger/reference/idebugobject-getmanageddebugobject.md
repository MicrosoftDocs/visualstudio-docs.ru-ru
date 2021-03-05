---
description: Создает копию управляемого объекта в адресном пространстве модуля отладки.
title: 'Идебугобжект:: Жетманажеддебугобжект | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87956b3630f9d152ecdda7754623e7257cf0a01a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164774"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Создает копию управляемого объекта в адресном пространстве модуля отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>Параметры
`ppObject`\
заполняет Возвращает объект [идебугманажедобжект](../../../extensibility/debugger/reference/idebugmanagedobject.md) , представляющий созданный управляемый объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки. Возвращает E_FAIL, если этот [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) не представляет экземпляр управляемого класса значения.

## <a name="remarks"></a>Комментарии
 Этот объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) должен представлять экземпляр управляемого класса значения, например `System.Decimal` экземпляр. При наличии локальной копии издержки вызова метода [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) исключаются.

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
