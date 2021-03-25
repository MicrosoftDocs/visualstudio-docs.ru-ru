---
description: Модуль отладки (DE) отправляет этот интерфейс в Диспетчер отладки сеансов (SDM) для установки сообщения в строке состояния во время загрузки символов.
title: IDebugBeforeSymbolSearchEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e3e7c0428a96b8841a598e7b91986aa1555ea5c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067482"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Модуль отладки (DE) отправляет этот интерфейс в Диспетчер отладки сеансов (SDM) для установки сообщения в строке состояния во время загрузки символов.

## <a name="syntax"></a>Синтаксис

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс, когда он должен задать сообщение в строке состояния во время загрузки символов. Этот интерфейс реализуется только модулями отладки, которые работают с или являются частью интерпретаторов сценариев. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс (модель SDM использует **QueryInterface** для доступа к интерфейсу **IDebugEvent2** ).

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события, когда он должен задать сообщение в строке состояния во время загрузки символов. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugBeforeSymbolSearchEvent2` .

|Метод|Описание|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Возвращает имя модуля, в котором выполняется отладка.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
