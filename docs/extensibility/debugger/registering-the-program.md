---
title: Регистрация программы | Документация Майкрософт
description: Сведения о том, как отлаживаемая программа регистрируется через порт после того, как модуль отладки получит порт.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4fda27bd0572713e16311e6feae8ff74870cb006
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070639"
---
# <a name="register-the-program"></a>Регистрация программы
После того как модуль отладки получит порт, представленный интерфейсом [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , следующий шаг при включении отладки программы заключается в его регистрации в порте. После регистрации программа доступна для отладки одним из следующих способов:

- Процесс присоединения, который позволяет отладчику получить полный контроль над выполняемым приложением.

- JIT-отладка, позволяющая выполнять отладку программы, работающей независимо от отладчика. Когда архитектура среды выполнения перехватывает ошибку, отладчик получает уведомления перед тем, как операционная система или среда выполнения освобождает память и ресурсы программы, вызвавшей сбой.

## <a name="registering-procedure"></a>Процедура регистрации

### <a name="to-register-your-program"></a>Регистрация программы

1. Вызовите метод [аддпрограмноде](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) , реализованный портом.

     `IDebugPortNotify2::AddProgramNode` требуется указатель на интерфейс [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .

     Обычно, когда операционная система или среда выполнения загружает программу, она создает узел программы. Если модулю отладки (DE) запрашивается загрузка программы, компонент DE создает и регистрирует узел программы.

     В следующем примере показан модуль отладки, запускающий программу и регистрирующий его с помощью порта.

    > [!NOTE]
    > Этот пример кода не является единственным способом запуска и возобновления процесса. Этот код главным образом является примером регистрации программы с помощью порта.

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
                    hr  = spPortEx->ResumeProcess(pDebugProcess);
                }
            }
        }
        return(hr);
    }

    ```

## <a name="see-also"></a>См. также
- [Получение порта](../../extensibility/debugger/getting-a-port.md)
- [Включение отладки программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
