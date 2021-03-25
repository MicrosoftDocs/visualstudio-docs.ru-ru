---
description: Задает критерий для сравнения двух контекстов памяти.
title: CONTEXT_COMPARE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd74516c3f687f05b2d5fb33dc2b94455114bbc6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094449"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Задает критерий для сравнения двух контекстов памяти.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Поля
`CONTEXT_EQUAL`\
Найдите в списке первый контекст памяти, равный контексту целевой памяти.

`CONTEXT_LESS_THAN`\
Найдите в списке первый контекст памяти, который меньше контекста целевой памяти.

`CONTEXT_GREATER_THAN`\
Найдите в списке первый контекст памяти, превышающий целевой контекст памяти.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Найдите в списке первый контекст памяти, который меньше или равен контексту целевой памяти.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Найдите в списке первый контекст памяти, который больше или равен контексту целевой памяти.

`CONTEXT_SAME_SCOPE`\
Найдите в списке первый контекст памяти, который находится в той же области, что и контекст целевой памяти.

`CONTEXT_SAME_FUNCTION`\
Найдите в списке первый контекст памяти, который находится в той же функции, что и Целевая область памяти.

`CONTEXT_SAME_MODULE`\
Найдите в списке первый контекст памяти, который находится в том же модуле, что и целевой контекст памяти.

`CONTEXT_SAME_PROCESS`\
Найдите в списке первый контекст памяти, который находится в том же процессе, что и целевой контекст памяти.

## <a name="remarks"></a>Remarks
Передается в качестве аргумента в метод [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) .

Эти значения используются для поиска контекста первой памяти в списке, удовлетворяющего указанным критериям сравнения. Контекст памяти получает список контекста памяти для сравнения с помощью `IDebugMemoryContext2::Compare` метода. Затем возвращается контекст первой памяти в списке, для которого выполняется оператор сравнения `true` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Сравнить](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
