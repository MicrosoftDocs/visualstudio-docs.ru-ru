---
description: Указывает, находится ли точка останова в расположении кода, является расположением данных или другим типом точки останова.
title: BP_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e310154bc62cdea1fb9069cc868cf9e20335d06
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151109"
---
# <a name="bp_type"></a>BP_TYPE
Указывает, находится ли точка останова в расположении кода, является расположением данных или другим типом точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>Поля
`BPT_NONE`\
Указывает, что тип точки останова отсутствует.

`BPT_CODE`\
Задает точку останова в коде.

`BPT_DATA`\
Задает точку останова в данных.

`BPT_SPECIAL`\
Указывает точку останова, которая не является ни кодом, ни типом данных. Этот тип является устаревшим и не должен использоваться.

## <a name="remarks"></a>Комментарии
Передается в качестве параметра методам [жетбреакпоинттипе](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) и [жетбреакпоинттипе](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
