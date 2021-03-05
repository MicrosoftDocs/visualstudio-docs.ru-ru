---
description: Этот интерфейс используется узлами программы для указания всех возможных модулей отладки (DE), которые могут отлаживать эту программу.
title: IDebugProgramEngines2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c19b4dc3967cf7001144d38114a1f873776cb2b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149591"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Этот интерфейс используется узлами программы для указания всех возможных модулей отладки (DE), которые могут отлаживать эту программу.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик DE или пользовательский порт реализует этот интерфейс для того же объекта, который реализует [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для поддержки установки конкретного de-используемого для конкретной программы.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) для `IDebugProgramNode2` интерфейса, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgramEngines2` .

|Метод|Описание|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Указывает все возможные алгоритмы DEs, которые могут отлаживать эту программу.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Выбирает DE, используемый для отладки этой программы.|

## <a name="remarks"></a>Комментарии
 После выбора пользователем DE этот вариант регистрируется в узле программы путем вызова [сетенгине](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Выбранный обработчик преобразуется в обработчик, возвращенный [жетенгинеинфо](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
