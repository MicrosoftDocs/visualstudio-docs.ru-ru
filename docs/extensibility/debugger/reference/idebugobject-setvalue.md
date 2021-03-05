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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 972281335b964679f38693182e42c4e64074dffa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167156"
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

## <a name="remarks"></a>Комментарии
 Значения в массиве копируются в этот объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , заменяя любое существующее значение. Размер нового значения может быть больше или меньше существующего значения. Это `IDebugObject` не может быть пустой ссылкой.

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
