---
description: Эта структура описывает локальную переменную, параметр или другое поле.
title: FIELD_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27055178f01f41bb6b4642b8c4d70ea6346b9e74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059428"
---
# <a name="field_info"></a>FIELD_INFO
Эта структура описывает локальную переменную, параметр или другое поле.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Участники
`dwFields`\
Сочетание флагов из перечисления [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) , которое указывает, какие элементы заполняются.

`bstrFullName`\
Полное имя поля.

`bstrName`\
Краткое имя поля.

`bstrType`\
Тип поля.

`dwModifiers`\
Сочетание флагов из перечисления [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) , которое описывает поле.

## <a name="remarks"></a>Remarks
Эта структура передается в метод " [info](../../../extensibility/debugger/reference/idebugfield-getinfo.md) ", где он заполняется.

## <a name="requirements"></a>Требования
Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
