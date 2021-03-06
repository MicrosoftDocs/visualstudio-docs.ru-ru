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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df5cfd2acef1a2214d4692a49c742c26cd420ffa
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227233"
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

## <a name="remarks"></a>Комментарии
 Разработчик может определить, как возвращаются сведения об ошибке. Однако некоторым вызывающим объектам может показаться, что был возвращен объект исключения, чтобы убедиться в наличии ошибки, поэтому этот метод всегда должен возвращать объект исключения, если произошла ошибка. Строка ошибки также должна указываться в том случае, если вызывающий объект хочет использовать ее.

## <a name="see-also"></a>См. также раздел
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
