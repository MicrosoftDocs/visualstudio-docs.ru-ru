---
description: Этот метод преобразует расположение метода и смещение в адрес памяти.
title: 'Идебужекспрессионевалуатор:: Жетмесодлокатионпроперти | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f841f602064b21035ea409457c708f99ec25bf12
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152524"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Этот метод преобразует расположение метода и смещение в адрес памяти.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Параметры
`upstrFullyQualifiedMethodPlusOffset`\
окне Положение и смещение метода, выраженное в виде строки.

`pSymbolProvider`\
окне Поставщик символов, выраженный в виде объекта [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
окне Адрес в методе, выраженный как объект [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
окне Связыватель, выраженный как объект [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) .

`ppProperty`\
заполняет Возвращает интерфейс [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий адрес памяти.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Для задания точки останова можно использовать возвращенный адрес, например.

 Несмотря на имя `upstrFullyQualifiedMethodPlusOffset` , этому параметру может быть передано имя метода с частичным указанием. В этом случае выбранным методом является тот, который в нем заключен `pAddress` . Способ интерпретации этого параметра является реализацией средства оценки выражений и поддерживаемого им языка.

## <a name="see-also"></a>См. также раздел
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
