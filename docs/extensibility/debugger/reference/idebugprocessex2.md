---
description: Этот интерфейс позволяет диспетчеру отладки сеансов (SDM) уведомлять процесс, который присоединяется к процессу или отсоединяется от него.
title: IDebugProcessEx2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bd22a779cd0a474b5df03d2315402dbe1a25239
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081520"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Этот интерфейс позволяет диспетчеру отладки сеансов (SDM) уведомлять процесс, который присоединяется к процессу или отсоединяется от него.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский поставщик порта реализует этот интерфейс на том же объекте, что и интерфейс [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , чтобы:

- Поддержка отслеживания сеансов, подключенных к процессу

- Поддержка автоматического подключения для нескольких модулей отладки

  Поставщик настраиваемого порта может реализовать этот интерфейс, если он выбрал.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов

- Модель SDM вызывает [QueryInterface](/cpp/atl/queryinterface) на `IDebugProcess2` интерфейсе для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessEx2` .

|Метод|Описание|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Информирует процесс о том, что сеанс теперь отлаживается процесс.|
|[Отсоединить](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Информирует процесс о том, что сеанс больше не находится в процессе отладки.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Добавляет узлы программы для списка модулей отладки.|

## <a name="remarks"></a>Remarks
 Этот интерфейс является частным между SDM и процессом.

## <a name="requirements"></a>Требования
 Заголовок: Портприв. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
