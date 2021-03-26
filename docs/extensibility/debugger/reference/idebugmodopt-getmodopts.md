---
description: Извлекает список необязательных модификаторов.
title: 'Идебугмодопт:: Жетмодоптс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 614ecb456b6f644dfd389020bbffb23691cfbf43
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081910"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Извлекает список необязательных модификаторов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Параметры
`celt`\
окне Число возвращаемых элементов.

`rgelt`\
заполняет Возвращает массив, содержащий параметры.

`pceltFetched`\
[вход, выход] Число элементов, возвращаемых в `rgelt` массиве.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
