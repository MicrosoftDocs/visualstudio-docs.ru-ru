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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db4d5cad6d0c2990141e0dd3a824425b8b53145b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167728"
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

## <a name="remarks"></a>Комментарии
 Этот метод инициализирует целевой объект до значения null перед вызовом метода; После этого проверяется наличие значения NULL, чтобы определить, был ли найден псевдоним.

## <a name="see-also"></a>См. также раздел
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
