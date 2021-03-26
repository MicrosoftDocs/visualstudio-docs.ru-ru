---
description: Возвращает идентификатор GUID для этого процесса.
title: 'IDebugProcess2:: GetProcessId | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b42b6f029ee6bbffdb1c59c55a2781d87d450d9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081754"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Возвращает идентификатор GUID для этого процесса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

## <a name="parameters"></a>Параметры
`pguidProcessId`\
заполняет Возвращает идентификатор GUID для этого процесса.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Глобальный уникальный идентификатор (GUID) определяет этот процесс из всех других процессов, выполняющихся в системе.

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
