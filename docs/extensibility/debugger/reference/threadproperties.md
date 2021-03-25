---
description: Описывает свойства потока.
title: СРЕАДПРОПЕРТИЕС | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0707cb5da4c63ffd686f22fa691c103c954478c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070860"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Описывает свойства потока.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>Участники
 `dwFields`\
 Сочетание флагов из перечисления [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , описывающее, какие поля в этой структуре являются допустимыми.

 `dwThreadId`\
 Идентификатор потока.

 `dwSuspendCount`\
 Число приостановок потока.

 `dwThreadState`\
 Значение из перечисления "перечисление [", указывающее](../../../extensibility/debugger/reference/threadstate.md) состояние операционного потока.

 `bstrPriority`\
 Строка, указывающая приоритет потока; Например, "выше обычного", "нормального" или "критическое время".

 `bstName`\
 Имя потока.

 `bstrLocation`\
 Расположение потока (обычно самый верхний кадр стека), обычно выраженное в виде имени метода, в котором выполнение в данный момент останавливается.

## <a name="remarks"></a>Remarks
 Эта структура заполняется вызовом метода [жетсреадпропертиес](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . Эти сведения обычно используются при заполнении окна **потоков** .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
