---
description: Этот интерфейс описывает порт.
title: IDebugPortRequest2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ca2d1d59c66c87c2dbb0fc256481d35ad590dbe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142626"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Этот интерфейс описывает порт. Это описание используется для добавления порта к поставщику порта.

## <a name="syntax"></a>Синтаксис

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio обычно реализует этот интерфейс в процессе получения порта отладки от поставщика порта.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс передается в [аддпорт](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) для создания порта отладки. Вызов [жетпортрекуест](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) возвращает этот интерфейс, представляющий запрос, используемый для создания порта в первую очередь.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPortRequest2` .

|Метод|Описание|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Возвращает имя создаваемого порта.|

## <a name="remarks"></a>Комментарии
 Модуль отладки обычно не взаимодействует с поставщиком порта и не будет использовать его для этого интерфейса.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
