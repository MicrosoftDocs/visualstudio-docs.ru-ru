---
description: Задает тип ссылки.
title: 'IDebugReference2:: Сетреференцетипе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetReferenceType
helpviewer_keywords:
- IDebugReference2::SetReferenceType
ms.assetid: 5854a172-ea82-481c-97d9-c7fc16923d44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3faaa31d277f2966a5975fe31f59fd12cd8c355
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075813"
---
# <a name="idebugreference2setreferencetype"></a>IDebugReference2::SetReferenceType
Задает тип ссылки. Зарезервировано для последующего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetReferenceType ( 
   REFERENCE_TYPE dwRefType
);
```

```csharp
int SetReferenceType ( 
   enum_REFERENCE_TYPE dwRefType
);
```

## <a name="parameters"></a>Параметры
`dwRefType`\
окне Значение из перечисления [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) , указывающее ссылочный тип.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
