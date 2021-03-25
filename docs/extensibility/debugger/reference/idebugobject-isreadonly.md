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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b3cf66d8d540a92b937de996368ed24b18ae0b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054066"
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

## <a name="remarks"></a>Remarks
 После создания объекта, доступного только для чтения, его значение не может быть изменено.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
