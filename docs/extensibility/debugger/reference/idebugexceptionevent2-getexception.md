---
description: Возвращает подробное описание исключения, которое вызвало это событие.
title: 'IDebugExceptionEvent2:: except | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6505cd2309323d7fe91f2c807af33555c3575fd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152901"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Возвращает подробное описание исключения, которое вызвало это событие.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>Параметры
`pExceptionInfo`\
[вход, выход] Структура [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , которая заполняется описанием исключения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии

 [Только C++] Вызывающий объект отвечает за освобождение всех строк в структуре [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , а также освобождение объекта [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) в структуре.

## <a name="see-also"></a>См. также раздел
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
