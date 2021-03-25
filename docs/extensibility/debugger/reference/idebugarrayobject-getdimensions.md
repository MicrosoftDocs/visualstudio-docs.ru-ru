---
description: Возвращает размеры массива.
title: 'Идебугаррайобжект:: Dimension | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ba82b8a921a7295b6521622ff45efc84a9b6742
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058889"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Возвращает размеры массива.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Параметры
`dwCount`\
окне Число извлекаемых измерений.

`dwDimensions`\
[вход, выход] Массив, который заполняется размерами каждого измерения. `dwCount` Задает максимальный размер `dwDimensions` массива.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Многомерный массив может иметь разные размеры для каждого измерения. Например, при наличии трехмерного массива `myarray[3][2][6]` этот метод возвращает 3, 2 и 6 в `dwDimensions` параметре в указанном порядке.

## <a name="see-also"></a>См. также
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
