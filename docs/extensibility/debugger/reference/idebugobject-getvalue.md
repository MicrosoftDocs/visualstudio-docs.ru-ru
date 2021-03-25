---
description: Возвращает значение объекта в виде последовательности байтов.
title: 'Идебугобжект:: GetValue | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d957743a725ad462a9ed95fca6ebdffbecb6de16
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054131"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Возвращает значение объекта в виде последовательности байтов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Параметры
`pValue`\
[вход, выход] Массив, который заполняется последовательными последовательностями байтов, представляющими значение объекта.

`nSize`\
окне Максимальное число извлекаемых байтов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Возвращает общее количество байтов значений, которые можно получить, вызвав [метод GetBytes](../../../extensibility/debugger/reference/idebugobject-getsize.md) .

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
