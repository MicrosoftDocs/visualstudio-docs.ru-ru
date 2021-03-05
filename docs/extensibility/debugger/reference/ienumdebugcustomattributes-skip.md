---
description: Пропускает указанное число настраиваемых атрибутов в последовательности перечисления.
title: 'Иенумдебугкустоматтрибутес:: Skip | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Skip
helpviewer_keywords:
- IEnumDebugCustomAttributes::Skip
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c57ca47b8d5100ff9c9bf7451e07ad0924775475
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226804"
---
# <a name="ienumdebugcustomattributesskip"></a>IEnumDebugCustomAttributes::Skip
Пропускает указанное число настраиваемых атрибутов в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Skip ( 
   ULONG celt
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
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
