---
description: Создает объект Array.
title: 'Идебугфунктионобжект:: Креатеаррайобжект | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aee0617364321e5a18f0ea83ef7f19f1388209df
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166493"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Создает объект Array. Этот массив может содержать как примитивы, так и значения экземпляров объектов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`ot`\
окне Задает значение из перечисления [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) , указывающее тип нового объекта массива.

`pClassField`\
окне Объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий класс объекта, при создании массива значений экземпляра объекта. При создании массива примитивных объектов этот параметр имеет значение null.

`dwRank`\
окне Ранг или количество измерений массива.

`dwDims`\
окне Размеры каждого измерения массива.

`dwLowBounds`\
окне Источник каждого измерения (обычно 0 или 1).

`ppObject`\
заполняет Возвращает объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий только что созданный массив. Фактически это объект [идебугаррайобжект](../../../extensibility/debugger/reference/idebugarrayobject.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Вызовите этот метод, чтобы создать объект, который представляет параметр массива для функции, представленной интерфейсом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
