---
description: Возвращает тип элемента в массиве.
title: 'Идебугаррайфиелд:: Жетелементтипе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9624a04ae70c8d29abd9b8af5b597b583efb7834
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143848"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Возвращает тип элемента в массиве.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>Параметры
`ppType`\
заполняет Возвращает объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , описывающий тип элемента.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Объект [идебугаррайфиелд](../../../extensibility/debugger/reference/idebugarrayfield.md) предполагает, что все элементы массива имеют одинаковый тип.

## <a name="see-also"></a>См. также раздел
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
