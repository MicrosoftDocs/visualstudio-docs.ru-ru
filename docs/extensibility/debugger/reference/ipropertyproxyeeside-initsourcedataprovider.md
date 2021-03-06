---
description: Инициализирует исходные данные для этого объекта и возвращает объект, содержащий начальные данные.
title: 'Ипропертипроксеесиде:: Инитсаурцедатапровидер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd1040c6269b9d394e6f0968f595c71cf1576135
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224126"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Инициализирует исходные данные для этого объекта и возвращает объект, содержащий начальные данные.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Параметры
`dataOut`\
заполняет Возвращает объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md)

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод выполняет все необходимое для инициализации объекта, чтобы он мог вернуть интерфейс [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) к данным объекта. Это позволяет просматривать данные объекта и, если это разрешено, изменено визуализатором типов.

## <a name="see-also"></a>См. также раздел
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
