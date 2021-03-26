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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39a22a0534a464e9899e666550b31ab24503c05d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096529"
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

## <a name="remarks"></a>Remarks
Передается в качестве аргумента в метод [Reason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) для подтверждения в диспетчере отладки сеанса (SDM), если после достижения точки входа программы или после пошагового выполнения в функцию или метод.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
