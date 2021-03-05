---
description: Выбирает различные типы конструкторов.
title: CONSTRUCTOR_ENUM | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e3a8eaae37b304c438c18ec2a683c19da00ab16
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170800"
---
# <a name="constructor_enum"></a>CONSTRUCTOR_ENUM
Выбирает различные типы конструкторов.

## <a name="syntax"></a>Синтаксис

```cpp
typedef enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
} CONSTRUCTOR_ENUM;
```

```csharp
public enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
};
```

## <a name="fields"></a>Поля
`crAll`\
Выбирает все конструкторы.

`crNonStatic`\
Выбирает нестатические конструкторы.

`crStatic`\
Выбирает статические конструкторы.

## <a name="remarks"></a>Комментарии
Передается в качестве аргумента в метод [енумконструкторс](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) .

## <a name="requirements"></a>Требования
Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
