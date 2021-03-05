---
description: Извлекает адрес указателя.
title: 'IDebugPointerObject3:: Жетпоинтераддресс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetPointerAddress
- IDebugPointerObject3::GetPointerAddress
ms.assetid: 4cc5af04-9e70-420d-8230-ef3108df6d51
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec9bf50500766c98797764a2bc21bc7b066cb7f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142886"
---
# <a name="idebugpointerobject3getpointeraddress"></a>IDebugPointerObject3::GetPointerAddress
Извлекает адрес указателя.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPointerAddress (
   UINT64* puAddress
);
```

```csharp
int GetPointerAddress (
   out ulong puAddress
);
```

## <a name="parameters"></a>Параметры
`puAddress` заполняет Возвращает адрес указателя.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)
