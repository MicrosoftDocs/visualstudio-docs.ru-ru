---
description: Обеспечивает поддержку языкового стандарта для поставщика порта.
title: IDebugPortSupplierLocale2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c29bd3fb882be6529daa0d26ab4cde23c11d0bc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167065"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Обеспечивает поддержку языкового стандарта для поставщика порта.

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский поставщик портов реализует этот интерфейс для задания языкового стандарта.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы **IDebugPortSupplierLocale2**.

|Метод|Описание|
|------------|-----------------|
|[Pragma](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Задает языковой стандарт для поставщика порта.|

## <a name="requirements"></a>Требования
 Заголовок: Портприв. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
