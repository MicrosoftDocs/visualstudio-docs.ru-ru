---
title: Получение порта | Документация Майкрософт
description: Узнайте, как Visual Studio передает порт модулю отладки для регистрации узлов программы с помощью порта и для удовлетворения запросов сведений о процессах.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b2d9c58f9a2e58e58fce44cb06827e9039e48c9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054872"
---
# <a name="get-a-port"></a>Получение порта
Порт представляет подключение к компьютеру, на котором выполняются процессы. Это может быть локальный компьютер или удаленный компьютер (который может работать под управлением операционных систем, отличных от Windows; Дополнительные сведения см. в разделе [порты](../../extensibility/debugger/ports.md) ).

Порт представлен интерфейсом [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) . Он используется для получения сведений о процессах, выполняемых на компьютере, к которому подключен порт.

Отладчику требуется доступ к порту для регистрации узлов программ с помощью порта и для удовлетворения запросов сведений о процессах. Например, если обработчик отладки реализует интерфейс [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) , то реализация метода [жетпровидерпроцессдата](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) может попросить указать порт на необходимость возврата сведений о процессе.

Visual Studio предоставляет необходимый порт модулю отладки и получает этот порт от поставщика порта. Если программа подключена к (из отладчика или вызвана исключением, которое запускает диалоговое окно JIT [JIT]), пользователю предоставляется выбор транспорта (другое имя для поставщика порта) для использования. В противном случае, если пользователь запускает программу из отладчика, система проекта указывает поставщика порта для использования. В любом из этих событий Visual Studio создает экземпляр поставщика порта, представленного интерфейсом [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , и запрашивает новый порт путем вызова [аддпорт](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) с помощью интерфейса [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) . Затем этот порт передается модулю отладки в одной форме или другой.

## <a name="example"></a>Пример
В этом фрагменте кода показано, как использовать порт, указанный для [лаунчсуспендед](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) , чтобы зарегистрировать узел программы в [ресумепроцесс](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Параметры, не связанные непосредственно с этой концепцией, были опущены для ясности.

> [!NOTE]
> В этом примере порт используется для запуска и возобновления процесса, и предполагается, что интерфейс [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) реализован в порте. Это не значит, что единственный способ выполнить эти задачи, и возможно, что порт даже не участвует в [IDebugProgramNode2е](../../extensibility/debugger/reference/idebugprogramnode2.md) программы.

```cpp
// This is an IDebugEngineLaunch2 method.
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,
                                      IDebugPort2 *pPort,
                                      /* omitted parameters */,
                                      IDebugProcess2**ppDebugProcess)
{
    // do stuff here to set up for a launch (such as handling the other parameters)
    ...

    // Now get the IPortNotify2 interface so we can register a program node
    // in CDebugEngine::ResumeProcess.
    CComPtr<IDebugDefaultPort2> spDefaultPort;
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);
    if (SUCCEEDED(hr))
    {
        CComPtr<IDebugPortNotify2> spPortNotify;
        hr = spDefaultPort->GetPortNotify(&spPortNotify);
        if (SUCCEEDED(hr))
        {
            // Remember the port notify so we can use it in ResumeProcess.
            m_spPortNotify = spPortNotify;

            // Now launch the process in a suspended state and return the
            // IDebugProcess2 interface
            CComPtr<IDebugPortEx2> spPortEx;
            hr = pPort->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                // pass on the parameters we were given (omitted here)
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)
            }
        }
    }
    return(hr);
}

HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)
{
    // Make a program node for this process
    HRESULT hr;
    CComPtr<IDebugProgramNode2> spProgramNode;
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);
    if (SUCCEEDED(hr))
    {
        hr = m_spPortNotify->AddProgramNode(spProgramNode);
        if (SUCCEEDED(hr))
        {
            // resume execution of the process using the port given to us earlier.
            // (Querying for the IDebugPortEx2 interface is valid here since
            // that's how we got the IDebugPortNotify2 interface in the first place.)
            CComPtr<IDebugPortEx2> spPortEx;
            hr = m_spPortNotify->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>См. также
- [Регистрация программы](../../extensibility/debugger/registering-the-program.md)
- [Включение отладки программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Поставщики портов](../../extensibility/debugger/port-suppliers.md)
- [Порты](../../extensibility/debugger/ports.md)
