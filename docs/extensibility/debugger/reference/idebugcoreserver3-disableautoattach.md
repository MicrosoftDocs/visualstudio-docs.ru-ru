---
description: Отключает автоматическое присоединение для всех модулей отладки, связанных с этим сервером.
title: IDebugCoreServer3::D Исаблеаутоаттач | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DisableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::DisableAutoAttach
ms.assetid: 9d860a20-c154-4df4-ba15-636e0fcd42bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ad02efc68fe0bdd7a64ae0df02fe934a2044abc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154721"
---
# <a name="idebugcoreserver3disableautoattach"></a>IDebugCoreServer3::DisableAutoAttach
Отключает автоматическое присоединение для всех модулей отладки, связанных с этим сервером.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DisableAutoAttach(
   void
);
```

```csharp
int DisableAutoAttach();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
