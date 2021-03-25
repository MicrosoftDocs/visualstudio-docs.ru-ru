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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1440ff2fa82c8296bf54b106b622556a8eebb611
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094332"
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

## <a name="remarks"></a>Remarks
 Используйте метод [Dimension](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) , чтобы получить размер каждого измерения объекта массива.

## <a name="see-also"></a>См. также
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
