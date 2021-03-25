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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7bbcb8dba1593de824a5a0bb2d4d31f7602eb879
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067469"
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

## <a name="see-also"></a>См. также
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
