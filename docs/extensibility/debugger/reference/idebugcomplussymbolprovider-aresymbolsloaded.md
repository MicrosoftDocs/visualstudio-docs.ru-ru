---
description: Определяет, загружаются ли отладочные символы для указанного модуля по заданному идентификатору домена приложения.
title: 'Идебугкомплуссимболпровидер:: Аресимболслоадед | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 567a0906544a28c2f145e8b4361045b56b6f9278
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088306"
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
Определяет, загружаются ли отладочные символы для указанного модуля по заданному идентификатору домена приложения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT AreSymbolsLoaded (
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int AreSymbolsLoaded (
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
Если отладочные символы загружены, возвращает `S_OK` ; в противном случае возвращает `S_FALSE` .

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **кдебугсимболпровидер** , предоставляющего интерфейс [идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .

```cpp
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );

    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );
Error:

    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );
    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
