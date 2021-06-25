---
title: Метод Нотифидебугжерофваиткомплетион | Документация Майкрософт
description: Сведения о методе Нотифидебугжерофваиткомплетион, который является заполнителем, используемым отладчиком в качестве целевой точки останова.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b9d6b5fbdcb8195709a751117056bcaa0617eff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904221"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Метод Нотифидебугжерофваиткомплетион
Метод-заполнитель, используемый отладчиком в качестве цели точки останова. Этот метод не должен быть встроенным или оптимизированным.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

## <a name="syntax"></a>Синтаксис

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Remarks
 Все операции JOIN с задачей должны вызывать этот метод, если задан бит уведомления отладчика.

## <a name="requirements"></a>Требования

## <a name="see-also"></a>См. также раздел
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
