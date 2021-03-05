---
description: Сопоставляет расположение документа в указанном модуле с массивом адресов отладки.
title: IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAddressesInModuleFromPosition
- IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
ms.assetid: f901c66e-f53c-4ea0-8004-d8fcbf46f916
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0397e8cc78fbff56d2fd538ca7dcfd5f962392dc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163919"
---
# <a name="idebugcomplussymbolprovidergetaddressesinmodulefromposition"></a>IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
Сопоставляет расположение документа в указанном модуле с массивом адресов отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAddressesInModuleFromPosition(
   ULONG32                  ulAppDomainID,
   GUID                     guidModule,
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesInModuleFromPosition(
   uint                    ulAppDomainID,
   Guid                    guidModule,
   IDebugDocumentPosition2 pDocPos,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Параметры
`ulAppDomainID`\
окне Идентификатор домена приложения.

`guidModule`\
окне Уникальный идентификатор модуля.

`pDocPos`\
окне Расположение документа.

`fStatmentOnly`\
окне Если `TRUE` значение равно, адреса отладки ограничиваются одной инструкцией.

`ppEnumBegAddresses`\
заполняет Возвращает перечислитель для начальных адресов отладки, связанных с данной инструкцией или строкой.

`ppEnumEndAddresses`\
заполняет Возвращает перечислитель для конечных адресов отладки, связанных с данной инструкцией или строкой.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
 В следующем примере показано, как реализовать этот метод для объекта **кдебугсимболпровидер** , предоставляющего интерфейс [идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .

```cpp
HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPosition(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IDebugDocumentPosition2* pDocPos,
    BOOL fStatementOnly,
    IEnumDebugAddresses** ppEnumBegAddresses,
    IEnumDebugAddresses** ppEnumEndAddresses
)
{
    GUID guidNULL = {0};

    if (guidNULL == guidModule)
    {
        return GetAddressesInAppDomainFromPosition( ulAppDomainID,
                pDocPos,
                fStatementOnly,
                ppEnumBegAddresses,
                ppEnumEndAddresses );
    }
    else
    {
        return GetAddressesInModuleFromPositionHelper( ulAppDomainID,
                guidModule,
                pDocPos,
                fStatementOnly,
                ppEnumBegAddresses,
                ppEnumEndAddresses );
    }
}

HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IDebugDocumentPosition2* pDocPos,
    BOOL fStatementOnly,
    IEnumDebugAddresses** ppEnumBegAddresses,
    IEnumDebugAddresses** ppEnumEndAddresses
)
{
    HRESULT hr = S_OK;
    CComBSTR bstrFileName;
    TEXT_POSITION posBeg;
    TEXT_POSITION posEnd;
    DWORD dwLine;
    USHORT segRet = 0;
    ULONG offRet = 0;
    CAddrList listAddr;
    CAddrList listAddrEnd;
    CAddrList* plistAddrEnd = NULL;
    bool fFileFound = false;
    Module_ID idModule(ulAppDomainID, guidModule);
    DWORD dwListCount;
    bool fFoundAddresses = false;
    CComPtr<CModule> pmodule;
    DWORD dwBegCol = 0;
    DWORD dwEndCol = 0;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pDocPos, IDebugDocumentPosition2));
    ASSERT(IsValidWritePtr(ppEnumBegAddresses, IEnumDebugAddresses*));

    METHOD_ENTRY(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper);

    // Bail on Invalid Args

    IfFalseGo( pDocPos && ppEnumBegAddresses, E_INVALIDARG );

    *ppEnumBegAddresses = NULL;
    if (ppEnumEndAddresses)
    {
        *ppEnumEndAddresses = NULL;
        plistAddrEnd = &listAddrEnd;
    }

    // Get the Position

    IfFailGo( pDocPos->GetFileName(&bstrFileName) );
    IfFailGo( pDocPos->GetRange(&posBeg, &posEnd) );

    // Iterate over the module list accumulating addresses
    // that match the position

    dwLine = posBeg.dwLine;
    IfFailGo( GetModule( idModule, &pmodule ) );
    dwListCount = listAddr.GetCount();

    if ( fStatementOnly )
    {
        dwBegCol = posBeg.dwColumn;
        dwEndCol = posBeg.dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);
    }
    else
    {
        dwBegCol = 0;
        dwEndCol = DWORD( -1);
    }

    while (!fFoundAddresses && dwLine <= posEnd.dwLine )
    {
        hr = pmodule->GetAddressesFromLine( bstrFileName,
                                            dwLine,
                                            posEnd.dwLine,
                                            dwBegCol,
                                            dwEndCol,
                                            &listAddr,
                                            plistAddrEnd );

        dwLine++;
        dwBegCol = 0;
        dwEndCol = dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);

        if (hr == E_SH_INVALID_POSITION)
        {
            fFileFound = true;
            break;
        }

        if (FAILED(hr))
        {
            // Move on to the next module
            break;
        }

        fFileFound = true;
        fFoundAddresses = listAddr.GetCount() != dwListCount;
    }

    // Distinguish no file from bad position in the file
    IfFalseGo( fFileFound, E_SH_FILE_NOT_FOUND);

    // If the list is empty the position is bad
    IfFalseGo( listAddr.GetCount(), E_SH_INVALID_POSITION );

    // Create enumerators
    IfFailGo( CreateEnumerator( ppEnumBegAddresses, &listAddr ) );
    if (ppEnumEndAddresses)
    {
        IfFailGo( CreateEnumerator( ppEnumEndAddresses, &listAddrEnd ) );
    }

Error:

    METHOD_EXIT(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper, hr);

    return hr;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
