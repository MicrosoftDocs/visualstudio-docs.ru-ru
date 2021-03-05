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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 698c803304cf5efd3375b6d49e4dedbc4622f4c1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221838"
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

## <a name="remarks"></a>Комментарии
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
