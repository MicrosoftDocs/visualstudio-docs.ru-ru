---
description: Извлекает список необязательных модификаторов.
title: 'Идебугмодопт:: Жетмодоптс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 971d04662042afed1afe8e1861d0080b513ca74d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149942"
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

## <a name="see-also"></a>См. также раздел
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
