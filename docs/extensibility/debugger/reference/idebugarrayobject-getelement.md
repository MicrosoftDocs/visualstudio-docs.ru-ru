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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea10afac9f5503288d257833d6dd59f9ba56fc6f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158661"
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

## <a name="remarks"></a>Комментарии
 Этот метод видит все элементы объекта массива в виде одномерного массива, даже если объект массива является многомерным. Например, при наличии массива `myarray[3][2][6]` и `dwIndex` параметра 20 этот метод возвратит элемент из `myarray[1][1][2]` , а `dwIndex` параметр, равный 21, возвратит элемент из `myarray[1][1][3]` . Используйте метод [NOCOUNT](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) , чтобы определить общее число элементов в массиве.

## <a name="see-also"></a>См. также раздел
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
