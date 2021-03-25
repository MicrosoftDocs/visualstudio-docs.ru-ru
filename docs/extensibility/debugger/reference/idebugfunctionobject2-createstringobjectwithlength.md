---
description: Создает строковый объект, имеющий указанную длину.
title: 'IDebugFunctionObject2:: Креатестрингобжектвисленгс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5314bf6d06f291ce7128b3b6ccebd520ef2eafca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072836"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Создает строковый объект, имеющий указанную длину.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`pcstrString`\
окне Строковое значение для объекта String.

`uiLength`\
окне Длина строки в байтах.

`ppObject`\
заполняет Возвращает объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий только что созданный строковый объект.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
