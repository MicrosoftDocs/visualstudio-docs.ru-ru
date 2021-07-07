---
title: Пример реализации вычисления выражений | Документация Майкрософт
description: Узнайте, как Visual Studio вызывает ParseText и создает объект IDebugExpression2 для выражения окна контрольных значений.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de0e052fd42f1603889f7521a1e45e50b0f36eea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902310"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Пример реализации вычисления выражений
> [!IMPORTANT]
> В Visual Studio 2015 такая реализация вычислителя выражений была сделана нерекомендуемой. Сведения о реализации вычислителей выражений в среде CLR см. на страницах [CLR expression evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) (Вычислители выражений CLR) и [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample) (Пример управляемого вычислителя выражений).

 Для выражения окна **Контрольных значений** Visual Studio вызывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md), чтобы создать объект [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md). `IDebugExpressionContext2::ParseText` создает экземпляр вычислителя выражений и вызывает метод [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), чтобы получить объект [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md).

 Метод `IDebugExpressionEvaluator::Parse` выполняет следующие задачи:

1. [только C++] анализирует выражение на наличие ошибок;

2. создает экземпляр класса (в этом примере называемого `CParsedExpression`), который использует интерфейс `IDebugParsedExpression` и сохраняет в классе выражение для анализа;

3. возвращает интерфейс `IDebugParsedExpression` из объекта `CParsedExpression`.

> [!NOTE]
> В следующих примерах и в примере MyCEE вычислитель выражений не разделяет вычисление и анализ.

## <a name="managed-code"></a>Управляемый код
 Ниже показана реализация `IDebugExpressionEvaluator::Parse` в управляемом коде. Эта версия метода передает задачу анализа методу [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md), так как код анализа выполняется одновременно (см. [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Неуправляемый код
Ниже показана реализация `IDebugExpressionEvaluator::Parse` в неуправляемом коде. Этот метод вызывает вспомогательную функцию `Parse` для анализа выражения и проверки наличия ошибок, однако он игнорирует результирующее значение. Формальное вычисление передается методу [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md), в котором выражение анализируется во время вычисления (см. [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>См. также
- [Вычисление выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)
