---
description: Завершает программу.
title: 'IDebugProgram2:: Terminate | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 404df2be6718ab691ec47081b6fd400a1ddc8891
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084471"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Завершает программу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Если возможно, программа будет завершена и выгружена из процесса. в противном случае модуль отладки (DE) выполнит необходимую очистку.

 Этот метод или метод [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) вызывается интегрированной средой разработки, обычно в ответ на то, что пользователь останавливает всю отладку. Реализация этого метода в идеале должна завершать программу внутри процесса. Если это невозможно, параметр DE должен препятствовать запуску программы в этом процессе (и выполнить все необходимые действия по очистке). Если `IDebugProcess2::Terminate` метод вызывался интегрированной средой разработки, весь процесс будет завершен некоторое время после `IDebugProgram2::Terminate` вызова метода.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Завершение](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
