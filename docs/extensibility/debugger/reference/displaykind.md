---
description: Перечисляет допустимые значения, представляющие типы данных, которые необходимо взять из объекта Идебугфиелд и отобразить пользователю.
title: Дисплайкинд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8c474c9295ceedbdffd286e99975c375ea69fc4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096035"
---
# <a name="displaykind"></a>DisplayKind
Перечисляет допустимые значения, представляющие типы данных, которые необходимо взять из объекта [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) и отобразить пользователю.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
typedef DWORD DisplayKind;
```

```csharp
public enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
```

## <a name="fields"></a>Поля
`DisplayKind_Value`\
Значение поля.

`DisplayKind_Name`\
Имя поля.

`DisplayKind_Type`\
Тип поля.

## <a name="requirements"></a>Требования
Заголовок: ee. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)
