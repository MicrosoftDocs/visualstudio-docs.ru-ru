---
description: Создает объект без конструктора.
title: 'Идебугфунктионобжект:: Креатеобжектноконструктор | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a35cab590ab763a3598f45ebe79543e66c2fa4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073525"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Создает объект без конструктора.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`pClassObject`\
окне Объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий тип создаваемого объекта.

`ppObject`\
заполняет Возвращает объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий только что созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр структуры или сложного типа (который не требует конструктора), который является параметром функции, представленной интерфейсом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

 Если для параметра объекта требуется конструктор, вызовите метод [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) .

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
