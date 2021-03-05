---
description: Этот метод возвращает поле, содержащее адрес отладки.
title: 'Идебугсимболпровидер:: Жетконтаинерфиелд | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetContainerField
helpviewer_keywords:
- IDebugSymbolProvider::GetContainerField method
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c86f3c7ce085b44b3b853736b6fed0f4363e59d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159657"
---
# <a name="idebugsymbolprovidergetcontainerfield"></a>IDebugSymbolProvider::GetContainerField
Этот метод возвращает поле, содержащее адрес отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetContainerField( 
   IDebugAddress*         pAddress,
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainerField(
   IDebugAddress            pAddress,
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
окне Адрес, представленный интерфейсом [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .

`ppContainerField`\
заполняет Возвращает поле контейнера, представленное интерфейсом [идебугконтаинерфиелд](../../../extensibility/debugger/reference/idebugcontainerfield.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
