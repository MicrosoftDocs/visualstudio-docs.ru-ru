---
description: Этот метод получает сведения о поле.
title: Идебугфиелд::/info | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: deebf0c8dafe64c8eb78ba5a1af0b8f96c70a18a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077061"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Этот метод получает сведения о поле.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Параметры
`dwFields`\
окне Сочетание [FIELD_INFO_FIELDSных](../../../extensibility/debugger/reference/field-info-fields.md) констант, которые выбирают отображаемые сведения. Если поле представляет символ, обычно это имя и тип символа.

`pFieldInfo`\
заполняет Возвращает сведения в указанной структуре [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
