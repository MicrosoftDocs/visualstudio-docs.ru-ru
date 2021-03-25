---
description: Указывает, какие сведения о потоке необходимо получить.
title: THREADPROPERTY_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81d185a80761e42e706dc3ef36da056bb37b0b1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070873"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Указывает, какие сведения о потоке необходимо получить.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Поля
 `TPF_ID`\
 Инициализируйте или используйте `dwThreadId` поле структуры [среадпропертиес](../../../extensibility/debugger/reference/threadproperties.md) .

 `TPF_SUSPENDCOUNT`\
 Инициализируйте или используйте `dwSuspendCount` поле `THREADPROPERTIE` структуры S.

 `TPF_STATE`\
 Инициализируйте или используйте `dwThreadState` поле `THREADPROPERTIE` структуры S.

 `TPF_PRIORITY`\
 Инициализируйте или используйте `bstrPriority` поле `THREADPROPERTIE` структуры S.

 `TPF_NAME`\
 Инициализируйте или используйте `bstrName` поле `THREADPROPERTIE` структуры S.

 `TPF_LOCATION`\
 Инициализируйте или используйте `bstrLocation` поле `THREADPROPERTIE` структуры S.

 `TPF_ALLFIELDS`\
 Задает все поля.

## <a name="remarks"></a>Remarks
 Эти значения передаются в качестве аргумента в метод [жетсреадпропертиес](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) , чтобы указать, какие поля структуры [среадпропертиес](../../../extensibility/debugger/reference/threadproperties.md) должны быть инициализированы.

 Эти значения также используются в `dwFields` члене `THREADPROPERTIES` структуры для указания того, какие поля используются и являются допустимыми.

 Эти флаги можно сочетать с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
