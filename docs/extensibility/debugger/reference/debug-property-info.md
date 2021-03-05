---
description: Содержит сведения о свойстве Debug.
title: DEBUG_PROPERTY_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0b02ca1f8c85f81096954fb416cc73ee400b9ba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170592"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Содержит сведения о свойстве Debug.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Члены
`dwValidFields`\
Сочетание флагов из перечисления [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , которое указывает, какие поля заполняются.

`bstrFullName`\
Полное имя свойства.

`bstrName`\
Имя свойства в контексте.

`bstrType`\
Тип свойства в виде форматированной строки.

`bstrValue`\
Значение свойства в виде форматированной строки.

`pProperty`\
Объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , описываемый этой структурой.

`dwAttrib`\
Сочетание флагов из перечисления [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , описывающее атрибуты этого свойства.

## <a name="remarks"></a>Комментарии
Свойство — это объект иерархической природы, имеющий имя, тип и значение. Например, свойство может описывать локальные переменные, параметры, контрольные переменные и выражения, а также регистры.

Эта структура передается в метод [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) , где она заполнена. Эта структура также возвращается как часть списка этой структуры из интерфейса [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , который, в свою очередь, возвращается из вызова методов [енумчилдрен](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) и [енумпропертиес](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
