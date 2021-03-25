---
description: Задает критерий для сравнения двух контекстов документа.
title: DOCCONTEXT_COMPARE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6eeee3e31c898660930b676df716fe25769bbb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096009"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Задает критерий для сравнения двух контекстов документа.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Поля
`DOCCONTEXT_EQUAL`\
Найдите в списке первый контекст документа, равный контексту целевого документа.

`DOCCONTEXT_LESS_THAN`\
Найдите в списке первый контекст документа, который меньше целевого контекста документа.

`DOCCONTEXT_GREATER_THAN`\
Найдите в списке первый контекст документа, превышающий целевой контекст документа.

`DOCCONTEXT_SAME_DOCUMENT`\
Найдите в списке первый контекст документа, который находится в том же документе, что и целевой контекст документа.

## <a name="remarks"></a>Remarks
Передается в качестве аргумента в метод [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .

Эти значения используются для указания критериев сравнения для поиска первого контекста документа в списке. Контекст документа получает список контекстов документов для сравнения с помощью `IDebugDocumentContext2::Compare` метода. Затем возвращается первый контекст документа в списке, для которого выполняется оператор сравнения `true` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Сравнить](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
