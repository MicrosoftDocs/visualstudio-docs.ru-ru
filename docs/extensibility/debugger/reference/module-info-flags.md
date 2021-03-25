---
description: Указывает состояние символов для модуля.
title: MODULE_INFO_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FLAGS
helpviewer_keywords:
- MODULE_INFO_FLAGS enumeration
ms.assetid: e22d3723-b4d4-4524-8a2f-3adb55bbd273
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bfe1639ea187c6f03327a2278aaa9f849309a2af
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079713"
---
# <a name="module_info_flags"></a>MODULE_INFO_FLAGS
Указывает состояние символов для модуля.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_MODULE_INFO_FLAGS {
   MIF_SYMBOLS_LOADED = 0x0001
};
typedef DWORD MODULE_INFO_FLAGS;
```

```csharp
public enum enum_MODULE_INFO_FLAGS {
   MIF_SYMBOLS_LOADED = 0x0001
};
```

## <a name="fields"></a>Поля
 `MIF_SYMBOLS_LOADED`\
 Модуль загрузил по крайней мере один набор символов (в противном случае символы не были загружены).

## <a name="remarks"></a>Remarks
 Это значение возвращается методом [жетсимболсеарчинфо](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
