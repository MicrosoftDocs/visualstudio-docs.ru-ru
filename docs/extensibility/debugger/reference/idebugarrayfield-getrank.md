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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9e3d822bac6fa16314f5d2962d69adbf74d0bc3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143718"
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

## <a name="remarks"></a>Комментарии
 Ранг массива соответствует числу измерений. В C++ и C# многомерные массивы являются массивами массивов и поэтому могут рассматриваться только как одномерные массивы (и `GetRank` метод всегда возвращает 1). В с [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] другой стороны многомерные массивы обрабатываются по-разному, а ранг такого массива отражает количество измерений (и `GetRank` метод всегда возвращает количество измерений).

## <a name="see-also"></a>См. также раздел
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
