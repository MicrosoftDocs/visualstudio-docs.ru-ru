---
description: Вызывается отладчиком в текущем кадре стека, когда ему требуется перехват текущего исключения.
title: 'IDebugStackFrame3:: Интерцепткуррентексцептион | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8aa2815eab2e78b373340ca1d4c60b4ae9929548
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053247"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Вызывается отладчиком в текущем кадре стека, когда ему требуется перехват текущего исключения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Параметры
`dwFlags`\
окне Задает различные действия. В настоящее время поддерживается только [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) значение, `IEA_INTERCEPT` и его необходимо указать.

`pqwCookie`\
заполняет Уникальное значение, идентифицирующее конкретное исключение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

 Ниже приведены наиболее распространенные ошибки.

|Ошибка|Описание|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Текущее исключение не может быть перехвачено.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Текущий кадр выполнения еще не выполнил поиск обработчика.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Этот метод не поддерживается для этого кадра.|

## <a name="remarks"></a>Remarks
 При возникновении исключения отладчик получает управление от времени выполнения по ключевым точкам во время обработки исключений. В течение этих минут отладчик может задать текущий кадр стека, если кадр желает перехватить исключение. Таким образом, перехваченное исключение — это, по сути, обработчик исключений для кадра стека, даже если этот кадр стека не имеет обработчика исключений (например, блока try/catch в коде программы).

 Когда отладчик хочет выяснить, следует ли перехватить исключение, он вызывает этот метод для текущего объекта кадра стека. Этот метод отвечает за обработку всех сведений об исключении. Если интерфейс [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) не реализован или `InterceptStackException` метод возвращает ошибку, отладчик продолжит обработку исключения обычным образом.

> [!NOTE]
> Исключения могут перехватываться только в управляемом коде, то есть когда отлаживаемая программа выполняется во время выполнения .NET. Разумеется, сторонние средства реализации языка могут реализовывать `InterceptStackException` собственные модули отладки, если это так.

 После завершения перехвата получает сигнал [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) .

## <a name="see-also"></a>См. также
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
