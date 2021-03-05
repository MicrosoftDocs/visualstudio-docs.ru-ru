---
description: Перечисляет допустимые значения флагов удаления программы.
title: PROGRAM_DESTROY_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PROGRAM_DESTROY_FLAGS enumeration
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a695ae921bb9fb0e6b137e258cd8bd70d278eba7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225322"
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

## <a name="remarks"></a>Комментарии
 Перечисление возвращается методом- [flags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md) .

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)
