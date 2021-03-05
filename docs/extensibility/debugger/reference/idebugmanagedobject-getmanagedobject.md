---
description: Возвращает интерфейс, представляющий управляемый объект.
title: 'Идебугманажедобжект:: Жетманажедобжект | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1a262759cfcedd5fb0d09bcb995dcbcb7f7ee2a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165271"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Возвращает интерфейс, представляющий управляемый объект.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>Параметры
`ppManagedObject`\
заполняет Возвращает интерфейс, представляющий управляемый объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Интерфейс, возвращаемый из этого метода, можно запрашивать для любого интерфейса, реализованного управляемым классом, что позволяет вызывать его методы.

## <a name="see-also"></a>См. также раздел
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
