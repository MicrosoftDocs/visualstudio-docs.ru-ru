---
description: Обновляет данные объекта с помощью заданного объекта данных и возвращает новый объект данных, представляющий новые данные объекта.
title: 'Ипропертипроксеесиде:: Инплацеупдатеобжект | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2119db579863bea2ad0b9fa5834996d658308549
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225595"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Обновляет данные объекта с помощью заданного объекта данных и возвращает новый объект данных, представляющий новые данные объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Параметры
`dataIn`\
окне Объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , содержащий новые данные.

`dataOut`\
заполняет Возвращает новый `IEEDataStorage` объект, содержащий замененные данные.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод фактически обновляет данные объекта. Данные в возвращенном объекте [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) не обязательно должны совпадать с данными во входящем `IEEDataStorage` объекте, но возвращаемый объект должен отражать текущее значение свойства.

 Объект входящих данных обычно не реализуется в EE. Однако объект, возвращаемый этим методом, всегда реализуется в EE, что позволяет `IEEDataStorage` классу ee реализовать интерфейс в любом нужном классе.

 Метод [функция createreplacementobject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) создает объект данных на основе входящего объекта данных, но не влияет на исходные данные свойства.

## <a name="see-also"></a>См. также раздел
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
