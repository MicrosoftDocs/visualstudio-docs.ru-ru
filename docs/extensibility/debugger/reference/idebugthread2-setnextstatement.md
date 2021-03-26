---
description: Задает текущий указатель инструкции для данного контекста кода.
title: 'IDebugThread2:: Сетнекстстатемент | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5dd6bd027a9938b7dce855742cc351180498bb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081169"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Задает текущий указатель инструкции для данного контекста кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Параметры
`pStackFrame`\
Зарезервировано для будущего использования; Задайте для значение null.

`pCodeContext`\
окне Объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , описывающий расположение кода для выполнения и его контекст.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны другие возможные значения.

|Значение|Описание|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Следующий оператор не может находиться в кадре стека более глубоко в стеке кадров.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Следующая инструкция не связана ни с одним кадром в стеке.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Некоторые отладчики отладчика не могут задать следующий оператор после исключения.|

## <a name="remarks"></a>Remarks
 Указатель инструкции указывает следующую инструкцию или инструкцию для выполнения. Этот метод используется для повтора строки исходного кода или принудительного выполнения, чтобы продолжить выполнение в другой функции, например.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
