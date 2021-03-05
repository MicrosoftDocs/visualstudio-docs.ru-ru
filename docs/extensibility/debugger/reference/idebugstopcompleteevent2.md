---
description: Модуль отладки (DE) может отправить это необязательное событие в Диспетчер отладки сеансов (SDM) при остановке программы.
title: IDebugStopCompleteEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d96aa335c8951b9dfc80517bf797338cd590b48
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159749"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Модуль отладки (DE) может отправить это необязательное событие в Диспетчер отладки сеансов (SDM) при остановке программы.

## <a name="syntax"></a>Синтаксис

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков

Этот интерфейс появился в Visual Studio 2005. Предыдущие выпуски не поддерживали асинхронную остановку.

- Метод " [останавливает](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) " вызывается SDM в многопроцессных или многопрограммных сценариях. Когда одна программа отправляет событие остановки в SDM, SDM запрашивает остановку других программ.

Остановить используется для асинхронного информирования SDM о том, что программа остановлена. Формирование модели SDM полезно для модуля отладки интерпретатора, где иногда нет кода, выполняемого в отлаживаемой программе, поэтому [не может быть](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) выполнено синхронно. Если модуль отладки хочет применить это асинхронное уведомление, он должен возвратить `S_ASYNC_STOP` из " [останавливается](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)".

## <a name="requirements"></a>Требования

Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
