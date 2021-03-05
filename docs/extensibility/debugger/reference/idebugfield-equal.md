---
description: Этот метод сравнивает это поле с указанным полем для проверки на равенство.
title: 'Идебугфиелд:: Equals | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2bf9b3e4bbb988621e3b65e855b07322fba1795
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152095"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Этот метод сравнивает это поле с указанным полем для проверки на равенство.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Параметры
`pField`\
окне Поле для сравнения с данным полем.

## <a name="return-value"></a>Возвращаемое значение
 Если поля совпадают, возвращает `S_OK` . Если поля отличаются, `S_FALSE.` в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
