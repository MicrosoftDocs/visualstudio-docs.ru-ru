---
description: Этот интерфейс перечисляет программы, запущенные в текущем сеансе отладки.
title: IEnumDebugPrograms2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d7f9a981146d5e024333f17557f4fdbc3d35bc05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082937"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Этот интерфейс перечисляет программы, запущенные в текущем сеансе отладки.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс, чтобы предоставить список программ, отлаживаемых с помощью DE.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Visual Studio вызывает [енумпрограмс](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) для получения этого интерфейса. [Енумпрограмс](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) не используется в Visual Studio.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugPrograms2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Извлекает указанное количество программ в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Пропускает указанное число программ в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Возвращает количество программ в перечислителе.|

## <a name="remarks"></a>Remarks
 Visual Studio использует этот интерфейс для:

- Заполните окно " **модули** " (вызвав [енумпрограмс](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , а затем вызвав [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) для каждой программы).

- Заполните список **присоединения к процессу** (вызвав `IDebugProcess2::EnumPrograms` , а затем вызвав [QueryInterface](/cpp/atl/queryinterface) для каждого интерфейса [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , чтобы получить интерфейс [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) ).

- Создать список DEs, который может выполнять отладку каждой программы в процессе (с помощью [жетенгинеинфо](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Примените обновления ("Изменить" и "продолжить") к каждой программе (вызвав IDebugProcess2:: Енумпрограмс, а затем вызвав [жетенкупдате](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
