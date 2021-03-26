---
title: Метод Сетнотификатионфорваиткомплетион | Документация Майкрософт
description: Узнайте, как отладчик использует бит состояния, чтобы помочь выйти из тела асинхронного метода для задач в стиле Promise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e189a2c12e262b81f93f7f8de5e58ea22b1277c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079440"
---
# <a name="setnotificationforwaitcompletion-method"></a>Метод SetNotificationForWaitCompletion
Задает или очищает бит состояния TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

## <a name="syntax"></a>Синтаксис

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Параметры
 `enabled`

 `true` значение бита; `false` значение, чтобы отменить бит.

## <a name="exceptions"></a>Исключения

## <a name="remarks"></a>Remarks
 Отладчик задает этот бит, чтобы помочь выйти из тела асинхронного метода. Если `enabled` имеет значение `true` , этот метод должен вызываться только для задачи, которая еще не завершена. Если `enabled` имеет это `false` , этот метод может быть вызван для завершенных задач. В любом из событий его следует использовать только для задач в стиле Promise.

## <a name="requirements"></a>Требования

## <a name="see-also"></a>См. также раздел
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
