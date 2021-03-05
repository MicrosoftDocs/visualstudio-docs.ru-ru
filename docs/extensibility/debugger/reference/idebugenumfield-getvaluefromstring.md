---
description: Этот метод возвращает значение, связанное с именем константы перечисления.
title: 'Идебуженумфиелд:: Жетвалуефромстринг | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6a4ab2950667ba9268335f2e0dbca1c0ce5183bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153304"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Этот метод возвращает значение, связанное с именем константы перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
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
 Этот метод учитывает регистр. Если требуется поиск без учета регистра (например, на языке, например Visual Basic, где имена не чувствительны к регистру), используйте [жетвалуефромстрингкасеинсенситиве](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>См. также раздел
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
