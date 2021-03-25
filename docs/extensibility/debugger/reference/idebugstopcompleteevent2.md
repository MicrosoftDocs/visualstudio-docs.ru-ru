---
description: Модуль отладки (DE) может отправить это необязательное событие в Диспетчер отладки сеансов (SDM) при остановке программы.
title: IDebugStopCompleteEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e4fd1826f44cb1d830ef45874b1c41c21a34895
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087149"
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
