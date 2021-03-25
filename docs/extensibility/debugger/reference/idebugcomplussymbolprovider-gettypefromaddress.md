---
description: Возвращает в символьный тип по заданному адресу отладки.
title: 'Идебугкомплуссимболпровидер:: Жеттипефромаддресс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetTypeFromAddress
- GetTypeFromAddress
ms.assetid: 01f21ff9-e8a5-4e5f-9f7b-1b6de8b1432f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3cde5d445551b83cc5497d3310bd5660842e9ffe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095606"
---
# <a name="idebugcomplussymbolprovidergettypefromaddress"></a>IDebugComPlusSymbolProvider::GetTypeFromAddress
Возвращает в символьный тип по заданному адресу отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetTypeFromAddress(
    IDebugAddress* pAddress,
    IDebugField**  ppField
);
```

```csharp
int GetTypeFromAddress(
    IDebugAddress   pAddress,
    out IDebugField ppField
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
окне Адрес отладки, представленный интерфейсом [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .

`ppField`\
заполняет Возвращает тип массива в том виде, в котором он представлен интерфейсом [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) .

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **кдебугсимболпровидер** , предоставляющего интерфейс [идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .

```cpp
HRESULT CDebugSymbolProvider::GetTypeFromAddress(
    IDebugAddress *pAddress,
    IDebugField **ppField)
{
    HRESULT hr = E_FAIL;
    CDEBUG_ADDRESS da;
    CDebugGenericParamScope* pGenScope = NULL;

    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromPrimitive );

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppField, IDebugField*));

    IfFailGo( pAddress->GetAddress(&da) );

    switch ( da.addr.dwKind )
    {
        case ADDRESS_KIND_METADATA_LOCAL:
        case ADDRESS_KIND_METADATA_PARAM:
        case ADDRESS_KIND_METADATA_FIELD:
        case ADDRESS_KIND_METADATA_ARRAYELEM:
        case ADDRESS_KIND_METADATA_METHOD:
            {
                IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );
                break;
            }

        case ADDRESS_KIND_METADATA_RETVAL:
            {
                if ( da.addr.addr.addrRetVal.dwCorType )
                {

                    IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );
                    IfFailGo( this->CreateType((const COR_SIGNATURE*)(&da.addr.addr.addrRetVal.rgSig),
                                               da.addr.addr.addrRetVal.dwSigSize,
                                               da.GetModule(),
                                               mdMethodDefNil,
                                               pGenScope,
                                               ppField) );
                }
                else
                {
                    IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );
                }

                break;
            }

        default:
            {
                ASSERT(!"Address type not supported.");
            }
    }

Error:

    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromPrimitive, hr );

    RELEASE( pGenScope );

    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
