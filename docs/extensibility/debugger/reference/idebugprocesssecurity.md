---
description: Идебугпроцесссекурити реализуется поставщиком порта для предупреждения пользователя о том, что присоединение к процессу является ненадежным.
title: Идебугпроцесссекурити | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7466d88be9460a2b4680fc7d14a741df9238ea0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076268"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` реализуется поставщиком порта для предупреждения пользователя о том, что присоединение к процессу является ненадежным.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessSecurity` .

|Метод|Описание|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Возвращает имя пользователя от поставщика порта.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Предупреждает пользователя о том, что присоединение к процессу отладки является ненадежным.|

## <a name="remarks"></a>Remarks
 Реализуйте этот интерфейс, чтобы отобразить предупреждение и разрешить пользователю отменять, если процесс, к которому выполняется присоединение, может считаться небезопасным.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Порты](../../../extensibility/debugger/ports.md)
- [Поставщики портов](../../../extensibility/debugger/port-suppliers.md)
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
