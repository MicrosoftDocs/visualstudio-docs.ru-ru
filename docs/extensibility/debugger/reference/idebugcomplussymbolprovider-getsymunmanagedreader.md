---
description: Возвращает средство чтения символов, используемое неуправляемым кодом.
title: 'Идебугкомплуссимболпровидер:: Жетсимунманажедреадер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetSymUnmanagedReader
- GetSymUnmanagedReader
ms.assetid: 8f1c1627-217f-4405-8141-7a2eb80310a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a650d55b6c3b36a5b3b08138f44618e2c3645627
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163802"
---
# <a name="idebugcomplussymbolprovidergetsymunmanagedreader"></a>IDebugComPlusSymbolProvider::GetSymUnmanagedReader
Возвращает средство чтения символов, используемое неуправляемым кодом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSymUnmanagedReader(
    ULONG32    ulAppDomainID,
    GUID       guidModule,
    IUnknown** ppSymUnmanagedReader
);
```

```csharp
int GetSymUnmanagedReader(
    uint       ulAppDomainID,
    Guid       guidModule,
    out object ppSymUnmanagedReader
);
```

## <a name="parameters"></a>Параметры
`ulAppDomainID`\
окне Идентификатор домена приложения.

`guidModule`\
окне Уникальный идентификатор модуля.

`ppSymUnmanagedReader`\
заполняет Возвращает объект, представляющий средство чтения символов.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **кдебугсимболпровидер** , предоставляющего интерфейс [идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .

```cpp
HRESULT CDebugSymbolProvider::GetSymUnmanagedReader(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IUnknown ** ppSymUnmanagedReader
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::GetSymUnmanagedReader );

    IfFailGo( GetModule( idModule, &pModule ) );
    IfFailGo( pModule->GetSymReader((ISymUnmanagedReader**) ppSymUnmanagedReader) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetSymUnmanagedReader, hr );
    return hr;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
