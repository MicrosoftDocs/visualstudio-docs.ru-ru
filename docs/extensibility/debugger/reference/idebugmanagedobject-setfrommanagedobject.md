---
description: Задает значение экземпляра объекта класса значения из экземпляра класса значений, указанного в качестве параметра.
title: 'Идебугманажедобжект:: Сетфромманажедобжект | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c00e61de35e0cc9c33845236d8103bcd16cebfa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076853"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Задает значение экземпляра объекта класса значения из экземпляра класса значений, указанного в качестве параметра.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>Параметры
`pManagedObject`\
окне Интерфейс, представляющий управляемый объект, содержащий новое значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод используется для изменения управляемого объекта, представленного объектом [идебугманажедобжект](../../../extensibility/debugger/reference/idebugmanagedobject.md) .

## <a name="see-also"></a>См. также
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
