---
description: Этот метод возвращает объект Property, содержащий локальные переменные, аргументы и другие свойства метода.
title: 'Идебужекспрессионевалуатор:: Жетмесодпроперти | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d98e661ad3f469c41c120e07e6d54f76b089cb0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152511"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Этот метод возвращает объект Property, содержащий локальные переменные, аргументы и другие свойства метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Параметры
`pSymbolProvider`\
окне Используемый поставщик символов, выраженный как объект [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
окне Адрес в коде, выраженный как объект [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , который должен быть разрешаться в ближайшую содержащую функцию.

`pBinder`\
окне Используемый связыватель, выраженный как объект [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) .

`fIncludeHiddenLocals`\
окне Ненулевое ( `TRUE` ) означает включение скрытых локальных переменных; нуль ( `FALSE` ) означает выход из скрытых локальных переменных

`ppProperty`\
заполняет Возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий метод.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Скрытые локальные переменные обычно являются переменными, создаваемыми компилятором.

## <a name="see-also"></a>См. также раздел
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
