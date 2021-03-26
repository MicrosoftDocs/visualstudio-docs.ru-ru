---
title: Регистрация устаревшего языка Service1 | Документация Майкрософт
description: Сведения о регистрации устаревшей языковой службы из пакета VSPackage в Visual Studio путем добавления разделов и записей реестра.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5fa94fbd514e5fb162bc569438197dd8c65444b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060774"
---
# <a name="registering-a-legacy-language-service-1"></a>Регистрация устаревшей языковой службы 1
В управляемой среде пакетов (MPF) языковая служба предложенной пакетом VSPackage (см. [пакеты VSPackage](../../extensibility/internals/vspackages.md)) и регистрируется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , добавляя разделы и записи реестра. Процесс регистрации выполняется частично во время установки и частично во время выполнения.

## <a name="register-the-language-service-by-using-attributes"></a>Регистрация языковой службы с помощью атрибутов
 Для регистрации языковой службы используются следующие атрибуты.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Ниже описаны эти атрибуты.

### <a name="provideserviceattribute"></a>провидесервицеаттрибуте
 Этот атрибут регистрирует языковую службу как службу.

### <a name="example"></a>Пример

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideServiceAttribute(typeof(TestLanguageService),
                             ServiceName = "Test Language Service")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageserviceattribute"></a>провиделангуажесервицеаттрибуте
 Этот атрибут регистрирует языковую службу специально в качестве языковой службы. Он позволяет задавать параметры, определяющие возможности, предоставляемые языковой службой. В примере показано подмножество параметров, которые может предоставить языковая служба. Полный набор параметров языковой службы см. в разделе <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .

### <a name="example"></a>Пример

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),
                             "Test Language",
                             106,             // resource ID of localized language name
                             CodeSense = true,             // Supports IntelliSense
                             RequestStockColors = false,   // Supplies custom colors
                             EnableCommenting = true,      // Supports commenting out code
                             EnableAsyncCompletion = true  // Supports background parsing
                             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageextensionattribute"></a>провиделангуажеекстенсионаттрибуте
 Этот атрибут связывает языковую службу с расширением файла. Каждый раз при загрузке файла с таким расширением в любом проекте служба языка запускается и используется для вывода содержимого файла.

### <a name="example"></a>Пример

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),
                                       ".Testext")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguagecodeexpansionattribute"></a>провиделангуажекодикспансионаттрибуте
 Этот атрибут регистрирует расположение, из которого получаются шаблоны расширения или фрагментов кода. Эта информация используется **браузером фрагментов кода** и редактором при вставке фрагмента кода в исходный файл.

### <a name="example"></a>Пример

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageCodeExpansionAttribute(
             typeof(TestLanguageService),
             "Test Language", // Name of language used as registry key.
             106,           // Resource ID of localized name of language service.
             "testlanguage",  // language key used in snippet templates.
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageeditoroptionpageattribute"></a>провиделангуажеедитороптионпажеаттрибуте
 Этот атрибут регистрирует страницу свойств, отображаемую в диалоговом окне " **Параметры** " в категории " **текстовый редактор** ". Используйте один из этих атрибутов для каждой страницы, которая будет отображаться для языковой службы. Если необходимо упорядочить страницы в древовидной структуре, используйте дополнительные атрибуты для определения каждого узла дерева.

### <a name="example"></a>Пример
 В этом примере показаны две страницы свойств, **Параметры** и **Отступы**, а также один узел, содержащий вторую страницу свойств.

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Options",      // Registry key name for property page
             "#242",         // Localized name of property page
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Advanced",     // Registry key name for node
             "#243",         // Localized name of node
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             @"Advanced\Indenting",     // Registry key name for property page
             "#244",         // Localized name of property page
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

## <a name="proffer-the-language-service-at-run-time"></a>Предложить языковую службу во время выполнения
 После загрузки языкового пакета необходимо сообщить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] о том, что языковая служба готова. Это можно сделать, профферинг службу. Это делается в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> методе. Кроме того, необходимо запустить таймер, который вызывает языковую службу во время периода простоя, чтобы можно было выполнить фоновый анализ. Этот таймер простоя также используется для обновления свойств документа, если они реализованы с помощью <xref:Microsoft.VisualStudio.Package.DocumentProperties> класса. Для поддержки таймера пакет должен реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> интерфейс (только <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> метод должен быть полностью реализован; остальные методы могут возвращать значения по умолчанию).

### <a name="example"></a>Пример
 В этом примере показан типичный подход к профферинг службы и предоставлению таймера бездействия.

```csharp

using System;
using System.Runtime.InteropServices;
using System.ComponentModel.Design;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.OLE.Interop;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,
        AutoOutlining = true,
        EnableCommenting = true,
        MatchBraces = true,
        ShowMatchingBrace = true)]
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package

    public class TestLanguagePackage : Package, IOleComponent
    {
        private uint m_componentID;

        protected override void Initialize()
        {
            base.Initialize();  // required

            // Proffer the service.
            IServiceContainer serviceContainer = this as IServiceContainer;
            TestLanguageService langService      = new TestLanguageService();
            langService.SetSite(this);
            serviceContainer.AddService(typeof(TestLanguageService),
                                        langService,
                                        true);

            // Register a timer to call our language service during
            // idle periods.
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                       as IOleComponentManager;
            if (m_componentID == 0 && mgr != null)
            {
                OLECRINFO[] crinfo = new OLECRINFO[1];
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
                                              (uint)_OLECADVF.olecadvfRedrawOff |
                                              (uint)_OLECADVF.olecadvfWarningsOff;
                crinfo[0].uIdleTimeInterval = 1000;
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);
            }
        }

        protected override void Dispose(bool disposing)
        {
            if (m_componentID != 0)
            {
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                           as IOleComponentManager;
                if (mgr != null)
                {
                    int hr = mgr.FRevokeComponent(m_componentID);
                }
                m_componentID = 0;
            }

            base.Dispose(disposing);
        }

        #region IOleComponent Members

        public int FDoIdle(uint grfidlef)
        {
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;
            // Use typeof(TestLanguageService) because we need to
            // reference the GUID for our language service.
            LanguageService service = GetService(typeof(TestLanguageService))
                                      as LanguageService;
            if (service != null)
            {
                service.OnIdle(bPeriodic);
            }
            return 0;
        }

        public int FContinueMessageLoop(uint uReason,
                                        IntPtr pvLoopData,
                                        MSG[] pMsgPeeked)
        {
            return 1;
        }

        public int FPreTranslateMessage(MSG[] pMsg)
        {
            return 0;
        }

        public int FQueryTerminate(int fPromptUser)
        {
            return 1;
        }

        public int FReserved1(uint dwReserved,
                              uint message,
                              IntPtr wParam,
                              IntPtr lParam)
        {
            return 1;
        }

        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)
        {
            return IntPtr.Zero;
        }

        public void OnActivationChange(IOleComponent pic,
                                       int fSameComponent,
                                       OLECRINFO[] pcrinfo,
                                       int fHostIsActivating,
                                       OLECHOSTINFO[] pchostinfo,
                                       uint dwReserved)
        {
        }

        public void OnAppActivate(int fActive, uint dwOtherThreadID)
        {
        }

        public void OnEnterState(uint uStateID, int fEnter)
        {
        }

        public void OnLoseActivation()
        {
        }

        public void Terminate()
        {
        }

        #endregion
    }
}
```
