---
description: Возвращает количество элементов в массиве.
title: 'Идебугаррайфиелд:: Жетнумберофелементс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 237cc74b2a34c78104e001bcc5a3b13dd6c7bd43
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143835"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Возвращает количество элементов в массиве.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetNumberOfElements( 
   DWORD* pdwNumElements
);
```

```csharp
int GetNumberOfElements(
   out uint pdwNumElements
);
```

## <a name="parameters"></a>Параметры
`pdwNumElements`\
заполняет Возвращает количество элементов в массиве.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Возвращаемое значение — это общее количество элементов в массиве, независимо от числа измерений.

## <a name="see-also"></a>См. также раздел
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
