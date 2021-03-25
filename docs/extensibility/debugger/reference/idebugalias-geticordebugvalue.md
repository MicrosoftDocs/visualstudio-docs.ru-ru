---
description: Извлекает интерфейс управляемого кода, представляющий значение, связанное с этим псевдонимом.
title: 'Идебугалиас:: Жетикордебугвалуе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad6cd04d077245d3e893099aab8820ddc8ccf559
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095918"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Извлекает интерфейс управляемого кода, представляющий значение, связанное с этим псевдонимом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Параметры
`ppUnk`\
[out] `IUnknown` интерфейс, представляющий значение, связанное с этим псевдонимом. Этот интерфейс можно запрашивать для `ICorDebugValue` интерфейса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод применяется только к управляемым значениям ( `ICorDebugValue` интерфейс доступен в платформа .NET Framework и определен в платформа .NET Framework SDK в файле CorDebug. IDL).

## <a name="see-also"></a>См. также
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
