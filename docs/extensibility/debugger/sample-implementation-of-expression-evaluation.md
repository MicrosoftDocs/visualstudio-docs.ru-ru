---
title: Пример реализации вычисления выражения | Документация Майкрософт
description: Узнайте, как Visual Studio вызывает Парсетекст для создания объекта IDebugExpression2 для выражения "Watch Windows".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 60d01917bb3a21f6d8ea2644fbeef2b22064cc00
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070457"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Пример реализации вычисления выражений
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Для выражения окна **контрольных значений** Visual Studio вызывает [парсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания объекта [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` создает экземпляр средства оценки выражений (EE) и вызывает метод [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для получения объекта [идебугпарседекспрессион](../../extensibility/debugger/reference/idebugparsedexpression.md) .

 `IDebugExpressionEvaluator::Parse`Выполняет следующие задачи:

1. [Только C++] Анализирует выражение для поиска ошибок.

2. Создает экземпляр класса (вызываемого `CParsedExpression` в этом примере), который запускает `IDebugParsedExpression` интерфейс и сохраняет в классе анализируемое выражение.

3. Возвращает `IDebugParsedExpression` интерфейс из `CParsedExpression` объекта.

> [!NOTE]
> В примерах ниже и в образце Мицее средство оценки выражений не отделяет анализ от оценки.

## <a name="managed-code"></a>Управляемый код
 В следующем коде показана реализация `IDebugExpressionEvaluator::Parse` в управляемом коде. Эта версия метода откладывает анализ на [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , так как код для синтаксического анализа также вычисляется одновременно (см. статью [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
Следующий код является реализацией `IDebugExpressionEvaluator::Parse` в неуправляемом коде. Этот метод вызывает вспомогательную функцию, `Parse` для синтаксического анализа выражения и проверки на наличие ошибок, но этот метод игнорирует результирующее значение. Формальное вычисление откладывается до [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , где выражение анализируется при его вычислении (см. статью [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
- [Вычисление выражения окно контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)
