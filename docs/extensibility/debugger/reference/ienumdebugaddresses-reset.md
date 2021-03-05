---
description: Этот метод сбрасывает перечисление адресов к первому элементу.
title: 'Иенумдебугаддрессес:: Reset | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90ccbb3be28f676133756d5d07fcaca7e0aca3ec
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222670"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
Этот метод сбрасывает перечисление к первому элементу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Параметры
 None

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 После вызова этого метода следующий вызов [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
