---
description: Указывает, выполняется ли эмуляция или реализация точки останова данных в оборудовании.
title: BP_RES_DATA_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RES_DATA_FLAGS
helpviewer_keywords:
- BP_RES_DATA_FLAGS enumeration
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 293b3635dd1a725f90ce63a0aa2f8568d5b324e3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078179"
---
# <a name="bp_res_data_flags"></a>BP_RES_DATA_FLAGS
Указывает, выполняется ли эмуляция или реализация точки останова данных в оборудовании.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
typedef DWORD BP_RES_DATA_FLAGS;
```

```csharp
public enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
```

## <a name="fields"></a>Поля
`BP_RES_DATA_EMULATED`\
Указывает, что выполняется Эмуляция точки останова в данных.

## <a name="remarks"></a>Remarks
Используется для `dwFlags` элемента структуры [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
