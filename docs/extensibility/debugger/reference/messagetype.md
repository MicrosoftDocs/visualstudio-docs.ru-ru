---
description: Указывает тип и причину сообщения.
title: MESSAGETYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b85933896dfff38c2d346fd18144710e2e6fc127
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091530"
---
# <a name="messagetype"></a>MESSAGETYPE
Указывает тип и причину сообщения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Поля
 `MT_OUTPUTSTRING`\
 Указывает, что сообщение должно быть отправлено в окно вывода. Это взаимоисключающее из `MT_MESSAGEBOX` .

 `MT_MESSAGEBOX`\
 Указывает, что сообщение должно отображаться в окне сообщения. Это взаимоисключающее из `MT_OUTPUTSTRING` .

 `MT_TYPE_MASK`\
 Значение маски для изоляции назначения сообщения.

 `MT_REASON_EXCEPTION`\
 Указывает, что в результате исключения отображается окно сообщения. Это взаимоисключающее из `MT_REASON_TRACEPOINT` .

 `MT_REASON_TRACEPOINT`\
 Указывает, что в результате попадания в точку трассировки отображается окно сообщения. Это взаимоисключающее с `MT_REASON_EXCEPTION` .

 `MT_REASON_MASK`\
 Значение маски, которое позволяет изолировать причину отображения сообщения.

## <a name="remarks"></a>Remarks
 Эти значения возвращаются методами [жетеррормессаже](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) [и.](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)

 Одно из значений причины можно объединить с одним из значений назначения выходных данных с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
