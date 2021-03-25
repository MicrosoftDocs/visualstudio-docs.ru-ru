---
description: Создает уникальный идентификатор или псевдоним для этого объекта или возвращает существующий псевдоним.
title: 'IDebugObject2:: Креатеалиас | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7265187172d79eb59624edb9c2428b243aae540
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053858"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Создает уникальный идентификатор или псевдоним для этого объекта или возвращает существующий псевдоним.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int CreateAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Параметры
`ppAlias`\
заполняет Новый (или существующий) псевдоним.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Псевдоним — это метка, представляющая определенный объект, в то время как объект находится в памяти.

## <a name="see-also"></a>См. также
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
