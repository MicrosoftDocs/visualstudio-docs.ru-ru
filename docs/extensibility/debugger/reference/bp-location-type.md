---
description: Задает тип расположения точки останова для запроса точки останова.
title: BP_LOCATION_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1ccf81393e42cc79b0ef93703b4a2327207baf6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144199"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Задает тип расположения точки останова для запроса точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Поля
`BPLT_NONE`\
Указывает, что расположение точки останова не указано.

`BPLT_FILE_LINE`\
Задает тип расположения точки останова в виде строки файла.

`BPLT_FUNC_OFFSET`\
Задает тип расположения точки останова в качестве смещения функции.

`BPLT_CONTEXT`\
Задает тип расположения точки останова в качестве контекста.

`BPLT_STRING`\
Задает тип расположения точки останова в виде строки.

`BPLT_ADDRESS`\
Указывает тип расположения точки останова в виде адреса.

`BPLT_RESOLUTION`\
Задает тип расположения точки останова в качестве разрешения.

`BPLT_CODE_FILE_LINE`\
Задает тип расположения точки останова в виде строки исходного кода.

`BPLT_CODE_FUNC_OFFSET`\
Задает тип расположения точки останова в виде смещения функции кода.

`BPLT_CODE_CONTEXT`\
Задает тип расположения точки останова в качестве контекста кода.

`BPLT_CODE_STRING`\
Задает тип расположения точки останова в виде строки кода.

`BPLT_CODE_ADDRESS`\
Задает тип расположения точки останова в виде адреса кода.

`BPLT_DATA_STRING`\
Задает тип расположения точки останова в виде строки данных.

`BPLT_TYPE_MASK`\
Задает битовую маску, чтобы тип точки останова мог извлекаться из значения.

`BPLT_LOCATION_TYPE_MASK`\
Задает битовую маску, чтобы тип расположения точки останова мог извлекаться из значения.

## <a name="remarks"></a>Комментарии
Передается в качестве параметра в метод [жетлокатионтипе](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) .

Тип расположения точки останова состоит из типа точки останова и типа расположения. Это означает, что тип расположения точки останова никогда не просто относится к типу точки останова (например, `BPT_CODE` ) или типу расположения (например, `BPLT_FILE_LINE` ). В это перечисление включены предопределенные константы для всех типов расположения точек останова, которые в настоящее время поддерживаются `BPLT_CODE_FILE_LINE` `BPLT_DATA_STRING` .

`BPT_CODE` и `BPT_DATA` являются членами перечисления [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
