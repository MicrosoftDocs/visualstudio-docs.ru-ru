---
description: Создает объект, представляющий тип-примитив.
title: 'Идебугтипефиелдбуилдер:: Креатепримитиве | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreatePrimitive
- IDebugTypeFieldBuilder::CreatePrimitive
ms.assetid: 512c6ff0-97c5-409f-939f-4cc969bc4bb9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c480b32d56708569d3ac05e309e8bd06e17db4e5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227363"
---
# <a name="idebugtypefieldbuildercreateprimitive"></a>IDebugTypeFieldBuilder::CreatePrimitive
Создает объект, представляющий тип-примитив.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreatePrimitive (
   DWORD          dwElementType,
   IDebugField ** pTypeField
);
```

```csharp
int CreatePrimitive (
   uint            dwElementType,
   out IDebugField pTypeField
);
```

## <a name="parameters"></a>Параметры
`dwElementType`\
окне Значение из [перечисления корелементтипе](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , представляющее тип-примитив.

`pTypeField`\
заполняет Возвращает интерфейс Идебугфиелд для нового типа.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)
