---
description: Останавливает все потоки, выполняющиеся в этой программе.
title: 'IDebugEngineProgram2:: останавливается | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7263756a0a8bacbbc6f90e327916cec8868d8f5c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077373"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Останавливает все потоки, выполняющиеся в этой программе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод вызывается при отладке этой программы в среде с несколькими программами. При получении события остановки от какой-либо другой программы этот метод вызывается в этой программе. Реализация этого метода должна быть асинхронной; то есть не все потоки должны быть остановлены перед возвратом этого метода. Реализация этого метода может быть такой же простой, как вызов метода [каусебреак](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) в этой программе.

 Разработчики должны отправить [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) при остановке программы.

## <a name="see-also"></a>См. также
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
