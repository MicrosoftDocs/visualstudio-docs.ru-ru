---
description: Возвращает значение, указывающее протокол, используемый для обмена данными между сервером и пакетом отладки.
title: 'IDebugCoreServer3:: Жетконнектионпротокол | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetConnectionProtocol
helpviewer_keywords:
- IDebugCoreServer3::GetConnectionProtocol
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ddea336fb77691459ef3e58a7724d4e242c3be2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154734"
---
# <a name="idebugcoreserver3getconnectionprotocol"></a>IDebugCoreServer3::GetConnectionProtocol
Возвращает значение, указывающее протокол, используемый для обмена данными между сервером и пакетом отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetConnectionProtocol(
   CONNECTION_PROTOCOL* pProtocol
);
```

```csharp
int GetConnectionProtocol(
   CONNECTION_PROTOCOL[] pProtocol
);
```

## <a name="parameters"></a>Параметры
`pProtocol`\
заполняет Возвращает одно из значений перечисления [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)
