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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7f58dd088b37d3f1a404677c6c76bb09160b438
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067599"
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

## <a name="remarks"></a>Remarks
Передается в качестве аргумента в метод [енумконструкторс](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) .

## <a name="requirements"></a>Требования
Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
