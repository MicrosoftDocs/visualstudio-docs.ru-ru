---
description: Возвращает байты памяти, составляющие значение свойства.
title: 'IDebugProperty2:: Жетмеморибитес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryBytes
helpviewer_keywords:
- IDebugProperty2::GetMemoryBytes
ms.assetid: b32042ed-7a06-4b4a-99ef-fe03b0aa61cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcfb88c167c47a5802edfc2a4dc1b3f765659a1e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166922"
---
# <a name="idebugproperty2getmemorybytes"></a>IDebugProperty2::GetMemoryBytes
Возвращает байты памяти, составляющие значение свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMemoryBytes ( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes ( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>Параметры
`ppMemoryBytes`\
заполняет Возвращает объект [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , который можно использовать для получения памяти, содержащей значение свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает `S_GETMEMORYBYTES_NO_MEMORY_BYTES` , если нет байтов памяти для извлечения.

## <a name="see-also"></a>См. также раздел
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
