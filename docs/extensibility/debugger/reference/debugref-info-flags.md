---
description: Указывает, какие сведения следует получить об эталонном объекте Debug.
title: DEBUGREF_INFO_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: da408e159f654f9eb707e71710a178d22881d715
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170514"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Указывает, какие сведения следует получить об эталонном объекте Debug.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Поля
`DEBUGREF_INFO_NAME`\
Инициализируйте или используйте `bstrName` поле в структуре.

`DEBUGREF_INFO_TYPE`\
Инициализируйте или используйте `bstrType` поле в структуре.

`DEBUGREF_INFO_VALUE`\
Инициализируйте или используйте `bstrValue` поле в структуре.

`DEBUGREF_INFO_ATTRIB`\
Инициализируйте или используйте `dwAttrib` поле в структуре.

`DEBUGREF_INFO_REFTYPE`\
Инициализируйте или используйте `dwRefType` поле в структуре.

`DEBUGREF_INFO_REF`\
Инициализируйте или используйте `pReference` поле в структуре.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Поле значения должно содержать автоматическое развернутое значение (если доступно) для этого типа объекта.

`DEBUGREF_INFO_NONE`\
Указывает, что флаги не заданы.

`DEBUGREF_INFO_ALL`\
Указывает маску флагов.

## <a name="remarks"></a>Комментарии
Эти флаги передаются методам [енумчилдрен](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) и [жетреференцеинфо](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) , чтобы указать, какие поля структуры [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) должны быть инициализированы.

Используется для `dwFields` элемента `DEBUG_REFERENCE_INFO` структуры, чтобы указать, какие поля используются и допустимы при возврате структуры.

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
