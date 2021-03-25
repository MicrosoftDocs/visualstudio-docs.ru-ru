---
description: Указывает, какая часть состояния программы (например, выполняемые потоки, кадры стека и адрес текущей инструкции) следует дампу.
title: ДУМПТИПЕ | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc27474b0012e60cccadda44665dc368178a02da
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095970"
---
# <a name="dumptype"></a>DUMPTYPE
Указывает, какая часть состояния программы (например, выполняемые потоки, кадры стека и адрес текущей инструкции) следует дампу.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="fields"></a>Поля
`DUMP_MINIDUMP`\
Задает небольшой, компактный дамп.

`DUMP_FULLDUMP`\
Указывает большой полный дамп.

## <a name="remarks"></a>Remarks
Передается в качестве аргумента в метод [вритедумп](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
