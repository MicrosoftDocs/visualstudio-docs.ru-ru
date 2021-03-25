---
description: 'IDebugComPlusSymbolProvider2:: Жеттипефромтокен Извлекает тип с учетом его токена.'
title: 'IDebugComPlusSymbolProvider2:: Жеттипефромтокен | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::GetTypeFromToken
- GetTypeFromToken
ms.assetid: 4452bc5d-0225-40e0-a467-c472a5c7c4ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f4bcc8d92cc58a719e9b450ec79e8376de554ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077984"
---
# <a name="idebugcomplussymbolprovider2gettypefromtoken"></a>IDebugComPlusSymbolProvider2::GetTypeFromToken
Извлекает тип с учетом его токена.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetTypeFromToken(
    ULONG32       appDomain,
    GUID          guidModule,
    DWORD         tdToken,
    IDebugField** ppField
);
```

```csharp
int GetTypeFromToken(
    uint            appDomain,
    Guid            guidModule,
    uint            tdToken,
    out IDebugField ppField
);
```

## <a name="parameters"></a>Параметры
`appDomain`\
окне Идентификатор домена приложения.

`guidModule`\
окне Уникальный идентификатор модуля.

`tdToken`\
окне Токен извлекаемого типа.

`ppField`\
заполняет Возвращает тип, представленный [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **кдебугсимболпровидер** , предоставляющего интерфейс [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) .

```cpp
HRESULT CDebugSymbolProvider::GetTypeFromToken(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    DWORD tdToken,
    IDebugField **ppField)
{
    HRESULT hr = E_FAIL;

    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromToken );

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppField, IDebugField*));

    Module_ID idModule(ulAppDomainID, guidModule);

    IfFailGo( this->CreateClassType(idModule, tdToken, ppField) );

Error:

    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromToken, hr );

    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
