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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c681fef38377f0ce8e74b45dba065b5eae39462c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151939"
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

## <a name="see-also"></a>См. также раздел
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
