---
description: Определяет, поддерживает ли модуль отладки (DE) возможность передачи этого исключения в отлаживаемую программу при возобновлении выполнения.
title: 'IDebugExceptionEvent2:: Канпасстодебугжее | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b56996a5fa7cbf3c08842b783aa2d5dfc1131b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152888"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Определяет, поддерживает ли модуль отладки (DE) возможность передачи этого исключения в отлаживаемую программу при возобновлении выполнения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает либо `S_OK` (исключение может быть передано в программу), либо `S_FALSE` (исключение не может быть передано).

## <a name="remarks"></a>Комментарии
 Параметру DE должно быть назначено действие по умолчанию для передачи в отлаживаемый отладчик. Интегрированная среда разработки может получить событие [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) и вызвать метод [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) , не вызывая `CanPassToDebuggee` метод. Таким образом, DE должен иметь вариант по умолчанию для передачи исключения в или нет.

## <a name="see-also"></a>См. также раздел
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
