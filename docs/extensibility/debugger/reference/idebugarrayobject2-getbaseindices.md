---
description: Получает базовые индексы (нижние границы) для каждого индекса, учитывая количество измерений в массиве.
title: 'IDebugArrayObject2:: Жетбасеиндицес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3ec8c0081205637ae228c426ac29d0523602439
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167793"
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

## <a name="remarks"></a>Комментарии
 В качестве примера эта функция возвращает значение "5" для массива, созданного следующим кодом C#:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>См. также раздел
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
