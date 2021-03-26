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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 017dfa60c1f854a36f1087bef87203f0b22ae4dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083639"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Сравнивает одну ссылку с другой. Зарезервировано для последующего использования.

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

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
