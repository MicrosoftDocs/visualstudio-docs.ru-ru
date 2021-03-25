---
description: Задает значение объекта из последовательности байтов.
title: 'Идебугобжект:: SetValue | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63d75eae9c7966bfc5e7fceea0512db0fa174066
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054105"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Задает значение объекта из последовательности байтов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>Параметры
`pValue`\
окне Массив байтов, представляющий новое значение.

`nSize`\
окне Размер значения в байтах.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Значения в массиве копируются в этот объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , заменяя любое существующее значение. Размер нового значения может быть больше или меньше существующего значения. Это `IDebugObject` не может быть пустой ссылкой.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
