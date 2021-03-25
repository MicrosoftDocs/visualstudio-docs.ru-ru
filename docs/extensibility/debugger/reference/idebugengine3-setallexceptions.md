---
description: Этот метод задает состояние всех необработанных исключений.
title: 'IDebugEngine3:: Сеталлексцептионс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetAllExceptions
helpviewer_keywords:
- IDebugEngine3::SetAllExceptions
ms.assetid: 8f03a6ac-a854-42f7-933c-a2df1b351975
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a6dbce81ed358ad13b49206e86c5f547a4db420
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066208"
---
# <a name="idebugengine3setallexceptions"></a>IDebugEngine3::SetAllExceptions
Этот метод задает состояние всех необработанных исключений.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetAllExceptions(
   EXCEPTION_STATE dwState
);
```

```csharp
int SetAllExceptions(
   enum_EXCEPTION_STATE dwState
);
```

## <a name="parameters"></a>Параметры
`dwState`\
окне Одно из значений [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
