---
description: Содержит сведения о состоянии точки останова, готовой к привязке к расположению кода.
title: PENDING_BP_STATE_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4da8892239740c65e1fcbbe618fa1ea76183e96
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079687"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Содержит сведения о состоянии точки останова, готовой к привязке к расположению кода.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagPENDING_BP_STATE_INFO { 
   PENDING_BP_STATE       state;
   PENDING_BP_STATE_FLAGS flags;
} PENDING_BP_STATE_INFO;
```

```csharp
public struct PENDING_BP_STATE_INFO { 
   public uint state;
   public uint flags;
};
```

## <a name="members"></a>Участники
 `state`\
 Значение из перечисления [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) , указывающее состояние ожидающей точки останова.

 `flags`\
 Сочетание флагов из перечисления [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) , которое указывает, является ли точка останова виртуализированной.

## <a name="remarks"></a>Remarks
 Эта структура передается в [метод WebMethod](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) , где он заполнен.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
