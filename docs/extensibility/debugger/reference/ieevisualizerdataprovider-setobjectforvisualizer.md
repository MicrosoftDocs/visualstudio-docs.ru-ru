---
description: Этот метод изменяет объект, который представляет визуализатор.
title: 'Иивисуализердатапровидер:: Сетобжектфорвисуализер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e0a59c10293d5d8cc13d46b625a7b43136cb71b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091803"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Этот метод изменяет объект, который представляет визуализатор.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Параметры
`pNewObject`\
окне Заданный объект.

`error`\
заполняет Если при установке объекта произошла ошибка, то эта строка содержит сообщение об ошибке.

`pException`\
заполняет Если произошла ошибка, этот объект содержит сведения об исключении.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Разработчик может определить, как возвращаются сведения об ошибке. Однако некоторым вызывающим объектам может показаться, что был возвращен объект исключения, чтобы убедиться в наличии ошибки, поэтому этот метод всегда должен возвращать объект исключения, если произошла ошибка. Строка ошибки также должна указываться в том случае, если вызывающий объект хочет использовать ее.

## <a name="see-also"></a>См. также
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
