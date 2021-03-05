---
description: Этот метод получает объект Идебугфунктионобжект, используемый для создания параметров функции.
title: 'Идебугбиндер:: Жетфунктионобжект | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9868edafb18a129d119a818d9e51363d4964afa2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143663"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Этот метод получает объект [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) , используемый для создания параметров функции.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Параметры
`ppFunction`\
заполняет Возвращает интерфейс [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) , используемый для создания параметров функции.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
