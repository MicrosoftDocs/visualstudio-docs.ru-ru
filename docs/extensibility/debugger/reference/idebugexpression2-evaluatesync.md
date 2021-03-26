---
description: Этот метод выполняет асинхронное вычисление выражения.
title: 'IDebugExpression2:: Евалуатесинк | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 85e0dd1c334ce57b5e466ab66a74db4b29a40adc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092440"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Этот метод выполняет асинхронное вычисление выражения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EvaluateSync(
    EVALFLAGS             dwFlags,
    DWORD                 dwTimeout,
    IDebugEventCallback2* pExprCallback,
    IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
    enum_EVALFLAGS       dwFlags,
    uint                 dwTimeout,
    IDebugEventCallback2 pExprCallback,
    out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Параметры
`dwFlags`\
окне Сочетание флагов из перечисления [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) , которое управляет вычислением выражений.

`dwTimeout`\
окне Максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.

`pExprCallback`\
окне Этот параметр всегда имеет значение null.

`ppResult`\
заполняет Возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , содержащий результат вычисления выражения.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Ниже приведены некоторые типичные коды ошибок.

|Ошибка|Описание|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|В настоящее время выполняется вычисление другого выражения, и одновременная Оценка выражений не поддерживается.|
|E_EVALUATE_TIMEOUT|Время ожидания оценки истекло.|

## <a name="remarks"></a>Remarks
Для синхронной оценки нет необходимости отсылать событие обратно в Visual Studio после завершения оценки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CExpression` объекта, реализующего интерфейс [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) .

```cpp
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,
                                  DWORD dwTimeout,
                                  IDebugEventCallback2* pExprCallback,
                                  IDebugProperty2** ppResult)
{
    // Set the aborted state to FALSE.
    m_bAborted = FALSE;
    // Delegate the evaluation to EvalExpression.
    return EvalExpression(TRUE, ppResult);
}

HRESULT CExpression::EvalExpression(BOOL bSynchronous,
                                    IDebugProperty2** ppResult)
{
    HRESULT hr;

    // Get the value of an environment variable.
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);
    // Create and initialize a CEnvVar object with the retrieved value.
    // CEnvVar implements the IDebugProperty2 interface.
    CComObject<CEnvVar> *pEnvVar;
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);

    if (pszVal) {
        // Check for synchronous evaluation.
        if (bSynchronous) {
            // Set and AddRef the result, IDebugProperty2 interface.
            *ppResult = pEnvVar;
            (*ppResult)->AddRef();
            hr = S_OK;
        } else {
            //For asynchronous evaluation, send an evaluation complete event.
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);
        }
    } else {
        // If a valid value is not retrieved, return E_FAIL.
        hr = E_FAIL;
    }
    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
