---
description: Возвращает порт, на котором выполняется процесс.
title: 'IDebugProcess2:: Port | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPort
helpviewer_keywords:
- IDebugProcess2::GetPort
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 83704cc45a1dd85031d1088bac8883a6a5996875
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081780"
---
# <a name="idebugprocess2getport"></a>IDebugProcess2::GetPort
Возвращает порт, на котором выполняется процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPort( 
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Параметры
`ppPort`\
заполняет Возвращает объект [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий порт, в котором был запущен процесс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
