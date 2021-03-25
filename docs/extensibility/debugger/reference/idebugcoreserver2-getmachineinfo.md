---
description: Извлекает описание компьютера, на котором работает основной сервер.
title: 'IDebugCoreServer2:: Жетмачинеинфо | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetInfo
helpviewer_keywords:
- IDebugCoreServer2::GetInfo
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 710738bc2284d4cba29a451209a91dd12091f1af
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077880"
---
# <a name="idebugcoreserver2getmachineinfo"></a>IDebugCoreServer2::GetMachineInfo
Извлекает описание компьютера, на котором работает основной сервер.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMachineInfo( 
   MACHINE_INFO_FIELDS Fields,
   MACHINE_INFO*       pMachineInfo
);
```

```csharp
int GetMachineInfo( 
   enum_ MACHINE_INFO_FIELDS  Fields,
   MACHINE_INFO[]             pMachineInfo
);
```

## <a name="parameters"></a>Параметры
`Fields`\
окне Сочетание флагов из перечисления [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) , определяющих поля, которые должны `pMachineInfo` быть заполнены.

 `pMachineInfo`\

 [вход, выход] Структура [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) , которая заполняется описанием компьютера.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
