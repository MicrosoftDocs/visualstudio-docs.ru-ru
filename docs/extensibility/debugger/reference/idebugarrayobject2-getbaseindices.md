---
description: Получает базовые индексы (нижние границы) для каждого индекса, учитывая количество измерений в массиве.
title: 'IDebugArrayObject2:: Жетбасеиндицес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3843b93bb9255c28b8ca083af37a3ba4ecbd7f7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067560"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Получает базовые индексы (нижние границы) для каждого индекса, учитывая количество измерений в массиве.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

## <a name="parameters"></a>Параметры
`dwRank`\
окне Количество измерений (Rank) массива.

`dwIndices`\
заполняет Базовые индексы (нижние границы) для массива.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 В качестве примера эта функция возвращает значение "5" для массива, созданного следующим кодом C#:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>См. также
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
