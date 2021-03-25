---
description: Этот метод позволяет поставщику порта отображать предупреждение перед присоединением пользователя к незащищенному процессу.
title: 'Идебугпроцесссекурити:: Куерикансафеляттач | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbbfcf11a35fcfc43ae9e903b13a7480a3cf9743
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076281"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Этот метод позволяет поставщику порта отображать предупреждение перед присоединением пользователя к незащищенному процессу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Возвращаемое значение
 Ниже приведены возвращаемые значения.

- `S_OK`: Присоединение к процессу является надежным, и не отображается диалоговое окно предупреждения.

- `S_FALSE`: Присоединение может быть проблемой безопасности, и отображается диалоговое окно с предупреждением.

- `FAILURE`: Присоединение к процессу завершается ошибкой.

## <a name="see-also"></a>См. также
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
