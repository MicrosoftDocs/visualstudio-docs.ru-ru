---
description: Пропускает указанное число элементов в перечислении путей кода.
title: 'IEnumCodePaths2:: Skip | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Skip
helpviewer_keywords:
- IEnumCodePaths2::Skip
ms.assetid: 356472d8-68b2-4b7e-b5f0-1f16d4ee80af
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c05084efe0c4e1fa119b0e76978c4094b87a0d1f
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225153"
---
# <a name="ienumcodepaths2skip"></a>IEnumCodePaths2::Skip
Пропускает заданное число элементов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Skip(
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
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
