---
description: Выгружает отладочные символы для указанного модуля из памяти.
title: 'Идебугкомплуссимболпровидер:: Унлоадсимболс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- UnloadSymbols
- IDebugComPlusSymbolProvider::UnloadSymbols
ms.assetid: 53e3ddc1-ab47-4097-8fef-b26e5504b37a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 529e25d99152b18e3b12aad612ad3162c2fc9008
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163568"
---
# <a name="idebugcomplussymbolproviderunloadsymbols"></a>IDebugComPlusSymbolProvider::UnloadSymbols
Выгружает отладочные символы для указанного модуля из памяти.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int UnloadSymbols(
    uint ulAppDomainID,
    Guid guidModule
);
```

## <a name="parameters"></a>Параметры
`ulAppDomainID`\
окне Идентификатор домена приложения.

`guidModule`\
окне Уникальный идентификатор модуля.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **кдебугсимболпровидер** , предоставляющего интерфейс [идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .

```cpp
HRESULT CDebugSymbolProvider::UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pmodule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::UnloadSymbols );

#if DEBUG

    DebugVerifyModules();
#endif

    IfFailGo( GetModule( idModule, &pmodule ) );

#if DEBUG

    DebugVerifyModules();
#endif

    RemoveModule( pmodule );
    pmodule->Cleanup();

Error:
#if DEBUG

    DebugVerifyModules();
#endif

    METHOD_EXIT( CDebugSymbolProvider::UnloadSymbols, hr );

    return hr;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
