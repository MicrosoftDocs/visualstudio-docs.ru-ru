---
description: Этот метод использует поиск с учетом регистра для возврата значения, связанного с именем константы перечисления.
title: 'Идебуженумфиелд:: Жетвалуефромстрингкасеинсенситиве | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f853598c5d3c9b293c806e1db475c5053a1a208e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153226"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Этот метод использует поиск с учетом регистра для возврата значения, связанного с именем константы перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Параметры
`pszValue`\
окне Строка, указывающая имя, для которого необходимо получить значение. Обратите внимание, что для C++ это строка расширенных символов.

`pValue`\
заполняет Возвращает связанное числовое значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает значение `S_OK` ; в противном случае возвращает значение `S_FALSE` , если имя не является частью перечисления, или код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод не учитывает регистр. Если требуется поиск с учетом регистра (например, на языке C++, где в именах учитывается регистр), используйте [жетвалуефромстринг](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>См. также раздел
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
