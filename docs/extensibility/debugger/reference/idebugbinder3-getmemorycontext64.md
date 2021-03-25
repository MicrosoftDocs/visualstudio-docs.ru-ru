---
description: Преобразует расположение объекта или адрес 64-разрядной памяти в контекст памяти.
title: 'IDebugBinder3:: GetMemoryContext64 | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetMemoryContext64
- IDebugBinder3::GetMemoryContext64
ms.assetid: f021fd16-9fc7-4c41-86af-e54e6224cfbb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 263d50a0c9f3f9b2ab0aa74a05647abc1930970c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094228"
---
# <a name="idebugbinder3getmemorycontext64"></a>IDebugBinder3::GetMemoryContext64
Преобразует расположение объекта или адрес 64-разрядной памяти в контекст памяти.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMemoryContext64 (
    IDebugField*           pField,
    UINT64                 uConstant,
    IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext64 (
    IDebugField              pField,
    ulong                    uConstant,
    out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Параметры
`pField`\
окне Объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , описывающий объект для размещения. Если значение равно `NULL` , используйте `dwConstant` вместо него.

`uConstant`\
окне 64-разрядный адрес памяти, например 0x50000000.

`ppMemCxt`\
заполняет Возвращает интерфейс [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , представляющий адрес объекта или адрес в памяти.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующих примерах создается объект, реализующий интерфейс [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md) , который использует этот метод для получения контекста памяти.

```cpp
HRESULT CValueProperty::GetMemoryContext ( IDebugMemoryContext2** out_ppMemoryContext )
{
    // precondition
    REQUIRE( NULL != out_ppMemoryContext );

    if (NULL == out_ppMemoryContext)
        return E_POINTER;

    *out_ppMemoryContext = NULL;

    INVARIANT( this );

    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    if (VT_EMPTY == this->m_VarValue.vt)
    {
        return E_FAIL;
    }

    // function body
    if (NULL != this->m_pBinder)
    {
        UINT64 dwOffset = 0;

        DEBUG_PROPERTY_INFO dpInfo;
        HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_VALUE,
                                           10, // RADIX
                                           DEFAULT_TIMEOUT,
                                           NULL,
                                           0,
                                           &dpInfo);
        if (ENSURE( S_OK == HR ))
        {
            REQUIRE( NULL != dpInfo.bstrValue );
            REQUIRE( NULL == dpInfo.bstrName );
            REQUIRE( NULL == dpInfo.bstrFullName );
            REQUIRE( NULL == dpInfo.bstrType );
            REQUIRE( NULL == dpInfo.pProperty );

            wchar_t * end;
            dwOffset = _wcstoui64(dpInfo.bstrValue, &end, 0); // base 0 to allow 0x if it's ever output
            ::SysFreeString(dpInfo.bstrValue);
        }

        if (CComQIPtr<IDebugBinder3> binder3 = this->m_pBinder)
            HR = binder3->GetMemoryContext64(NULL, dwOffset, out_ppMemoryContext);
        else
            HR = this->m_pBinder->GetMemoryContext(NULL, (DWORD)(__int32)dwOffset, out_ppMemoryContext);

        if (ENSURE( S_OK == HR ))
        {
            REQUIRE( NULL != *out_ppMemoryContext );
        }
    }

    // postcondition
    INVARIANT( this );

    HRESULT HR = E_FAIL;

    if (NULL != *out_ppMemoryContext)
    {
        HR = S_OK;
    }

    return HR;
}
```

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
