---
description: Определяет, доступен ли этот объект только для чтения.
title: 'Идебугобжект:: IsReadOnly | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99cf51ba5415631b2e8e66c36b459297a8fcb6e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161482"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Определяет, доступен ли этот объект только для чтения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Параметры
`pfIsReadOnly`\
заполняет Возвращает ненулевое значение ( `TRUE` ), если данный объект доступен только для чтения; в противном случае возвращает ноль ( `FALSE` ).

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 После создания объекта, доступного только для чтения, его значение не может быть изменено.

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
