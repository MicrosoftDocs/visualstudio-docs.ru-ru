---
description: Извлекает идентификатор процесса, владеющего объектом, представленным данным интерфейсом IDebugAddress2.
title: 'IDebugAddress2:: GetProcessID | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eeae55e91df8dac3fb176952a352df642facb055
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154955"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Извлекает идентификатор процесса, владеющего объектом, представленным данным интерфейсом [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) .

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>Параметры
`pProcID`\
заполняет Идентификатор процесса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
