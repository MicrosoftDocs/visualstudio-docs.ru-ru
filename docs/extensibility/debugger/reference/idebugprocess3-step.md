---
description: Заставляет процесс выполнить шаг 1 инструкции или инструкции.
title: 'IDebugProcess3:: шаг | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d5c9e43676751a97baf0bf664c3da17dcf9aca5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076528"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Заставляет процесс выполнить шаг 1 инструкции или инструкции.

> [!NOTE]
> Этот метод следует использовать вместо [шага](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Параметры
`pThread`\
окне Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, для которого выполняется пошаговое выполнение.

`sk`\
окне Одно из значений [степкинд](../../../extensibility/debugger/reference/stepkind.md) .

`step`\
окне Одно из значений [степунит](../../../extensibility/debugger/reference/stepunit.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Если существует какая-либо синхронизация потоков или обмен данными между потоками, другие потоки в процессе будут выполняться, когда конкретный поток пошаговым выполнением.

 **Предупреждение об ошибке** Не отправляйте событие остановки или мгновенное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может перестать отвечать на запросы.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
