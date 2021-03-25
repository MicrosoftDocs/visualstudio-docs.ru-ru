---
description: Возвращает элемент массива.
title: 'Идебугаррайобжект:: элемент | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43659e8dfbd86f800105cbfa35fa3b3a13c099cf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094384"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Возвращает элемент массива.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Параметры
`dwIndex`\
окне Индекс элемента.

`ppElement`\
заполняет Возвращает интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий элемент.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод видит все элементы объекта массива в виде одномерного массива, даже если объект массива является многомерным. Например, при наличии массива `myarray[3][2][6]` и `dwIndex` параметра 20 этот метод возвратит элемент из `myarray[1][1][2]` , а `dwIndex` параметр, равный 21, возвратит элемент из `myarray[1][1][3]` . Используйте метод [NOCOUNT](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) , чтобы определить общее число элементов в массиве.

## <a name="see-also"></a>См. также
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
