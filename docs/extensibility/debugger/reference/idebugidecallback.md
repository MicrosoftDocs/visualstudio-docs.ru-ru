---
description: Позволяет Вычислителю выражений (EE) отображать сообщение в окне вывода отладчика.
title: Идебугидекаллбакк | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 461003f3bdb83e51e8b5c525895d134b717d8fc6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091907"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Позволяет Вычислителю выражений (EE) отображать сообщение в окне вывода отладчика.

## <a name="syntax"></a>Синтаксис

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот обратный вызов реализуется управляемым модулем отладки.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Он может быть использован средством оценки выражений для отправки выходных данных в окно вывода отладчика.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Отправляет указанную строку сообщения в окно вывода отладчика.|

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
