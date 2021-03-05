---
description: Этот интерфейс представляет порт отладки на компьютере.
title: IDebugPort2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f78db8ba9a29b40d111dc5a82827395b100302b5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169487"
---
# <a name="idebugport2"></a>IDebugPort2
Этот интерфейс представляет порт отладки на компьютере.

## <a name="syntax"></a>Синтаксис

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский поставщик портов реализует этот интерфейс для представления порта отладки на компьютере.

 Если порт поддерживает отправку событий порта, он также должен реализовать <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс для поддержки <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейса, который, в свою очередь, предоставляет интерфейс [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовы метода [Port](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) или [аддпорт](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) возвращают этот интерфейс, представляющий запрошенный порт.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPort2` .

|Метод|Описание|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Возвращает имя порта.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Возвращает идентификатор порта.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Возвращает запрос, используемый для создания порта (если он доступен).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Возвращает поставщика порта для этого порта.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Возвращает интерфейс для процесса с учетом идентификатора процесса.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Перечисляет все процессы, запущенные в порте.|

## <a name="remarks"></a>Комментарии
 Локальный порт предоставляет доступ ко всем процессам и программам, выполняемым на локальном компьютере. Другие порты могут представлять подключение последовательного кабеля к устройству на основе Windows CE или сетевое подключение к компьютеру, не являющемуся DCOM. `IDebugPort2`Интерфейс используется для поиска имени и идентификатора порта, а также для перечисления всех процессов, запущенных в порте. Средства для запуска и завершения процессов в порте реализуются в `IDebugPortEx2` интерфейсе.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
