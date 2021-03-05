---
description: Задает значение этого свойства и при необходимости возвращает сообщение об ошибке.
title: 'IDebugProperty3:: Сетвалуеасстрингвисеррор | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::SetValueAsStringWithError
helpviewer_keywords:
- IDebugProperty3::SetValueAsStringWithError
ms.assetid: b378368f-4a45-4b2f-8e3d-3bff7a18ab17
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd789561a85f23cff2ec794d4877662441f9149e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168105"
---
# <a name="idebugproperty3setvalueasstringwitherror"></a>IDebugProperty3::SetValueAsStringWithError
Задает значение этого свойства и при необходимости возвращает сообщение об ошибке.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetValueAsStringWithError(
    LPCOLESTR pszValue,
    DWORD     dwRadix,
    DWORD     dwTimeout,
    BSTR*     errorString
);
```

```csharp
int SetValueAsStringWithError(
    string     pszValue,
    uint       dwRadix,
    uint       dwTimeout,
    out string errorString
);
```

## <a name="parameters"></a>Параметры
`pszValue`\
окне Заданное значение.

`dwRadix`\
окне Основание для установки значения.

`dwTimeout`\
окне Интервал времени ожидания установки значения ( `INFINITE` означает, что ожидание бесконечно).

`errorString`\
заполняет Если при установке этого значения произошла ошибка, это содержит причину сбоя.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
Входящее значение может быть вычисляемым выражением.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **кпроперти** , предоставляющего интерфейс [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) .

```cpp
HRESULT CProperty::SetValueAsStringWithError(
    LPCOLESTR in_szValue,
    DWORD in_RADIX,
    DWORD in_TIMEOUT,
    BSTR * out_ERRORTEXT
)
{
    // precondition
    REQUIRE( NULL != in_szValue );

    if (NULL == in_szValue)
        return E_INVALIDARG;

    INVARIANT( this );
    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    if (NULL == m_pPropertyContext->m_pCEE->m_LanguageSpecificUseCases.pfSetValue)
        return S_OK;

    // function body
    DEBUG_PROPERTY_INFO dpInfo,dpInfo2;
    HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_FULLNAME | DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_TYPE | DEBUGPROP_INFO_VALUE_AUTOEXPAND,
                                       in_RADIX,
                                       in_TIMEOUT,
                                       NULL,
                                       0,
                                       &dpInfo);

    if (ENSURE( S_OK == HR ))
    {
        REQUIRE( NULL != dpInfo.bstrFullName );
        REQUIRE( NULL != dpInfo.bstrType );

        REQUIRE( NULL == dpInfo.bstrName );
        REQUIRE( NULL == dpInfo.bstrValue );
        REQUIRE( NULL == dpInfo.pProperty );

        BSTR bstrError = NULL;

        UINT ichError = 0;
        IDebugProperty2* pProperty = NULL;
        IDebugParsedExpression* pParsedExpression = NULL;

        CComBSTR bstrValue = dpInfo.bstrFullName;
        bstrValue += L" = ";
        bstrValue += in_szValue;
        HR = this->m_pPropertyContext->m_pCEE->
                Parse(bstrValue, 0, in_RADIX, &bstrError, &ichError, &pParsedExpression);
        if (S_OK == HR)
        {
            REQUIRE( NULL == bstrError );
            HR = pParsedExpression->EvaluateSync(EVAL_NOEVENTS | EVAL_RETURNVALUE,
                                                 in_TIMEOUT,
                                                 m_pPropertyContext->m_pSymbolProvider,
                                                 m_pPropertyContext->m_pAddress,
                                                 m_pPropertyContext->m_pBinder,
                                                 NULL,
                                                 &pProperty);

            dpInfo2.dwAttrib = DBG_ATTRIB_VALUE_ERROR;
            if (pProperty)
            {
                pProperty->GetPropertyInfo(DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_VALUE,10,in_TIMEOUT,NULL,0,&dpInfo2);
            }
            if (DBG_ATTRIB_VALUE_ERROR & dpInfo2.dwAttrib)
            {
                HR = E_FAIL;
                bstrError = dpInfo2.bstrValue;
            }
            else
            {
                ::SysFreeString(dpInfo.bstrValue);
            }
            EXTERNAL_RELEASE(pProperty);
            EXTERNAL_RELEASE(pParsedExpression);
        }

        if (bstrError)
        {
            if(out_ERRORTEXT)
            {
                *out_ERRORTEXT = bstrError;
                bstrError = NULL;
            }
            else
            {
                ::SysFreeString(bstrError);
            }
        }
        ::SysFreeString(dpInfo.bstrFullName);
        ::SysFreeString(dpInfo.bstrType);
    }

    // postcondition
    INVARIANT( this );

    return HR;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
