---
description: Используется ядром отладки (DE) для запуска и завершения программ.
title: IDebugEngineLaunch2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f03b4754d1648dc8a184d59e5e8b0f038a000bf2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153473"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Используется ядром отладки (DE) для запуска и завершения программ.

## <a name="syntax"></a>Синтаксис

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется с помощью пользовательского интерфейса DE, если он имеет особые требования для запуска процесса, который не может быть полностью обработан пользовательским портом. Обычно это происходит, когда DE является частью интерпретатора, а отлаживаемый процесс является сценарием: сначала необходимо запустить интерпретатор, а затем загрузить и запустить сценарий. Порт может запустить интерпретатор, но сценарий может потребовать специальной обработки (где у DE есть роль). Этот интерфейс реализуется только в том случае, если существуют уникальные требования для запуска программы, которая не может быть обработана пользовательским портом.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс вызывается диспетчером отладки сеанса (SDM), если SDM может получить этот интерфейс из интерфейса [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (с помощью QueryInterface). Если этот интерфейс можно получить, SDM знает, что у DE есть особые требования, и вызывает этот интерфейс для запуска программы, вместо того чтобы запускать его через порт.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEngineLaunch2` .

|Метод|Описание|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Запускает процесс с помощью средства DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Возобновляет выполнение процесса.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Определяет, можно ли завершить процесс.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Завершает процесс.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
