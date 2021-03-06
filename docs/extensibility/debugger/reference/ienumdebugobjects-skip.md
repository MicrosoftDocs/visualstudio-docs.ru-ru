---
description: Этот метод пропускает указанное число элементов Идебугобжект.
title: 'Иенумдебугобжектс:: Skip | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 962083242b5b178ddf39e21328917d09dc0ed09a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224646"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
Этот метод пропускает указанное число элементов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   [In] uint celt
);
```

## <a name="parameters"></a>Параметры
`celt`\
[in] Число пропускаемых элементов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` `celt` , если больше числа оставшихся элементов; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Если `celt` задает значение, превышающее число оставшихся элементов, перечисление устанавливается в конец и `S_FALSE` возвращается.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
