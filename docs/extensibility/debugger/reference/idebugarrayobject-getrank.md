---
description: Возвращает ранг массива, то есть количество измерений.
title: 'Идебугаррайобжект:: Rank | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a246cda3f5b9395ae013b4bca9d4d27d6f8a5c1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158544"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Возвращает ранг массива, то есть количество измерений.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Параметры
`pdwRank`\
заполняет Возвращает ранг.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Используйте метод [Dimension](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) , чтобы получить размер каждого измерения объекта массива.

## <a name="see-also"></a>См. также раздел
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
