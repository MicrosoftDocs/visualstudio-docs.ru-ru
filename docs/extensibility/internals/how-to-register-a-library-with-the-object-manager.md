---
title: Как зарегистрировать библиотеку с помощью диспетчера объектов | Документация Майкрософт
description: Узнайте, как зарегистрировать библиотеку с помощью диспетчера объектов Visual Studio, чтобы можно было просматривать символы в средствах просмотра, таких как представление классов и обозреватель объектов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b83b68af4c026c40aca7969068ad015a61d64321
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086070"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Как зарегистрировать библиотеку с помощью диспетчера объектов
Средства просмотра символов, такие как **представление классов**, **обозреватель объектов**, **Обозреватель вызовов** и **Поиск результатов поиска** символов, позволяют просматривать символы в проекте или во внешних компонентах. К символам относятся пространства имен, классы, интерфейсы, методы и другие языковые элементы. Библиотеки отписывают эти символы и предоставляют их [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчеру объектов, который заполняет средства данными.

 Диспетчер объектов отслеживает все доступные библиотеки. Каждая библиотека должна быть зарегистрирована в диспетчере объектов перед предоставлением символов для средств обзора символов.

 Как правило, Библиотека регистрируется при загрузке VSPackage. Тем не менее при необходимости ее можно выполнить в другое время. Вы отрегистрируете библиотеку при завершении работы VSPackage.

 Чтобы зарегистрировать библиотеку, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> метод. Для библиотеки управляемого кода используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод.

 Чтобы отменить регистрацию библиотеки, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> метод.

 Чтобы получить ссылку на диспетчер объектов, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> передайте <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> `GetService` методу идентификатор службы.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Регистрация и Отмена регистрации библиотеки с помощью диспетчера объектов

### <a name="to-register-a-library-with-the-object-manager"></a>Регистрация библиотеки с помощью диспетчера объектов

1. Создайте библиотеку.

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. Получите ссылку на объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> типа и вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод.

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>Отмена регистрации библиотеки с помощью диспетчера объектов

1. Получите ссылку на объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> типа и вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> метод.

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>См. также
- [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Поддержка средств обзора символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Пошаговое руководство. предоставление списка символов, предоставленных библиотекой, диспетчеру объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
