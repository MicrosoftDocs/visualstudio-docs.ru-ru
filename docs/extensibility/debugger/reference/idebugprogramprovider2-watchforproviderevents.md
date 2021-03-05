---
description: Позволяет процессу получать уведомления о событиях портов.
title: 'IDebugProgramProvider2:: Ватчфорпровидеревентс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::WatchForProviderEvents
helpviewer_keywords:
- IDebugProgramProvider2::WatchForProviderEvents
ms.assetid: 2eb93653-b5fb-45b6-b136-56008c5d25ef
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb00d177cfdb5fe8451b914926f29f591d8f924d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151484"
---
# <a name="idebugprogramprovider2watchforproviderevents"></a>IDebugProgramProvider2::WatchForProviderEvents
Позволяет процессу получать уведомления о событиях портов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WatchForProviderEvents(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   CONST_GUID_ARRAY     EngineFilter,
   REFGUID              guidLaunchingEngine,
   IDebugPortNotify2*   pEventCallback
);
```

```csharp
int WatchForProviderEvents(
   enum_PROVIDER_FLAGS   Flags,
   IDebugDefaultPort2    pPort,
   AD_PROCESS_ID         ProcessId,
   CONST_GUID_ARRAY      EngineFilter,
   ref Guid              guidLaunchingEngine,
   IDebugPortNotify2     pEventCallback
);
```

## <a name="parameters"></a>Параметры
`Flags`\
окне Сочетание флагов из перечисления [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) . Для этого вызова обычно используются следующие флаги:

|Flag|Описание|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Вызывающий объект работает на удаленном компьютере.|
|`PFLAG_DEBUGGEE`|Выполняется отладка вызывающего объекта (для каждого узла возвращается дополнительная информация о маршалинге).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Вызывающий объект был подключен к, но не был запущен отладчиком.|
|`PFLAG_REASON_WATCH`|Вызывающий объект хочет отслеживать события. Если этот флаг не установлен. Затем событие обратного вызова удаляется, а вызывающий объект больше не получает уведомления.|

`pPort`\
окне Порт, на котором выполняется вызывающий процесс.

`processId`\
окне Структура [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , содержащая идентификатор процесса, содержащего рассматриваемую программу.

`EngineFilter`\
окне Массив идентификаторов GUID модулей отладки, связанных с процессом.

`guidLaunchingEngine`\
окне Идентификатор GUID модуля отладки, который запустил этот процесс (при наличии).

`pEventCallback`\
окне Объект [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) , получающий уведомления о событиях.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Когда вызывающий объект хочет удалить обработчик событий, установленный с предыдущим вызовом этого метода, вызывающий объект передает те же параметры, что и первый раз, но не отключает `PFLAG_REASON_WATCH` флаг.

## <a name="example"></a>Пример
 В следующем примере показано, как реализовать этот метод для объекта **кдебуженгине** , предоставляющего интерфейс [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) .

```cpp
STDMETHODIMP CDebugEngine::WatchForProviderEvents(
    PROVIDER_FLAGS Flags,
    IDebugDefaultPort2 *pPort,
    AD_PROCESS_ID processId,
    CONST_GUID_ARRAY EngineFilter,
    REFGUID guidLaunchingEngine,
    IDebugPortNotify2 *pPortNotify)
{
    HRESULT hRes = E_FAIL;

    if (EVAL(pPort != NULL) && EVAL(pPortNotify != NULL))
    {
        // We will only watch/send events about the process if the debugger
        // is actually debugging the process, and only if this is an attach or a LoRIE launch
        if (IsFlagSet(Flags, PFLAG_DEBUGGEE) &&
            guidLaunchingEngine == GUID_NULL &&
            processId.ProcessIdType == AD_PROCESS_ID_SYSTEM)
        {
            // We don't support WatchForProviderEvents when in interop mode
            if (m_fInterop)
            {
                ASSERT(!"Shouldn't ever be called in interop mode");
                hRes = E_FAIL;
            }
            else
            {
                if (IsFlagSet(Flags, PFLAG_REASON_WATCH))
                {
                    // QI to get IDebugEventCallback2 which is required.
                    CComQIPtr<IDebugEventCallback2> pCallback(pPortNotify);

                    ASSERT(pCallback != NULL);
                    if ( pCallback != NULL )
                    {
                        // Register the callback
                        hRes = this->InitDebugSession(pCallback);

                        if ( S_OK == hRes )
                        {
                            // Get the IDebugProcess2 from the port and call AttachImpl
                            CComPtr<IDebugProcess2> spProcess;

                            hRes = pPort->GetProcess(processId, &spProcess);

                            if (HREVAL(S_OK, hRes))
                            {
                                hRes = AttachImpl(spProcess, NULL, NULL, processId.ProcessId.dwProcessId, ATTACH_REASON_USER, NULL);

                                if ( FAILED(hRes) && (!m_pPidList || 0 == m_pPidList->GetCount()) )
                                    this->Cleanup();
                            }
                        }
                        else
                            this->Cleanup();
                    }
                    else
                        hRes = E_FAIL;
                }
                else
                {
                    // Detach will be done by SDM calling on programs directly if there are managed programs.

                    // This handling is the case where no managed code ever ran.
                    if ( this->IsProcessBeingDebugged(processId.ProcessId.dwProcessId) )
                    {
                        ProgramList *pProgList = this->GetProgramListCopy();

                        if ( EVAL(pProgList) )
                        {
                            if ( pProgList->GetCount() == 0)
                            {
                                CComPtr<ICorDebugProcess> pCorProcess;

                                hRes = this->GetCorProcess(processId.ProcessId.dwProcessId, &pCorProcess);

                                if (HREVAL(S_OK, hRes) )
                                {
                                    hRes = pCorProcess->Stop(INFINITE);

                                    if ( HREVAL(S_OK, hRes) )
                                        hRes = pCorProcess->Detach();
                                }

                                // Tell the engine that it should unregister this process from com+
                                this->UnregisterProcess(processId.ProcessId.dwProcessId);

                                // If there are no more pids left then cleanup everything.
                                if ( 0 == m_pPidList->GetCount() )
                                    this->Cleanup();
                            }
                            // This is needed for cases where the SDM has not yet received program create
                            // by the time that we need to detach (example: the managed attach succeeds,
                            // but some other attach step fails).
                            else
                            {
                                PROGNODE *pProgNode = NULL;
                                while ( pProgNode = pProgList->Next(pProgNode) )
                                {
                                    CDebugProgram * pProgram = ((CDebugProgram *)pProgNode->data);
                                    hRes = pProgram->Detach();
                                }
                            }

                            delete pProgList;
                        }
                    }
                    else
                        hRes = S_OK;
                }
            }
        }
        else
        {
            hRes = S_FALSE;
        }
    }
    else
    {
        hRes = E_INVALIDARG;
    }

    return hRes;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
