---
description: Перечисляет допустимые значения флагов, управляющих вычислением выражений.
title: EVALFLAGS90 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e75b938f45df5d4fa91bec4b59964dfc6a54e5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095931"
---
# <a name="evalflags90"></a>EVALFLAGS90
Перечисляет допустимые значения флагов, управляющих вычислением выражений. Это перечисление расширяет перечисление [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) .

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Поля
`EVAL90_RETURNVALUE`\
Указывает, что должно быть вычислено возвращаемое значение, если оно имеется.

`EVAL90_NOSIDEEFFECTS`\
Указывает, что побочные эффекты не допускаются.

`EVAL90_ALLOWBPS`\
Задает остановку в точках останова.

`EVAL90_ALLOWERRORREPORT`\
Указывает, что сообщение об ошибке должно быть разрешено узлу. В основном используется для вычисления выражений в скрипте в Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Заставляет функции оцениваться как адреса, а не вызывать функцию.

`EVAL90_NOFUNCEVAL`\
Предотвращает вычисление функции. Например, рассмотрим `int` маркер в выражении `myExpression(int) + 10` . Эта функция может быть правильно оценена как адрес, но не как значение.

`EVAL90_NOEVENTS`\
Флаг, указывающий, что события, происходящие во время оценки выражения, не должны отправляться в Диспетчер отладки сеанса (SDM) или в интегрированную среду разработки.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Включает вычисление выражений во время разработки.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Позволяет создавать неявные переменные.

`EVAL90_FORCE_EVALUATION_NOW`\
Приводит к немедленному выполнению оценки. Это полезно при обслуживании запроса, например запроса пользователя.

## <a name="requirements"></a>Требования
Заголовок: Msdbg90. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
