---
description: Этот метод создает службу визуализатора.
title: 'Иивисуализерсервицепровидер:: Креатевисуализерсервице | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b304dd8fe2845cf6c1201e6e128f8b89ec47b1b6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222826"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Этот метод создает службу визуализатора.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Параметры
`binder`\
окне Объект [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) , переданный в [евалуатесинк](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
окне Объект [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md) , переданный в `IDebugParsedExpression::EvaluateSync` .

`pAddress`\
окне Объект [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , переданный в `IDebugParsedExression::EvaluateSync` .

`dataProvider`\
окне Объект, реализующий интерфейс [иивисуализердатапровидер](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (предоставленный средством оценки выражений).

`ppService`\
заполняет Созданная служба.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 `binder` `pSymProv` Все параметры, и `pAddress` были переданы в `IDebugParsedExpression::EvaluateSync` метод. `CreateVisualizerService` метод должен вызываться только в `IDebugParsedExpression::EvaluateSync` составе поддержки средства оценки выражений для визуализаторов типов.

## <a name="see-also"></a>См. также раздел
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
