---
description: Этот метод преобразует строку выражения в проанализированное выражение.
title: Идебужекспрессионевалуатор::P Арсе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6a586c7e7cac1a4ef034b7941840db59d376180
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152498"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Этот метод преобразует строку выражения в проанализированное выражение.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Параметры
`upstrExpression`\
окне Строка выражения для синтаксического анализа.

`dwFlags`\
окне Коллекция констант [парсефлагс](../../../extensibility/debugger/reference/parseflags.md) , определяющих способ синтаксического анализа выражения.

`nRadix`\
окне Основание системы счисления, используемое для интерпретации любых числовых данных.

`pbstrError`\
заполняет Возвращает ошибку в виде текста, читаемого человеком.

`pichError`\
заполняет Возвращает позиции символа начала ошибки в строке выражения.

`ppParsedExpression`\
заполняет Возвращает проанализированное выражение в объекте [идебугпарседекспрессион](../../../extensibility/debugger/reference/idebugparsedexpression.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод создает проанализированное выражение, а не фактическое значение. Проанализированное выражение готово к вычислению, то есть преобразованному в значение.

## <a name="see-also"></a>См. также раздел
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
