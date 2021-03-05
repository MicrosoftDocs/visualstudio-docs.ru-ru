---
description: Указывает тип шага для пошагового выполнения.
title: СТЕПКИНД | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9cb230eac9e8851437614a590615ad2402923f6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225296"
---
# <a name="stepkind"></a>STEPKIND
Указывает тип шага для пошагового выполнения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>Поля
 `STEP_INTO`\
 Шаги в функцию.

 `STEP_OVER`\
 Шаги над функцией.

 `STEP_OUT`\
 Выполнит шаги функции.

 `STEP_BACKWARDS`\
 Выполните шаги назад в функцию.

## <a name="remarks"></a>Комментарии
 Передается в качестве аргумента в метод [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
