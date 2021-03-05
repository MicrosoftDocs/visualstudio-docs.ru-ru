---
description: Наблюдает за выполнением (или останавливает наблюдение за выполнением) в заданном потоке.
title: 'IDebugEngineProgram2:: Ватчфорсреадстеп | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaf02e07bebbbfd711d99ef7605befbdce1f9376
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153421"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Наблюдает за выполнением (или останавливает наблюдение за выполнением) в заданном потоке.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Параметры
`pOriginatingProgram`\
окне Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, для которой выполняется пошаговое выполнение.

`dwTid`\
окне Указывает идентификатор потока для отслеживания.

`fWatch`\
окне Ненулевое значение ( `TRUE` ) означает начало наблюдения за потоком, определяемым `dwTid` ; в противном случае нуль ( `FALSE` ) означает завершение наблюдения за выполнением `dwTid` .

`dwFrame`\
окне Указывает индекс кадра, который управляет типом шага. Если это значение равно нулю (0), то тип шага — «шаг с заходом», и программа должна останавливаться всякий раз, когда поток определяется по `dwTid` выполнению. Если `dwFrame` имеет ненулевое значение, то шаг имеет тип «шаг с обходом», и программа должна останавливаться только в том случае, если поток, идентифицированный, `dwTid` выполняется в кадре, индекс которого равен или выше в стеке, чем `dwFrame` .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Когда диспетчер отладки сеансов (SDM) выводит программу, определяемую `pOriginatingProgram` параметром, она уведомляет все другие подключенные программы, вызывая этот метод.

 Этот метод применим только к степпингу одного потока.

## <a name="see-also"></a>См. также раздел
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
