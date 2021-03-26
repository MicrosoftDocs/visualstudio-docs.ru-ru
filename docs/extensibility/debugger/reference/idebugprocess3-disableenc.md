---
description: Этот метод явно отключает функцию "изменить и продолжить" для этого процесса (и всех содержащихся в нем программ).
title: IDebugProcess3::D Исаблинк | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f9c4a1e05cf7d4a98489daf0c2ee3377d54f417
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081624"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Этот метод явно отключает функцию "изменить и продолжить" для этого процесса (и всех содержащихся в нем программ). Пользовательский поставщик порта всегда должен возвращать значение `E_NOTIMPL` .

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Параметры
`reason`\
окне Значение из перечисления [енкунаваилаблереасон](../../../extensibility/debugger/reference/encunavailablereason.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

> [!NOTE]
> Пользовательский поставщик порта всегда должен возвращать значение `E_NOTIMPL` .

## <a name="remarks"></a>Remarks
 Если для процесса отключена возможность "изменить и продолжить", ее можно включить заново, только перезапустив процесс.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
