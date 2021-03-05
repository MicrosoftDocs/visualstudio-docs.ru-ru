---
description: Указывает, какие сведения следует получить об объекте свойства отладки.
title: DEBUGPROP_INFO_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63467e93b80648e6a00728dc66971b7c9b3c9b24
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170527"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Указывает, какие сведения следует получить об объекте свойства отладки.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Поля
`DEBUGPROP_INFO_FULLNAME`\
Инициализируйте или используйте `bstrFullName` поле.

`DEBUGPROP_INFO_NAME`\
Инициализируйте или используйте `bstrName` поле.

`DEBUGPROP_INFO_TYPE`\
Инициализируйте или используйте `bstrType` поле.

`DEBUGPROP_INFO_VALUE`\
Инициализируйте или используйте `bstrValue` поле.

`DEBUGPROP_INFO_ATTRIB`\
Инициализируйте или используйте `dwAttrib` поле.

`DEBUGPROP_INFO_PROP`\
Инициализируйте или используйте `pProperty` поле, содержащее интерфейс [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Указывает, что поле значения должно содержать автоматическое развернутое значение (если доступно) для этого типа объекта.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Не рекомендуется.

`DEBUGPROP_INFO_VALUE_RAW`\
Не возвращайте никаких беаутифиед значений или элементов (то есть не форматируйте значения).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Не возвращайте никаких специальных синтезированных значений (например, не вызывайте `ToString()` объект для получения значения).

`DEBUGPROP_INFO_NONE`\
Указывает, что флаги не заданы.

`DEBUGPROP_INFO_STANDARD`\
Инициализируйте или используйте `dwAttrib` `bstrName` поля,, `bstrType` и `bstrValue` .

`DEBUGPROP_INFO_All`\
Указывает маску всех флагов.

## <a name="remarks"></a>Комментарии
Эти значения передаются методам [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [енумчилдрен](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)и [енумпропертиес](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) , чтобы указать, какие поля должны быть инициализированы структурой [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .

Эти значения также используются для `dwFields` элемента `DEBUG_PROPERTY_INFO` структуры, чтобы указать, какие поля структуры используются и допустимы при возврате структуры.

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
