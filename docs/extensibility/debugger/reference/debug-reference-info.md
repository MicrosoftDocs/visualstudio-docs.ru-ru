---
description: Описывает ссылку.
title: DEBUG_REFERENCE_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 729dab8cc7a8b2960c699cce503400d97c6fa398
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096243"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Описывает ссылку.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Участники
`dwFields`\
Сочетание флагов из перечисления [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) , которое указывает, какие поля заполняются.

`bstrName`\
Заданное пользователем имя объекта [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .

`bstrType`\
Ссылочный тип в виде форматированной строки.

`bstrValue`\
Ссылочное значение в виде форматированной строки

`dwAttrib`\
Сочетание флагов из перечисления [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , которое задает флаги для атрибутов свойств отладки.

`dwRefType`\
Значение из перечисления [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) , указывающее, является ли ссылочный тип строгим или слабым.

`m_pReference`\
Объект [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , указывающий справочные сведения.

## <a name="remarks"></a>Remarks
Эта структура передается в вызов метода [жетреференцеинфо](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) , который должен быть заполнен. Эта структура также возвращается как часть списка из интерфейса [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) , который, в свою очередь, возвращается из вызова метода [енумчилдрен](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
