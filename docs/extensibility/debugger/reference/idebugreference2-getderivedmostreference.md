---
description: Возвращает производную ссылку на ссылку.
title: 'IDebugReference2:: Жетдериведмостреференце | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c482b05620f280b2948aefe7e95eb38682268c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071445"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Возвращает производную ссылку на ссылку. Зарезервировано для последующего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>Параметры
`ppDerivedMost`\
заполняет Возвращает объект [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , представляющий производное свойство.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="remarks"></a>Remarks
 Например, если это свойство описывает объект, реализующий, `ClassRoot` но который на самом деле является экземпляром, `ClassDerived` производным от `ClassRoot` , то этот метод возвращает объект [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , представляющий ссылку на `ClassDerived` объект.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
