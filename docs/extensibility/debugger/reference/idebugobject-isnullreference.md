---
description: Проверяет, является ли этот объект пустой ссылкой.
title: 'Идебугобжект:: Иснуллреференце | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 844e6c92385c1aa719d3c9d0ff399db9104dccc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161515"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Проверяет, является ли этот объект пустой ссылкой.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Параметры
`pfIsNull`\
заполняет Возвращает ненулевое значение ( `TRUE` ), если этот объект является пустой ссылкой; в противном случае возвращает ноль ( `FALSE` ).

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Пустая ссылка означает пустой объект или объект, который не был назначен.

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
