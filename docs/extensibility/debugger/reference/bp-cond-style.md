---
description: Задает стиль условия точки останова для ожидающих и связанных точек останова.
title: BP_COND_STYLE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c23549d1553902c00048f946d2711c497fbe2322
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144485"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Задает стиль условия точки останова для ожидающих и связанных точек останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Поля
`BP_COND_NONE`\
Вызывает точку останова, когда достигнута точка точки останова. Условие для точки останова не указано.

`BP_COND_WHEN_TRUE`\
Вызывает точку останова только в том случае, если условное выражение, связанное с точкой останова, имеет значение `true` .

`BP_COND_WHEN_CHANGED`\
Вызывает точку останова только в том случае, если значение условного выражения, связанное с точкой останова, изменилось по сравнению с предыдущим вычислением.

## <a name="remarks"></a>Комментарии
Используется для `styleCondition` элемента структуры [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
