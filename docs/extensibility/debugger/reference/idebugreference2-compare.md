---
description: Сравнивает одну ссылку с другой.
title: 'IDebugReference2:: Compare | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef006cba574e0cc5f51d2ec45eb6187b1076543a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166011"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Сравнивает одну ссылку с другой. Зарезервировано для будущего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>Параметры
`dwCompare`\
окне Значение из перечисления [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) , указывающее операцию сравнения, например, "равно", "меньше" или "больше чем".

`pReference`\
окне Объект [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , представляющий ссылку, сравниваемую с.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="see-also"></a>См. также раздел
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
