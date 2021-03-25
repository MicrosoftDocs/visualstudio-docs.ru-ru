---
description: Этот интерфейс используется для представления и получения сведений с сервера на компьютере в сети.
title: IDebugCoreServer2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 318644353ff3643e92b2a7186359661b403db486
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077724"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Этот интерфейс используется для представления и получения сведений с сервера на компьютере в сети.

## <a name="syntax"></a>Синтаксис

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio реализует этот интерфейс для представления сервера. Каждый экземпляр Visual Studio создает экземпляр этого интерфейса.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Поставщик пользовательского порта получает этот интерфейс в вызове [события](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Модуль отладки может получить этот интерфейс опосредованно через вызов метода- [сервера](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (который возвращает [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)— интерфейс, производный от `IDebugCoreServer2` ).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugCoreServer2` .

|Метод|Описание|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Возвращает имя и атрибуты компьютера.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Возвращает имя компьютера.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Возвращает поставщика порта, существующего на компьютере.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Возвращает порт, уже существующий на компьютере.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Создает перечислитель для всех портов на компьютере.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Создает перечислитель для всех поставщиков портов на компьютере.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Возвращает служебные программы для компьютера.|

## <a name="remarks"></a>Remarks
 Этот интерфейс также используется в Visual Studio для просмотра процессов, выполняющихся на компьютерах в сети.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
