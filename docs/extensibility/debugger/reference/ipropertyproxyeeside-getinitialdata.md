---
description: Возвращает начальные данные для этого объекта.
title: 'Ипропертипроксеесиде:: Жетинитиалдата | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetInitialData
helpviewer_keywords:
- IPropertyProxyEESide::GetInitialData
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96129d254ad153b6a0ad754931cd18abba803849
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082534"
---
# <a name="ipropertyproxyeesidegetinitialdata"></a>IPropertyProxyEESide::GetInitialData
Возвращает начальные данные для этого объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetInitialData(
   IEEDataStorage** dataOut
);
```

```csharp
int GetInitialData(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Параметры
`dataOut`\
заполняет Возвращает объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , содержащий начальные данные этого объекта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
