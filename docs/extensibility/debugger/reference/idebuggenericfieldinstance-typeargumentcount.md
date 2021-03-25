---
description: Возвращает число аргументов параметра типа для данного экземпляра.
title: 'Идебугженерикфиелдинстанце:: Типеаргументкаунт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7afd914b3880ca1004a319a66b3f4176e15789e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072875"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Возвращает число аргументов параметра типа для данного экземпляра.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>Параметры
`pcArgs`\
[вход, выход] Число аргументов параметра типа для данного экземпляра.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Например, если List \<int> , этот метод возвращает значение 1, а если List \<int,float2> возвращает значение 2. Этот метод возвращает 0, если отсутствуют аргументы типа.

## <a name="see-also"></a>См. также
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
