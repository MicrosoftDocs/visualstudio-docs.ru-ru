---
title: Вычисление выражения контрольных значений | Документация Майкрософт
description: Узнайте, как Visual Studio использует Евалуатесинк, когда он готов к отображению значения выражения Watch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21a173a8c041bbaf12cb67bf90e1c4407ac5e4a7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097062"
---
# <a name="evaluate-a-watch-expression"></a>Вычисление выражения контрольных значений
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Когда Visual Studio будет готова отобразить значение выражения Watch, оно вызывает [евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), который, в свою очередь, вызывает [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Этот процесс создает объект [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , содержащий значение и тип выражения.

В этой реализации `IDebugParsedExpression::EvaluateSync` выражение анализируется и вычисляется в то же время. Эта реализация выполняет следующие задачи:

1. Анализирует и оценивает выражение для создания универсального объекта, содержащего значение и его тип. В C# это представляется как `object` время в C++, оно представлено как `VARIANT` .

2. Создает экземпляр класса (вызываемого `CValueProperty` в этом примере), который реализует `IDebugProperty2` интерфейс и сохраняет в классе возвращаемое значение.

3. Возвращает `IDebugProperty2` интерфейс из `CValueProperty` объекта.

## <a name="managed-code"></a>Управляемый код
Это реализация `IDebugParsedExpression::EvaluateSync` в управляемом коде. Вспомогательный метод `Tokenize` анализирует выражение в дереве синтаксического анализа. Вспомогательная функция `EvalToken` преобразует токен в значение. Вспомогательная функция `FindTerm` рекурсивно проходит по дереву синтаксического анализа, вызывая `EvalToken` для каждого узла, представляющего значение, и применяя любые операции (сложение или вычитание) в выражении.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>Неуправляемый код
Это реализация `IDebugParsedExpression::EvaluateSync` в неуправляемом коде. Вспомогательная функция `Evaluate` выполняет синтаксический анализ и вычисление выражения, возвращая объект, `VARIANT` содержащий результирующее значение. Вспомогательная функция `VariantValueToProperty` объединяет в `VARIANT` `CValueProperty` объект.

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>См. также
- [Вычисление выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Пример реализации вычисления выражений](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
