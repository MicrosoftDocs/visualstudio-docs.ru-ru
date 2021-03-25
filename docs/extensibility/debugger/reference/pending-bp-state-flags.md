---
description: Задает флаги состояния ожидания точки останова.
title: PENDING_BP_STATE_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5e462c460b5ae41f0a1a33db62a058b1da6fa15
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086460"
---
# <a name="pending_bp_state_flags"></a>PENDING_BP_STATE_FLAGS
Задает флаги состояния ожидания точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
typedef DWORD PENDING_BP_STATE_FLAGS;
```

```csharp
public enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
```

## <a name="fields"></a>Поля
 `PBPSF_NONE` Заполнителе.

 `PBPSF_VIRTUALIZED` Задает виртуализированную незавершенную точку останова, которая должна быть привязана при каждом загрузке нового кода.

## <a name="remarks"></a>Remarks
 Используется для `flags` элемента структуры [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
