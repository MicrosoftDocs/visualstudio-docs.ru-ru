---
description: Помечает этот псевдоним для удаления.
title: Идебугалиас::D Dispose | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: efca2b2bedc531fa241d8cfe6cfe8cd3527a7b40
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143926"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Помечает этот псевдоним для удаления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 После вызова этого метода псевдоним будет недоступен.

## <a name="see-also"></a>См. также раздел
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
