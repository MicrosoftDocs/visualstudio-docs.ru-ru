---
description: Сообщает узлу программы или программы, какой модуль отладки (DE) следует использовать для отладки этой программы.
title: 'IDebugProgramEngines2:: Сетенгине | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e938cd63c88d0d58866b36528a1342983dc457f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084185"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Сообщает узлу программы или программы, какой модуль отладки (DE) следует использовать для отладки этой программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Параметры
`guidEngine`\
окне Идентификатор GUID для DE.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
