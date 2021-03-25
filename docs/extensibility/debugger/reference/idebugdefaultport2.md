---
description: Этот интерфейс предоставляет несколько методов для доступа к серверу и средствам уведомления на порту.
title: IDebugDefaultPort2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 03eb9f8c1bae74f15d295a72b27821d41b8282a1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067118"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Этот интерфейс предоставляет несколько методов для доступа к серверу и средствам уведомления на порту.

## <a name="syntax"></a>Синтаксис

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio реализует этот интерфейс, чтобы представить порт отладки для доступа к программам. Пользовательский поставщик порта также может реализовать этот интерфейс, если он обрабатывает удаленную отладку.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс предоставляет аргумент для методов в интерфейсе [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . Вызов [QueryInterface](/cpp/atl/queryinterface) в интерфейсе [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) также может получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 В дополнение к методам, определенным в [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Получает интерфейс уведомления порта от этого порта.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Возвращает интерфейс для сервера, на котором размещен этот порт.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Определяет, работает ли этот порт на локальном компьютере.|

## <a name="remarks"></a>Remarks
 Имя " `IDebugDefaultPort2` " является битом атрибутаDurableService, так как оно не представляет порт по умолчанию. Его можно назвать «IDebugPort3».

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
