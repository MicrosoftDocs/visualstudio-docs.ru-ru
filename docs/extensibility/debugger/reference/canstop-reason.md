---
description: Используется, чтобы определить, может ли программа прерывать выполнение после достижения определенной точки выполнения.
title: CANSTOP_REASON | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: def5bdbb6433f6a154eb6f84a88fb39004bc41ae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171002"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Используется, чтобы определить, может ли программа прерывать выполнение после достижения определенной точки выполнения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Поля
`CANSTOP_ENTRYPOINT`\
Указывает точку входа данной программы.

`CANSTOP_STEPIN`\
Указывает шаг с заходом в функцию.

## <a name="remarks"></a>Комментарии
Передается в качестве аргумента в метод [Reason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) для подтверждения в диспетчере отладки сеанса (SDM), если после достижения точки входа программы или после пошагового выполнения в функцию или метод.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
