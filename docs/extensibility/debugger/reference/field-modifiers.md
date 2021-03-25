---
description: Задает модификаторы для типа поля.
title: FIELD_MODIFIERS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 55f493280808f0b68089a9d72c4184585d386b18
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059383"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Задает модификаторы для типа поля.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>Поля
`FIELD_MOD_ACCESS_TYPE`\
Указывает, что доступ к полю невозможен.

`FIELD_MOD_ACCESS_PUBLIC`\
Указывает, что поле имеет открытый доступ.

`FIELD_MOD_ACCESS_PROTECTED`\
Указывает, что поле имеет защищенный доступ.

`FIELD_MOD_ACCESS_PRIVATE`\
Указывает, что поле имеет закрытый доступ.

`FIELD_MOD_NOMODIFIERS`\
Указывает, что поле не имеет модификаторов.

`FIELD_MOD_STATIC`\
Указывает, что поле является статическим.

`FIELD_MOD_CONSTANT`\
Указывает, что поле является константой.

`FIELD_MOD_TRANSIENT`\
Указывает, что поле является временным.

`FIELD_MOD_VOLATILE`\
Указывает, что поле является временным.

`FIELD_MOD_ABSTRACT`\
Указывает, что поле является абстрактным.

`FIELD_MOD_NATIVE`\
Указывает, что поле является машинным.

`FIELD_MOD_SYNCHRONIZED`\
Указывает, что поле синхронизировано.

`FIELD_MOD_VIRTUAL`\
Указывает, что поле является виртуальным.

`FIELD_MOD_INTERFACE`\
Указывает, что поле является интерфейсом.

`FIELD_MOD_FINAL`\
Указывает, что поле является окончательным.

`FIELD_MOD_SENTINEL`\
Указывает, что поле является Sentinel.

`FIELD_MOD_INNERCLASS`\
Указывает, что поле является внутренним классом.

`FIELD_TYPE_OPTIONAL`\
Указывает, что поле является необязательным.

`FIELD_MOD_BYREF`\
Указывает, что поле является ссылочным аргументом. Это конкретно для аргументов метода.

`FIELD_MOD_HIDDEN`\
Указывает, что поле должно быть скрыто или представлено в другом контексте. Например, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] Статические локальные переменные.

`FIELD_MOD_MARSHALASOBJECT`\
Указывает, что поле представляет объект с `IUnknown` интерфейсом.

`FIELD_MOD_SPECIAL_NAME`\
Указывает, что поле имеет специальное имя, например, `.ctor` для конструктора ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] только).

`FIELD_MOD_HIDEBYSIG`\
Указывает, что к полю `Overloads` применено ключевое слово ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] только).

`FIELD_MOD_WRITEONLY`\
Указывает, что поле доступно только на запись. Это значение не включено в `FIELD_MOD_ALL` , так как только такие поля только для записи используются для вычисления функции. Пользователь должен явно запрашивать `FIELD_MOD_WRITEONLY` поля.

`FIELD_MOD_ACCESS_MASK`\
Указывает маску доступа к полю.

`FIELD_MOD_MASK`\
Указывает маску для модификаторов полей.

## <a name="remarks"></a>Remarks
Используется для `dwModifiers` элемента структуры [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

Эти значения также передаются методу [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) для фильтрации конкретных полей.

## <a name="requirements"></a>Требования
Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
