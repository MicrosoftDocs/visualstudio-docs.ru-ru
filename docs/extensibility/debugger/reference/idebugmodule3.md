---
description: Этот интерфейс представляет модуль, который поддерживает альтернативные расположения символов и состояний Жустмикоде.
title: IDebugModule3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38ced8edcc97ad4ab8ff4db430cea57a2533cb30
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149888"
---
# <a name="idebugmodule3"></a>IDebugModule3
Этот интерфейс представляет модуль, который поддерживает альтернативные расположения символов и состояний Жустмикоде.

## <a name="syntax"></a>Синтаксис

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для поддержки альтернативных расположений символов и для работы с Жустмикоде состояниями (см. Описание "Жустмикоде" в [глоссарии отладчика Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [жетсимболсеарчинфо](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) возвращает этот интерфейс. Метод DE отправляет интерфейс [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) в Диспетчер отладки сеансов (SDM) с помощью метода [event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Кроме того, вызов [QueryInterface](/cpp/atl/queryinterface) в интерфейсе [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам в интерфейсе [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Возвращает список путей поиска символов и результатов поиска по каждому пути.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Загружает и инициализирует символы для текущего модуля.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Возвращает флаг, указывающий, представляет ли модуль пользовательский код.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Указывает, должен ли модуль рассматриваться как пользовательский код.|

## <a name="remarks"></a>Комментарии
 Visual Studio является обычным потребителем этого интерфейса.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
