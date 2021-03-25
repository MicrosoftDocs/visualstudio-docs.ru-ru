---
description: Эта структура представляет собственный адрес.
title: NATIVE_ADDRESS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NATIVE_ADDRESS
helpviewer_keywords:
- NATIVE_ADDRESS structure
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 799120bf3a068ccbc7eebad729b4312d6715af34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086473"
---
# <a name="native_address"></a>NATIVE_ADDRESS

Эта структура представляет собственный адрес.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagNATIVE_ADDRESS {
    DWORD unknown;
} NATIVE_ADDRESS;
```

```csharp
public struct NATIVE_ADDRESS {
    public uint unknown;
}
```

## <a name="members"></a>Участники

`unknown`\
Собственный адрес (значение этого параметра зависит от среды выполнения и операционной системы).

## <a name="remarks"></a>Remarks

Эта структура является частью объединения в структуре [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , если `dwKind` поле `DEBUG_ADDRESS_UNION` структуры имеет `ADDRESS_KIND_NATIVE` значение (Value из перечисления [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Требования

Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
