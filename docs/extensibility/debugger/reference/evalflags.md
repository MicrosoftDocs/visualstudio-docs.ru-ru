---
description: Задает флаги, управляющие вычислением выражений.
title: ЕВАЛФЛАГС | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bcf68b95bb905d41aaab906603cd4dd248e52ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095944"
---
# <a name="evalflags"></a>EVALFLAGS
Задает флаги, управляющие вычислением выражений.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Поля
`EVAL_RETURNVALUE`\
Указывает, что должно быть вычислено возвращаемое значение, если оно имеется.

`EVAL_NOSIDEEFFECTS`\
Указывает, что побочные эффекты не допускаются.

`EVAL_ALLOWBPS`\
Задает остановку в точках останова.

`EVAL_ALLOWERRORREPORT`\
Указывает, что сообщение об ошибках должно быть разрешено узлу. В основном используется для вычисления выражений в скрипте в Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Заставляет функции оцениваться как адреса, а не вызывать функцию.

`EVAL_NOFUNCEVAL`\
Предотвращает вычисление функции. Например, рассмотрим `int` маркер в выражении `myExpression(int) + 10` . Эта функция может быть правильно оценена как адрес, но не как значение.

`EVAL_NOEVENTS`\
Флаг, указывающий, что события, происходящие во время оценки выражения, не должны отправляться в Диспетчер отладки сеанса (SDM) или в интегрированную среду разработки.

## <a name="remarks"></a>Remarks
Эти флаги передаются в качестве аргумента методам [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) и [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .

Эти флаги можно сочетать с помощью побитового или.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
