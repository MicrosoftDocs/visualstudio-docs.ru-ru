---
description: Этот метод находит псевдоним по заданному имени.
title: 'IDebugBinder3:: Финдалиас | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9958c1c2b93d6547f1f3453bafc9e331f9061844
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089060"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Этот метод находит псевдоним по заданному имени. При этом будут искаться все псевдонимы в программе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Параметры
`pcstrName`\
окне Имя искомого псевдонима.

`ppAlias`\
заполняет Найден псевдоним (если имеется), представленный интерфейсом [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает значение `S_FALSE` (если псевдоним не найден) или код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод инициализирует целевой объект до значения null перед вызовом метода; После этого проверяется наличие значения NULL, чтобы определить, был ли найден псевдоним.

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
