---
title: Вычисление выражения окна контрольных значений | Документация Майкрософт
description: Узнайте, как Visual Studio вызывает модуль отладки для определения текущего значения каждого выражения в его списке контрольных значений при приостановке выполнения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e72a89a6d3b51a328294d5bfa56e1699ead5498a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097075"
---
# <a name="evaluate-a-watch-window-expression"></a>Вычисление выражения окна контрольных значений
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Когда выполнение приостанавливается, Visual Studio вызывает модуль отладки (DE) для определения текущего значения каждого выражения в его списке контрольных значений. Параметр DE вычисляет каждое выражение с помощью средства оценки выражений (EE), а Visual Studio отображает его значение в окне **Контрольные** значения.

 Ниже приведены общие сведения о вычислении выражения списка контрольных значений.

1. Visual Studio вызывает [ЖЕТЕКСПРЕССИОНКОНТЕКСТ](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) de, чтобы получить контекст выражения, который можно использовать для вычисления выражений.

2. Для каждого выражения в списке Watch Visual Studio вызывает [парсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для преобразования текста выражения в проанализированное выражение.

3. `IDebugExpressionContext2::ParseText` вызывает метод [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для выполнения фактической работы по синтаксическому анализу текста и созданию объекта [идебугпарседекспрессион](../../extensibility/debugger/reference/idebugparsedexpression.md) .

4. `IDebugExpressionContext2::ParseText` Создает объект [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) и помещает в `IDebugParsedExpression` него объект. Затем этот `DebugExpression2` объект I возвращается в Visual Studio.

5. Visual Studio вызывает [евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для вычисления проанализированного выражения.

6. `IDebugExpression2::EvaluateSync` передает вызов [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) для выполнения фактической оценки и создания объекта [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , возвращаемого в Visual Studio.

7. Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для получения значения выражения, которое затем отображается в списке контрольных значений.

## <a name="parse-then-evaluate"></a>Затем проанализируйте
 Поскольку анализ сложного выражения может занять много времени, чем его вычисление, процесс вычисления выражения разбивается на два шага: 1) анализ выражения и 2) вычисление проанализированного выражения. Таким образом, вычисление может происходить много раз, но выражение должно быть проанализировано только один раз. Промежуточное проанализированное выражение возвращается из EE в объекте [идебугпарседекспрессион](../../extensibility/debugger/reference/idebugparsedexpression.md) , который в свою очередь инкапсулируется и возвращается из de в качестве объекта [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpression`Объект откладывает все вычисления на `IDebugParsedExpression` объект.

> [!NOTE]
> В EE нет необходимости соблюдать этот двухэтапный процесс, хотя в Visual Studio предполагается это. EE может анализироваться и оцениваться на том же этапе, когда вызывается [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (например, как работает образец мицее). Если язык может формировать сложные выражения, может потребоваться разделить шаг анализа на шаге оценки. Это может повысить производительность отладчика Visual Studio, когда отображается много контрольных выражений.

## <a name="in-this-section"></a>Содержание раздела
 [Пример реализации вычисления выражений](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Использует пример Мицее для пошагового выполнения процесса оценки выражений.

 [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md) Объясняет, что происходит после успешного синтаксического анализа выражения.

## <a name="related-sections"></a>Связанные разделы
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) Предоставляет аргументы, которые передаются, когда модуль отладки (DE) вызывает средство оценки выражений (EE).

## <a name="see-also"></a>См. также
 [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
