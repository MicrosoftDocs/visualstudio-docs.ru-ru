---
description: Этот метод позволяет поставщику порта отображать предупреждение перед присоединением пользователя к незащищенному процессу.
title: 'Идебугпроцесссекурити:: Куерикансафеляттач | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e6a586983d64e8be27b15a0514234d1a321e943
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166168"
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

## <a name="see-also"></a>См. также раздел
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
