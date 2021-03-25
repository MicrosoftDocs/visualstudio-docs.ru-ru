---
description: Этот метод задает (DE) GUID модуля отладки.
title: 'IDebugEngine3:: Сетенгинегуид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64d18b8a2cc1e1f0a6ad67418bb4abdf1e684829
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066169"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
Этот метод задает для модуля отладки (DE) `GUID` .

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetEngineGuid(
   GUID* guidEngine
);
```

```csharp
int SetEngineGuid(
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Параметры
`guidEngine`\
[входные] `GUID` подсистемы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
