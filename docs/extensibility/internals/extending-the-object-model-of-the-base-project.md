---
title: Расширение объектной модели базового проекта | Документация Майкрософт
description: Узнайте, как расширить объектную модель автоматизации базового проекта в Visual Studio с помощью подтипа проекта.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175571b374c6a54999b212b316301f3f775891ff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899346"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Расширение объектной модели базового проекта

Подтип проекта может расширить объектную модель автоматизации базового проекта в следующих местах:

- Project. Extender (" \<ProjectSubtypeName> "): позволяет подтипу проекта предлагать объект с пользовательскими методами из <xref:EnvDTE.Project> объекта. Подтип проекта может использовать расширители автоматизации для предоставления `Project` объекта. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на основе статистического выражения подтипа проекта, должен предоставлять свой объект для `VSHPROPID_ExtObjectCATID` FROM <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (соответствующий `itemid` значению [вситемид. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem. Extender (" \<ProjectSubtypeName> "): позволяет подтипу проекта предлагать объект с пользовательскими методами из определенного <xref:EnvDTE.ProjectItem> объекта в проекте. Подтип проекта может использовать расширители автоматизации для предоставления этого объекта. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на основном агрегаторе подтипа проекта, должен предоставлять свой объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующего нужному <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ) CATID.

- Project. Properties: Эта коллекция предоставляет независимые от конфигурации свойства `Project` объекта. Дополнительные сведения о свойствах `Project` см. в разделе <xref:EnvDTE.Project.Properties%2A>. Подтип проекта может использовать расширители автоматизации для добавления его свойств в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на основном агрегаторе подтипа проекта, должен предоставлять свой объект для `VSHPROPID_BrowseObjectCATID` FROM <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующий `itemid` значению [вситемид. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration. Properties: Эта коллекция предоставляет зависящие от конфигурации свойства проекта для конкретной конфигурации (например, Debug). Для получения дополнительной информации см. <xref:EnvDTE.Configuration>. Подтип проекта может использовать расширители автоматизации для добавления его свойств в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на главном агрегаторе подтипа проекта, предлагает свой объект для CATID `VSHPROPID_CfgBrowseObjectCATID` (соответствующий `itemid` значению [вситемид. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Интерфейс используется для различения одного объекта обзора конфигурации из другого.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
