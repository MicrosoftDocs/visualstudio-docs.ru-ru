---
description: Указывает условие, связанное с числом проходов точки останова, которое вызывает срабатывание точки останова.
title: BP_PASSCOUNT_STYLE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39a0dba08aa74386c442a7732b6522d8ee27652c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094475"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Указывает условие, связанное с числом проходов точки останова, которое вызывает срабатывание точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Поля
`BP_PASSCOUNT_NONE`\
Указывает, что стиль количества проходов точек останова не задан.

`BP_PASSCOUNT_EQUAL`\
Задает значение "равно" для стиля количества проходов точки останова. Точка останова срабатывает, когда количество попаданий в точку останова равно количеству проходов.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Задает для параметра число проходов точки останова значение равно или больше. Точка останова срабатывает, когда количество попаданий в точку останова равно или превышает число проходов.

`BP_PASSCOUNT_MOD`\
Указывает число проходов по модулю. Например, если число проходов имеет тип, `BP_PASSCOUNT_MOD` а значение счетчика Pass равно 4, то точка останова срабатывает каждый раз, когда число попаданий кратно 4.

## <a name="remarks"></a>Remarks
Используется для `stylePassCount` элемента структуры [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) , которая в свою очередь является членом структур [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
