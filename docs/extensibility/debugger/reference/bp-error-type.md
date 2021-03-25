---
description: Указывает тип ошибки точки останова.
title: BP_ERROR_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddff439aba67248bd2eb706a85c5f91b4bf1628d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085290"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Указывает тип ошибки точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Поля
`BPET_NONE`\
Указывает отсутствие ошибки точки останова.

`BPET_TYPE_WARNING`\
Указывает ошибку точки останова в стиле предупреждения.

`BPET_TYPE_ERROR`\
Указывает ошибку точки останова в стиле ошибки.

`BPET_SEV_HIGH`\
Указывает ошибку точки останова с высокой степенью серьезности.

`BPET_SEV_GENERAL`\
Указывает ошибку точки останова со средним уровнем серьезности.

`BPET_SEV_LOW`\
Указывает ошибку точки останова с низким уровнем серьезности.

`BPET_TYPE_MASK`\
Указывает ошибку точки останова в стиле маски.

`BPET_SEV_MASK`\
Задает ошибку точки останова с уровнем серьезности-маска.

`BPET_GENERAL_WARNING`\
Указывает ошибку точки останова общего стиля предупреждения.

`BPET_GENERAL_ERROR`\
Указывает общую ошибку точки останова в стиле ошибки.

`BPET_ALL`\
Указывает все типы ошибок точек останова.

## <a name="remarks"></a>Remarks
Эти значения можно комбинировать с помощью побитового `OR` и используемого для `dwType` элемента структуры [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) . Передается в качестве параметра в метод [енумеррорбреакпоинтс](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) .

Тип ошибки точки останова состоит из типа и степени серьезности. Это означает, что тип ошибки точки останова никогда не является просто типом (например, `BPET_TYPE_ERROR` ) или уровнем серьезности (например, `BPET_SEV_GENERAL` ). `BPET_GENERAL_WARNING` и `BPET_GENERAL_ERROR` предоставляют стандартные значения для общих точек останова и предупреждений об ошибках.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
