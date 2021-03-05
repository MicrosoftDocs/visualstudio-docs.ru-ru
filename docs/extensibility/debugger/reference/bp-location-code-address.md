---
description: Описывает расположение точки останова по адресу в коде.
title: BP_LOCATION_CODE_ADDRESS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 961a62284b841d56ae73a29df0e83810ff9d7d20
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144446"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
Описывает расположение точки останова по адресу в коде.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Члены
`bstrContext`\
Контекст точки останова, обычно имя метода или функции, как показано в стеке вызовов.

`bstrModuleUrl`\
URL-адрес модуля, содержащего точку останова.

`bstrFunction`\
Имя функции, содержащей точку останова.

`bstrAddress`\
Адрес точки останова, который анализируется средством оценки выражений для привязки его к объекту [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="remarks"></a>Комментарии
Эта структура является членом структуры [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) в составе объединения.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
