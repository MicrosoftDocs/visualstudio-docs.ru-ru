---
description: Этот интерфейс является интерфейсом расширения, реализованным разработчиками IDebugProcess2.
title: Идебугпроцесскуерипропертиес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8205b96723a1b48da46e6e19162c50139c9fe71d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166220"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Этот интерфейс является интерфейсом расширения, реализованным разработчиками [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) . Он позволяет разработчику получить сведения о среде процесса отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализуйте этот интерфейс, чтобы получить сведения о среде выполнения процесса отладки.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessQueryProperties` .

|Метод|Описание|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Запрашивает значение свойства.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Запросы значений свойств.|

## <a name="remarks"></a>Комментарии
 Этот интерфейс реализован редко.

## <a name="requirements"></a>Требования
 Заголовок: Портприв. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
