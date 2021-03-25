---
description: Определяет, представляет ли поле закрытый тип.
title: 'Идебужекстендедфиелд:: Исклоседтипе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ba4c55b53ebb1f1e5ad2000f31efc8a37f81eef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077204"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Определяет, представляет ли поле закрытый тип.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Возвращаемое значение
 Если поле является закрытым типом, возвращает `S_OK` ; в противном случае возвращает `S_FALSE` .

## <a name="see-also"></a>См. также
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
