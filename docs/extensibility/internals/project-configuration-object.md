---
title: Объект конфигурации проекта | Документация Майкрософт
description: Узнайте, как объект конфигурации проекта управляет отображением сведений о конфигурации в пользовательском интерфейсе.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a17d5ed54e74b5632d02f8f8013a9098aaab0a49
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062906"
---
# <a name="project-configuration-object"></a>Объект конфигурации проекта
Объект конфигурации проекта управляет отображением сведений о конфигурации в пользовательском интерфейсе.

 ![Конфигурация проекта Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "вспрожекткфг") Страницы свойств конфигурации проекта

 Поставщик конфигурации проекта управляет конфигурациями проекта. Среда и другие пакеты для получения доступа к конфигурациям проекта и получения сведений о них вызывают интерфейсы, присоединенные к объекту поставщика конфигурации проекта.

> [!NOTE]
> Вы не можете создавать или изменять файлы конфигурации решения программным способом. Для этого необходимо использовать `DTE.SolutionBuilder`. Дополнительные сведения см. в разделе [Конфигурация решения](../../extensibility/internals/solution-configuration.md) .

 Чтобы опубликовать отображаемое имя, которое будет использоваться в пользовательском интерфейсе конфигурации, проект должен реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , который возвращает список `IVsCfg` указателей, которые можно использовать для получения отображаемых имен конфигурации и сведений о платформе, которые должны быть перечислены в пользовательском интерфейсе окружения. Активная конфигурация и платформа определяются конфигурацией проекта, хранящейся в конфигурации активного решения. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>Метод можно использовать для получения активной конфигурации проекта.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>При необходимости объект может быть реализован в <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> объекте с <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> объектом, чтобы можно было получить `IVsProjectCfg2` объект на основе канонического имени конфигурации проекта.

 Другой способ предоставления среды и других проектов с доступом к конфигурациям проекта заключается в том, что проекты предоставляют реализацию метода, `IVsCfgProvider2::GetCfgs` возвращающего один или несколько объектов конфигурации. Проекты также могут реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , который наследует от `IVsProjectCfg` и `IVsCfg` , соответственно, для предоставления сведений о конфигурации. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> поддерживает платформы и функциональные возможности для добавления, удаления и переименования конфигураций проекта.

> [!NOTE]
> Поскольку Visual Studio больше не ограничена двумя типами конфигураций, код, обрабатывающий конфигурации, не должен быть написан с предположения о количестве конфигураций, а также не должен быть написан с предположением о том, что проект, имеющий только одну конфигурацию, обязательно является отладочной или розничной. Это делает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> устарело.

 Вызов `QueryInterface` для объекта, возвращаемого из метода `IVsGetCfgProvider::GetCfgProvider` извлечения `IVsCfgProvider2` . Если объект `IVsGetCfgProvider` не найден при вызове метода `QueryInterface` для `IVsProject3` объекта Project, можно получить доступ к объекту поставщика конфигурации, вызвав метод `QueryInterface` в корневом объекте браузера иерархии для объекта, возвращаемого для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` , или с помощью указателя на поставщик конфигурации, возвращенный для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .

 `IVsProjectCfg2` в основном предоставляет доступ к объектам сборки, отладки и управления развертыванием, а также позволяет проектам свободно группировать выходные данные. Методы `IVsProjectCfg` и `IVsProjectCfg2` можно использовать для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> для управления процессом сборки и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> указателей для выходных групп конфигурации.

 Проект должен возвращать одинаковое количество групп для каждой поддерживаемой конфигурации, даже если количество выходов, содержащихся в группе, может отличаться от конфигурации к конфигурации. Группы также должны иметь одинаковые сведения об идентификаторе (каноническое имя, отображаемое имя и сведения о группе) из конфигурации в пределах проекта. Дополнительные сведения см. в разделе [Конфигурация проекта для выходных данных](../../extensibility/internals/project-configuration-for-output.md).

 Чтобы включить отладку, в конфигурациях должны быть реализованы <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` — Это необязательный интерфейс, реализуемый проектами, позволяющий отладчику запустить конфигурацию и реализовать его в объекте конфигурации с помощью `IVsCfg` и `IVsProjectCfg` . Среда вызывает ее, когда пользователь выбирает, чтобы запустить отладчик, нажав клавишу F5.

 `ISpecifyPropertyPages` и `IDispatch` используются совместно со страницами свойств для получения и вывода сведений о конфигурации для пользователя. Дополнительные сведения см. в разделе [страницы свойств](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>См. также
- [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)
- [Конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md)
- [Конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)
- [Страницы свойств](../../extensibility/internals/property-pages.md)
- [Конфигурация решения](../../extensibility/internals/solution-configuration.md)
