---
description: Возвращает следующий набор элементов из перечисления Ports.
title: 'IEnumDebugPorts2:: Next | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Next
helpviewer_keywords:
- IEnumDebugPorts2::Next
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5972a5676c0e7859886578cb871c9a25846a4dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052818"
---
# <a name="ienumdebugports2next"></a>IEnumDebugPorts2::Next
Возвращает следующий набор из перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugPort2** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugPort2[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>Параметры
`celt`\
[in] Количество получаемых элементов. Также указывает максимальный размер `rgelt` массива.

`rgelt`\
[вход, выход] Массив элементов [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , которые должны быть заполнены.

`pceltFetched`\
заполняет Возвращает количество элементов, фактически возвращаемых в `rgelt` .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если может быть возвращено меньше запрошенного числа элементов; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
