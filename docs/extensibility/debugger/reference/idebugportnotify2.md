---
description: Этот интерфейс регистрирует или отменяет регистрацию программы, которую можно отладить с помощью порта, на котором она выполняется.
title: IDebugPortNotify2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 759be0ff57da7c6bb65ed6ca8191720f835b894a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169344"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Этот интерфейс регистрирует или отменяет регистрацию программы, которую можно отладить с помощью порта, на котором она выполняется.

## <a name="syntax"></a>Синтаксис

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский поставщик портов реализует этот интерфейс для поддержки добавления и удаления программ из порта. Обычно он реализуется для того же объекта, который реализует интерфейс [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [QueryInterface](/cpp/atl/queryinterface) в `IDebugPort2` интерфейсе возвращает этот интерфейс. Кроме того, вызов [жетпортнотифи](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) возвращает этот интерфейс. Модуль отладки может видеть этот интерфейс как параметр для [ватчфорпровидеревентс](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPortNotify2` .

|Метод|Описание|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Регистрирует программу, которую можно отладить с помощью порта, на котором она запущена.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Отменяет регистрацию программы, которая может быть отлаживаться из порта, на котором она выполняется.|

## <a name="remarks"></a>Комментарии
 Если порт отладки не позволяет получить сведения о загрузке или выгрузке программ, Пользовательский поставщик порта должен реализовать этот интерфейс. Все программы, загруженные для отладки через определенный порт, отправляются с помощью этого интерфейса.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
