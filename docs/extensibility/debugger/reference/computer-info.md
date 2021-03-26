---
description: Описывает компьютер, на котором работает отладчик.
title: COMPUTER_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7ebcee7270eb187998ce7c6078277dd90897012
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096464"
---
# <a name="computer_info"></a>COMPUTER_INFO
Описывает компьютер, на котором работает отладчик.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="members"></a>Участники
`wProcessorArchitecture`\
Определяет архитектуру микропроцессора.

`wSuiteMask`\
Определяет маску набора.

`dwOperatingSystemVersion`\
Номер версии операционной системы.

## <a name="remarks"></a>Remarks
Эта структура возвращается методом [жеткомпутеринфо](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) .

## <a name="requirements"></a>Требования
Заголовок: Мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [жеткомпутеринфо](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
