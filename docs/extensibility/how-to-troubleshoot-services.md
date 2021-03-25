---
title: Руководство. Устранение неполадок служб | Документация Майкрософт
description: Узнайте, как устранять некоторые распространенные проблемы, которые могут возникнуть при попытке получить службу в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a105f38166ecea958bb0e5bbfe790170b020e354
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079219"
---
# <a name="how-to-troubleshoot-services"></a>Руководство. Устранение неполадок служб
Существует несколько распространенных проблем, которые могут возникнуть при попытке получить службу:

- Служба не зарегистрирована в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Служба запрашивается типом интерфейса, а не типом службы.

- Пакет VSPackage, запрашивающий службу, не был помещен в узел.

- Используется неправильный поставщик услуг.

  Если запрашиваемая служба не может быть получена, вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> возвращает значение null. После запроса службы всегда следует проверять значение NULL:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Устранение неполадок службы

1. Проверьте системный реестр, чтобы узнать, была ли служба зарегистрирована правильно. Дополнительные сведения см. [в разделе руководство. предоставление службы](../extensibility/how-to-provide-a-service.md).

    Следующий фрагмент файла *reg* показывает, как может быть зарегистрирована служба SVsTextManager:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    В приведенном выше примере номер версии — это версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , например 12,0 или 14,0, раздел {F5E7E71D-1401-11D1-883B-0000F87579D2} — это идентификатор службы (SID) службы, SVsTextManager, а значение по умолчанию {F5E7E720-1401-11D1-883B-0000F87579D2} — идентификатор GUID пакета VSPackage текстового диспетчера, который предоставляет службу.

2. При вызове метода WebService используйте тип службы, а не тип интерфейса. При запросе службы из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Package> ИЗВЛЕКАЕТСЯ идентификатор GUID из типа. Служба не будет найдена, если выполняются следующие условия.

   1. Тип интерфейса передается методу "Услуга", а не типу службы.

   2. Для интерфейса явно не назначен GUID. Поэтому при необходимости система создает идентификатор GUID по умолчанию для объекта.

3. Убедитесь, что пакет VSPackage, запрашивающий службу, был помещен в сайт. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] сайты VSPackage после создания и перед вызовом <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

    Если у вас есть код в конструкторе VSPackage, которому требуется служба, переместите ее в `Initialize` метод.

4. Убедитесь, что используется правильный поставщик услуг.

    Не все поставщики служб являются одинаковыми. Поставщик услуг, который [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] передается в окно инструментов, отличается от того, который он передает в VSPackage. Поставщик службы окон инструментов знает <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> , но не знает о них <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Можно вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для получения поставщика службы VSPackage из окна инструментов.

    Если в окне инструментов размещается пользовательский элемент управления или любой другой контейнер элементов управления, контейнер будет размещен в модели компонентов Windows и не будет иметь доступа к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] службам. Можно вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для получения поставщика службы VSPackage из контейнера элементов управления.

## <a name="see-also"></a>См. также
- [Список доступных служб](../extensibility/internals/list-of-available-services.md)
- [Использование и предоставление служб](../extensibility/using-and-providing-services.md)
- [Основные компоненты службы](../extensibility/internals/service-essentials.md)
- [Устранение неполадок в Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)