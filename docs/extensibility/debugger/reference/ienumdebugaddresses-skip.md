---
description: Этот метод пропускает указанное число элементов в перечислении адресов.
title: 'Иенумдебугаддрессес:: Skip | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Skip
helpviewer_keywords:
- IEnumDebugAddresses::Skip method
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ae1b23c28f98d90649e701b7ff96b2394a9894b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222657"
---
# <a name="ienumdebugaddressesskip"></a>IEnumDebugAddresses::Skip
Этот метод пропускает указанное число элементов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   uint celt
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
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
