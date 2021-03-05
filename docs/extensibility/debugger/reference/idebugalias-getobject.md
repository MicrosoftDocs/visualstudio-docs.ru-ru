---
description: Возвращает объект, для которого предназначен этот псевдоним.
title: 'Идебугалиас:: GetObject | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetObject
helpviewer_keywords:
- IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10bcb0bb356907cb3f23b1c470248b9926f329ec
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143900"
---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
Возвращает объект, для которого предназначен этот псевдоним.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetObject(
   IDebugObject2** ppObject
);
```

```csharp
int GetObject(
   Out IDebugObject2 ppObject
)
```

## <a name="parameters"></a>Параметры
`ppObject`\
заполняет [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) , который представляет этот псевдоним.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
