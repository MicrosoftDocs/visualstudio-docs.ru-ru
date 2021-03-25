---
description: Возвращает число элементов в массиве.
title: 'Идебугаррайобжект:: NOCOUNT | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c3a5d052fcb2c40f9dad76791aa992dbfbde72b0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058902"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Возвращает число элементов в массиве.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Параметры
`pdwElements`\
заполняет Возвращает число.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод видит все элементы объекта массива в виде одномерного массива, даже если объект массива является многомерным. Например, при наличии массива `myarray[3][2][6]` этот метод возвратит 36 в `pdwElements` параметре. Используйте метод [WebMethod](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) для получения отдельных элементов по одному за раз.

## <a name="see-also"></a>См. также
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
