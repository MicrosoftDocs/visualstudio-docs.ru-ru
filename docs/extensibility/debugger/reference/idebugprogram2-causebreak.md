---
description: Запрашивает, что программа останавливает выполнение, в следующий раз, когда один из его потоков пытается выполнить.
title: 'IDebugProgram2:: Каусебреак | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef10a714b6e65b40edb83cb0547ae1a28720d328
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166038"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Запрашивает, что программа останавливает выполнение, в следующий раз, когда один из его потоков пытается выполнить.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Событие [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) отправляется, когда программа далее пытается выполнить код после вызова этого метода.

 Этот метод является асинхронным в том случае, если метод возвращает значение немедленно, без обязательного ожидания завершения программы.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
