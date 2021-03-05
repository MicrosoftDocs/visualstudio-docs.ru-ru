---
description: Возвращает свойство, которое необходимо уничтожить.
title: 'IDebugPropertyDestroyEvent2:: Жетдебугпроперти | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2::GetDebugProperty
helpviewer_keywords:
- IDebugPropertyDestroyEvent2::GetDebugProperty
ms.assetid: c96ae785-0ac8-4df4-8df3-15a8d7e13687
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78b1aecd63ba8b7a6defe7a24bcea8d6983f1610
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168040"
---
# <a name="idebugpropertydestroyevent2getdebugproperty"></a>IDebugPropertyDestroyEvent2::GetDebugProperty
Возвращает свойство, которое необходимо уничтожить.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Параметры
`ppProperty`\
заполняет Возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий свойство, которое необходимо уничтожить.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
