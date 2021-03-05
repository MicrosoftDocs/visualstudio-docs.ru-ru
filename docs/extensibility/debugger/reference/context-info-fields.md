---
description: Указывает, какие сведения следует получить о контексте памяти.
title: CONTEXT_INFO_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 401195d5b03f87ba1ea5c66811570a720e53bdae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170774"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Указывает, какие сведения следует получить о контексте памяти.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Поля
`CIF_MODULEURL`\
Инициализируйте или используйте `bstrModuleUrl` поле структуры [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) .

`CIF_FUNCTION`\
Инициализируйте или используйте `bstrFunction` поле `CONTEXT_INFO` структуры.

`CIF_FUNCTIONOFFSET`\
Инициализируйте или используйте `posFunctionOffset` поле `CONTEXT_INFO` структуры.

`CIF_ADDRESS`\
Инициализируйте или используйте `bstrAddress` поле `CONTEXT_INFO` структуры.

`CIF_ADDRESSOFFSET`\
Инициализируйте или используйте `bstrAddressOffset` поле `CONTEXT_INFO` структуры.

`CIF_ALLFIELDS`\
Инициализация или использование всех полей `CONTEXT_INFO` структуры.

## <a name="remarks"></a>Комментарии
Эти значения передаются параметру в метод " [info](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) ", чтобы указать, какие поля структуры [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) должны быть инициализированы.

Эти флаги также используются для указания того, какие поля `CONTEXT_INFO` структуры используются и являются допустимыми при возврате структуры.

Эти значения можно комбинировать с помощью побитового или.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
