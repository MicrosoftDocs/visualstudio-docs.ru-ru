---
description: Перечисляет допустимые значения флагов удаления программы.
title: PROGRAM_DESTROY_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PROGRAM_DESTROY_FLAGS enumeration
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7abe750e76fa7cfcbecfd8b82853aeccbe543352
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079622"
---
# <a name="program_destroy_flags"></a>PROGRAM_DESTROY_FLAGS
Перечисляет допустимые значения флагов удаления программы.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PPROGRAM_DESTROY_FLAGS
{
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1
};
typedef DWORD PROGRAM_DESTROY_FLAGS;
```

```csharp
public enum enum_PPROGRAM_DESTROY_FLAGS
{
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1
};
```

## <a name="fields"></a>Поля
 `PROGRAM_DESTROY_CONTINUE_DEBUGGING`\
 Уничтожить программу, но продолжить отладку.

## <a name="remarks"></a>Remarks
 Перечисление возвращается методом- [flags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md) .

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)
