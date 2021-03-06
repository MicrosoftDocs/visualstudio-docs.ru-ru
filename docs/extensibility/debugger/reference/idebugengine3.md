---
description: Представляет один модуль отладки (DE), управляющий отладкой одного или нескольких модулей.
title: IDebugEngine3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3a10f439ba344b71cd31fd990928b7804b6c11d4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066194"
---
# <a name="idebugengine3"></a>IDebugEngine3
Представляет один модуль отладки (DE), управляющий отладкой одного или нескольких модулей.

## <a name="syntax"></a>Синтаксис

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется с помощью пользовательского DE (если он поддерживает символы) для включения состояния Жустмикоде. Этот интерфейс должен быть реализован с помощью DE, если он поддерживает символы и Жустмикоде.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс вызывается диспетчером отладки сеансов (SDM) для передачи параметров пользователя для расположений, из которых загружаются символы. Он также вызывается для установки идентификатора GUID обработчика при его создании (этот идентификатор GUID основан на метриках из времени регистрации механизма). SDM также вызывает этот интерфейс для установки состояния Жустмикоде и установки всех исключений, известных отладчику, в указанное состояние.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованным от [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Задает путь или пути, которые DE будет использовать для поиска отладочных символов.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Загружает символы для всех модулей, в которых их символы еще не загружены.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Указывает, что сведения о Жустмикодее находятся в де.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Задает значение DE GUID из метрик.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Задать все исключения, которые в настоящее время недопустимы в указанном состоянии.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
