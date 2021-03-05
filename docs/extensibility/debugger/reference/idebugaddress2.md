---
description: Этот интерфейс предоставляет доступ к ИДЕНТИФИКАТОРу процесса, владеющего объектом, адрес которого представлен этим интерфейсом.
title: IDebugAddress2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58a3f01472f60996b7094334de8cb2dbd79acac0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143965"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Этот интерфейс предоставляет доступ к ИДЕНТИФИКАТОРу процесса, владеющего объектом, адрес которого представлен этим интерфейсом.

## <a name="syntax"></a>Синтаксис

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для того же объекта, который реализует интерфейс [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) . Этот интерфейс предоставляет доступ к ИДЕНТИФИКАТОРу процесса, владеющего объектом, связанным с этим адресом.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из интерфейса [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 В дополнение к методам, унаследованным от интерфейса [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Возвращает идентификатор процесса, владеющего объектом, представленным этим интерфейсом.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
