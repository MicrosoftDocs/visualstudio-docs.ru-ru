---
description: Возвращает ранг или количество измерений массива.
title: 'Идебугаррайфиелд:: Rank | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ac945e23090b649ffb5ad2f452ec9245aac81ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058980"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Возвращает ранг или количество измерений массива.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Параметры
`pdwRank`\
заполняет Возвращает ранг.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Ранг массива соответствует числу измерений. В C++ и C# многомерные массивы являются массивами массивов и поэтому могут рассматриваться только как одномерные массивы (и `GetRank` метод всегда возвращает 1). В с [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] другой стороны многомерные массивы обрабатываются по-разному, а ранг такого массива отражает количество измерений (и `GetRank` метод всегда возвращает количество измерений).

## <a name="see-also"></a>См. также
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
