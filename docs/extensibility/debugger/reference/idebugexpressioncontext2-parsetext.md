---
description: Анализирует выражение в текстовой форме для последующей оценки.
title: IDebugExpressionContext2::P Арсетекст | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2095a1d6e035c676ab92722f9ae785e1a42c5b78
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152643"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Анализирует выражение в текстовой форме для последующей оценки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>Параметры
`pszCode`\
окне Выражение для синтаксического анализа.

`dwFlags`\
окне Сочетание флагов из перечисления [парсефлагс](../../../extensibility/debugger/reference/parseflags.md) , которое управляет синтаксическим анализом.

`nRadix`\
окне Основание системы счисления, используемое при анализе любой числовой информации в `pszCode` .

`ppExpr`\
заполняет Возвращает объект [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , представляющий проанализированное выражение, которое готово для привязки и оценки.

`pbstrError`\
заполняет Возвращает сообщение об ошибке, если выражение содержит ошибку.

`pichError`\
заполняет Возвращает индекс символа ошибки в `pszCode` случае, если выражение содержит ошибку.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
При вызове этого метода модуль отладки (DE) должен проанализировать выражение и проверить его на правильность. `pbstrError`Параметры и `pichError` могут быть заполнены, если выражение является недопустимым.

Обратите внимание, что выражение не вычисляется, только анализируется. Последующий вызов методов [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) оценивает проанализированное выражение.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CEnvBlock` объекта, предоставляющего интерфейс [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Этот пример считает, что выражение анализируется как имя переменной среды и получает значение из этой переменной.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
