---
description: Создает копию объекта данных, относящегося к Вычислителю выражений (EE).
title: 'Ипропертипроксеесиде:: функция createreplacementobject | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 460052ceb9f2f90a5123f4cc646682919f96dc94
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082586"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Создает копию объекта данных, относящегося к Вычислителю выражений (EE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Параметры
`dataIn`\
окне Объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , содержащий копируемые данные.

`dataOut`\
[out] Возвращает новый объект `IEEDataStorage`.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этому методу предоставляется объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , представляющий массив байтов. Этот объект входящих данных обычно не реализуется в EE. Однако объект, возвращаемый этим методом, всегда реализуется в EE, что позволяет `IEEDataStorage` классу ee реализовать интерфейс в любом нужном классе.

 Обратите внимание, что данные, передаваемые входящим `IEEDataStorage` объектом, должны быть одними и теми же данными в исходящем `IEEDataStorage` объекте.

## <a name="see-also"></a>См. также
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
