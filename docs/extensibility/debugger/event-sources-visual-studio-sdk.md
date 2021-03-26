---
title: Источники событий (Visual Studio SDK) | Документация Майкрософт
description: 'Сведения о двух источниках событий в отладке Visual Studio: модуль отладки и диспетчер отладки сеанса.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], event sources
ms.assetid: b9ba0908-ae4c-4a64-aab1-bee453dd7a22
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec6213a1462c391d13bbdf8a20ac61e232cafb49
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097010"
---
# <a name="event-sources-visual-studio-sdk"></a>Источники событий (Visual Studio SDK)
Существует два источника событий: модуль отладки (DE) и диспетчер отладки сеансов (SDM). События, отправленные из DE, имеют подсистему, не имеющую значения NULL, а события, отправленные из SDM, имеют обработчик со значением NULL.

## <a name="example"></a>Пример
В следующем примере показано, как отправить **IDebugProgramCreateEvent2** из de в SDM.

```csharp
CDebugProgramCreateEvent* pProgramCreateEvent = new CDebugProgramCreateEvent();
if (FAILED(pCallback->Event(m_pEngine, NULL, m_pProgram, NULL, pProgramCreateEvent, IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS)))
{
    // Handle failure here.
}
]

CEvent * pProgCreate = new CEvent(IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS);
pProgCreate->SendEvent(pCallback, m_pEngine, (IDebugProgram2 *)this, NULL);

HRESULT CEvent::SendEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {
    HRESULT hr;

    if (m_dwAttrib & EVENT_STOPPING)
    {
        hr = SendStoppingEvent(pCallback, pEngine, pProgram, pThread);
    }
    else if (m_dwAttrib & EVENT_SYNCHRONOUS)
    {
        hr = SendSynchronousEvent(pCallback, pEngine, pProgram, pThread);
    }
    else
    {
        assert(m_dwAttrib == 0);
        hr = SendAsynchronousEvent(pCallback, pEngine, pProgram, pThread);
    }

    return hr;
}

HRESULT CEvent::SendAsynchronousEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {

    HRESULT hr;

    // Make sure the CEvent object running this code is not deleted until the code completes.
    AddRef();

    pCallback->Event(pEngine, NULL, pProgram, pThread, (IDebugEvent2 *)this, m_riid, m_dwAttrib);

    // No error recovery here.
    hr = S_OK;

    Release();
    return hr;
}

```

## <a name="see-also"></a>См. также
- [Отправка событий](../../extensibility/debugger/sending-events.md)
