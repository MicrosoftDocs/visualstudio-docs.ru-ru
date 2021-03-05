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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f64e2e8ec365daa84cbd1d4f7e3e9bdc43391d5e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170436"
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

## <a name="remarks"></a>Комментарии
Передается в качестве аргумента в метод [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .

Эти значения используются для указания критериев сравнения для поиска первого контекста документа в списке. Контекст документа получает список контекстов документов для сравнения с помощью `IDebugDocumentContext2::Compare` метода. Затем возвращается первый контекст документа в списке, для которого выполняется оператор сравнения `true` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Сравнить](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
