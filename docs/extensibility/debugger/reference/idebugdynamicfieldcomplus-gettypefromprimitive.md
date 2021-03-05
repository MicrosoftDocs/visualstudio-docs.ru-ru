---
description: Извлекает тип по заданному типу-примитиву.
title: 'Идебугдинамикфиелдкомплус:: Жеттипефромпримитиве | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
- GetTypeFromPrimitive
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bfd9b64a760a170791a921bb19508cfd6c789993
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167221"
---
# <a name="idebugdynamicfieldcomplusgettypefromprimitive"></a>IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
Извлекает тип по заданному типу-примитиву.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetTypeFromPrimitive(
   DWORD         dwCorElementType,
   IDebugField** ppType
);
```

```csharp
int GetTypeFromPrimitive(
   uint            dwCorElementType,
   out IDebugField ppType
);
```

## <a name="parameters"></a>Параметры
`dwCorElementType`\
окне Значение из [перечисления корелементтипе](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , представляющее тип-примитив.

`ppType`\
заполняет Возвращает [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий тип.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
