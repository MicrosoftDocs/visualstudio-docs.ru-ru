---
description: Извлекает настраиваемый атрибут по его имени.
title: 'Идебугкустоматтрибутекуери:: Жеткустоматтрибутебинаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery::GetCustomAttributeByName
- GetCustomAttributeByName
ms.assetid: 6779727c-d10a-4abe-9acd-d0a1eb0737e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7168eea4ddefa85ded7ab3b3c18b9d647a054b99
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154487"
---
# <a name="idebugcustomattributequerygetcustomattributebyname"></a>IDebugCustomAttributeQuery::GetCustomAttributeByName
Извлекает настраиваемый атрибут по его имени.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCustomAttributeByName(
    LPCOLESTR pszCustomAttributeName,
    BYTE*     ppBlob,
    DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
    string    pszCustomAttributeName,
    ref int[] ppBlob,
    out uint  pdwLen
);
```

## <a name="parameters"></a>Параметры
`pszCustomAttributeName`\
окне Имя настраиваемого атрибута.

`ppBlob`\
[вход, выход] Массив байтов, содержащих данные настраиваемых атрибутов.

`pdwLen`\
заполняет Длина параметра в байтах `ppBlob` .

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK`. Если пользовательский атрибут не существует, возвращает значение `S_FALSE` . В противном случае возвращается код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **кдебугклассфиелдсимбол** , предоставляющего интерфейс [идебугкустоматтрибутекуери](../../../extensibility/debugger/reference/idebugcustomattributequery.md) .

```cpp
HRESULT CDebugClassFieldSymbol::GetCustomAttributeByName(
    LPCOLESTR pszCustomAttributeName,
    BYTE *pBlob,
    DWORD *pdwLen
)
{
    HRESULT hr = S_FALSE;
    CComPtr<IMetaDataImport> pMetadata;
    mdToken token = mdTokenNil;
    CComPtr<IDebugField> pField;
    CComPtr<IDebugCustomAttributeQuery> pCA;

    ASSERT(IsValidWideStringPtr(pszCustomAttributeName));
    ASSERT(IsValidWritePtr(pdwLen, ULONG*));

    METHOD_ENTRY( CDebugClassFieldSymbol::GetCustomAttributeByName );

    IfFalseGo( pszCustomAttributeName && pdwLen, E_INVALIDARG );

    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );

    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );
    IfFailGo( CDebugCustomAttribute::GetCustomAttributeByName( pMetadata,
              token,
              pszCustomAttributeName,
              pBlob,
              pdwLen ) );
Error:

    METHOD_EXIT( CDebugClassFieldSymbol::GetCustomAttributeByName, hr );
    return hr;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)
