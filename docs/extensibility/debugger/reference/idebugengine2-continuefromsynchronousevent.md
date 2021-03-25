---
description: Вызывается диспетчером отладки сеансов (SDM) для указания на то, что Синхронное событие отладки, ранее отправленное модулем отладки (DE) в SDM, было получено и обработано.
title: 'IDebugEngine2:: Континуефромсинчронаусевент | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
helpviewer_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64303d91ff9ab4743adc980bb8ee92f9bdec9345
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093890"
---
# <a name="idebugengine2continuefromsynchronousevent"></a>IDebugEngine2::ContinueFromSynchronousEvent
Вызывается диспетчером отладки сеансов (SDM) для указания на то, что Синхронное событие отладки, ранее отправленное модулем отладки (DE) в SDM, было получено и обработано.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2* pEvent
);
```

```csharp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2 pEvent
);
```

## <a name="parameters"></a>Параметры
`pEvent`\
окне Объект [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , представляющий ранее отправленное Синхронное событие, из которого отладчик должен продолжить работу.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
Значение DE должно проверять, что это источник события, представленного `pEvent` параметром.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CEngine` объекта, реализующего интерфейс [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) .

```cpp
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)
{
    HRESULT hr;

    // Create a pointer to a unique event interface defined for batch file
    // breaks.
    IAmABatchFileEvent *pBatEvent;
    // Check for successful query for the unique batch file event
    // interface.
    if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,
                                        (void **)&pBatEvent)))
    {
        // Release the result of the QI.
        pBatEvent->Release();
        // Check thread message for notification to continue.
        if (PostThreadMessage(GetCurrentThreadId(),
                              WM_CONTINUE_SYNC_EVENT,
                              0,
                              0))
        {
            hr = S_OK;
        }
        else
        {
            hr = HRESULT_FROM_WIN32(GetLastError());
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }
    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
