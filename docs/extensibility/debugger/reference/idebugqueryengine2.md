---
description: Этот интерфейс позволяет диспетчеру отладки сеансов (SDM) получать интерфейс, представляющий модуль отладки (DE).
title: IDebugQueryEngine2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f8e4cd9358cf63188ec88f4ec4a613aebf9d4f79
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151406"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Этот интерфейс позволяет диспетчеру отладки сеансов (SDM) получать интерфейс, представляющий модуль отладки (DE).

## <a name="syntax"></a>Синтаксис

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс для объектов, реализующих наиболее распространенные интерфейсы DE (например, [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)и [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)), чтобы обеспечить доступ к интерфейсу [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) интерфейса de.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на типичном интерфейсе de для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugQueryEngine2` .

|Метод|Описание|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Возвращает интерфейс пользовательского модуля отладки (DE).|

## <a name="remarks"></a>Комментарии
 Этот интерфейс обычно реализуется в объекте, реализующем интерфейс [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , для поддержки последовательного упорядочения по функциям. то есть, когда отладчик выполняет шаг с выходом из функции, следующая выполняемая функция может не быть предыдущей функцией в стеке, а функция в другом потоке — вообще. Определение причинности см. в разделе [Глоссарий отладчика Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
