---
description: Возвращает контекст памяти для значения свойства.
title: 'IDebugProperty2:: Жетмемориконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryContext
helpviewer_keywords:
- IDebugProperty2::GetMemoryContext
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a82b2f0ed4a1fb7a37ec621d737d624d30d33ef2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166857"
---
# <a name="idebugproperty2getmemorycontext"></a>IDebugProperty2::GetMemoryContext
Возвращает контекст памяти для значения свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext(
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>Параметры
`ppMemory`\
заполняет Возвращает объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , представляющий память, связанную с этим свойством.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает значение, `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT` Если контекст памяти для извлечения отсутствует.

## <a name="see-also"></a>См. также раздел
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
