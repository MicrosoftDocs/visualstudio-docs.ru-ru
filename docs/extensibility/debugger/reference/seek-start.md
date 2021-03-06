---
description: Указывает начальную точку поиска в потоке дизассемблированного кода.
title: SEEK_START | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bb097c6015b5457a0ad4808674321c410a559d2
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221903"
---
# <a name="seek_start"></a>SEEK_START
Указывает начальную точку поиска в потоке дизассемблированного кода.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Поля
 `SEEK_START_BEGIN`\
 Начинает поиск в начале текущего документа.

 `SEEK_START_END`\
 Начинает поиск в конце текущего документа.

 `SEEK_START_CURRENT`\
 Начинает поиск в текущей позиции текущего документа.

 `SEEK_START_CODECONTEXT`\
 Начинает поиск в заданном контексте кода текущего документа.

 `SEEK_START_CODELOCID`\
 Начинает поиск по указанному идентификатору расположения кода. Идентификаторы расположения кода получаются путем вызова [жеткуррентлокатион](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Комментарии
 Передается в качестве аргумента в метод [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
