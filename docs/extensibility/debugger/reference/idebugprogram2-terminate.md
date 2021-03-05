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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 880bf4e727d90c19cf11f42cc3020124235bb1e2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171987"
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

## <a name="remarks"></a>Комментарии
 Если возможно, программа будет завершена и выгружена из процесса. в противном случае модуль отладки (DE) выполнит необходимую очистку.

 Этот метод или метод [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) вызывается интегрированной средой разработки, обычно в ответ на то, что пользователь останавливает всю отладку. Реализация этого метода в идеале должна завершать программу внутри процесса. Если это невозможно, параметр DE должен препятствовать запуску программы в этом процессе (и выполнить все необходимые действия по очистке). Если `IDebugProcess2::Terminate` метод вызывался интегрированной средой разработки, весь процесс будет завершен некоторое время после `IDebugProgram2::Terminate` вызова метода.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Завершение](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
