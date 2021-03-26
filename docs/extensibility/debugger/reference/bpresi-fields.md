---
description: Задает сведения, которые должны быть получены об успешном разрешении точки останова.
title: BPRESI_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 652d1423b95f923a8413bdec6fbbed528e9f624a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096698"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Задает сведения, которые должны быть получены об успешном разрешении точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Поля
`BPRESI_BPRESLOCATION`\
Инициализируйте или используйте `bpResLocation` поле (расположение разрешения точки останова) структуры [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .

`BPRESI_PROGRAM`\
Инициализируйте или используйте `pProgram` поле `BP_RESOLUTION_INFO` структуры.

`BPRESI_THREAD`\
Инициализируйте или используйте `pThread` поле `BP_RESOLUTION_INFO` структуры.

`BPRESI_ALLFIELDS`\
Задает все поля.

## <a name="remarks"></a>Remarks
Передается в метод [жетресолутионинфо](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) , чтобы указать, какие поля структуры [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) должны быть инициализированы.

Эти флаги также используются для указания того, какие поля `BP_RESOLUTION_INFO` структуры используются и являются допустимыми при возврате этой структуры.

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
