---
description: Указывает ссылочный тип.
title: REFERENCE_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91a77c73d689322faa22ea9ad81c8aacf0616d07
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225283"
---
# <a name="reference_type"></a>REFERENCE_TYPE
Указывает ссылочный тип.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
typedef DWORD REFERENCE_TYPE;
```

```csharp
public enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
```

## <a name="fields"></a>Поля
 `REF_TYPE_WEAK`\
 Указывает слабую ссылку. Не может использоваться вместе с `REF_TYPE_STRONG` .

 `REF_TYPE_STRONG`\
 Задает строгую ссылку. Не может использоваться вместе с `REF_TYPE_WEAK` .

## <a name="remarks"></a>Комментарии
 Используется в качестве `dwRefType` члена структуры [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .

 Передается в качестве параметра в метод [сетреференцетипе](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)
