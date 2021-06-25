---
title: Проектирование подтипов проектов | Документация Майкрософт
description: Узнайте, как подтипы проектов позволяют VSPackage расширять проекты на основе Microsoft Build Engine (MSBuild).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c04c8e681646aed6816c645defe7ffd87ac7033c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899697"
---
# <a name="project-subtypes-design"></a>Разработка подтипов проекта

Подтипы проектов позволяют VSPackage расширять проекты на основе Microsoft Build Engine (MSBuild). Использование статистической обработки позволяет повторно использовать основную часть реализуемой управляемой системы проектов, тем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не менее настроив поведение для конкретного сценария.

 В следующих разделах подробно описаны основные проектирование и реализация подтипов проектов.

- Проект подтипа проекта.

- Многоуровневая агрегация.

- Вспомогательные интерфейсы.

## <a name="project-subtype-design"></a>Проект подтипа проекта

Инициализация подтипа проекта достигается за счет статистической обработки основных <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объектов и <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Этот агрегат позволяет подтипу проекта переопределять или улучшать большинство возможностей базового проекта. Подтипы проектов получают первый шанс для обработки свойств с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , команд, с помощью, и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> управления элементами проекта с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Подтипы проектов также могут расширять:

- Объекты конфигурации проекта.

- Зависимые от конфигурации объекты.

- Независимые от конфигурации объекты просмотра.

- Объекты автоматизации проектов.

- Коллекции свойств автоматизации проекта.

Дополнительные сведения о расширяемости для подтипов проектов см. в разделе [Свойства и методы, расширенные по подтипам проектов](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Файлы политики

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Среда предоставляет пример расширения базовой системы проектов с подтипом проекта в его реализации файлов политики. Файл политики позволяет выполнять формирование [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды, управляя компонентами, включающими диалоговое окно Обозреватель решений, **Добавление проекта** , **Добавление нового элемента** и диалоговое окно **Свойства** . Подтип политики переопределяет и расширяет эти функции с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> реализаций и.

### <a name="aggregation-mechanism"></a>Механизм агрегирования

Механизм агрегирования подтипа проекта среды поддерживает несколько уровней статистической обработки, позволяя реализовать Расширенный подтип, изменяя проект. Кроме того, вспомогательные объекты подтипа проекта, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> , предназначены для разрешения нескольких уровней слоев. В соответствии с ограничениями правил агрегирования COM и COM, подтипы проектов и базовые проекты должны быть совместно обработаны, чтобы обеспечить правильное участие внутреннего подтипа или базового проекта при делегировании вызовов методов и управлении счетчиками ссылок. То есть проект, для которого необходимо выполнить статистическую обработку, должен быть запрограммирован на поддержку статистической обработки.

На следующем рисунке показано схематическое представление агрегированного подтипа проекта с несколькими уровнями.

![График Visual Studio multilevel projectflavor](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Многоуровневая агрегация подтипа проекта состоит из трех уровней: базового проекта, который агрегирован по подтипу проекта, а затем статистической обработки расширенного подтипа проекта. Эта фигура посвящена некоторым вспомогательным интерфейсам, предоставляемым как часть [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] архитектуры подтипа проекта.

### <a name="deployment-mechanisms"></a>Механизмы развертывания

Между множеством базовых функций системы проектов, улучшенных подтипом проекта, применяются механизмы развертывания. Подтип проекта влияет на механизмы развертывания путем реализации интерфейсов конфигурации (таких как <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ), которые извлекаются путем вызова QueryInterface в <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . В сценарии, где и подтип проекта, и Расширенный подтип проекта добавляют различные реализации конфигурации, базовый проект вызывает `QueryInterface` в качестве дополнительного подтипа проекта `IUnknown` . Если внутренний подтип проекта содержит реализацию конфигурации, для которой запрашиваются базовые проекты, то Расширенный подтип проекта делегирует реализации, предоставляемой внутренним подтипом проекта. В качестве механизма сохранения состояния из одного уровня статистической обработки в другой все уровни подтипов проектов реализуются <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> для сохранения данных XML, не связанных с построением, в файлы проекта. Дополнительные сведения см. [в разделе Сохранение данных в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> реализуется как механизм для получения расширителей автоматизации из подтипов проекта.

На следующем рисунке основное внимание уделяется реализации расширения автоматизации, объекта просмотра конфигурации проекта в частности, используемого подтипами проекта для расширения базовой системы проектов.

![График авто расширения проекта Flavor VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Подтипы проектов могут дополнительно расширить базовую систему проектов путем расширения объектной модели автоматизации. Они определяются как часть объекта автоматизации DTE и используются для расширения объекта проекта, `ProjectItem` объекта и `Configuration` объекта. Дополнительные сведения см. [в разделе Расширение объектной модели базового проекта](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Многоуровневая агрегация

Реализация подтипа проекта, которая служит оболочкой для подтипа проекта более низкого уровня, должна совместно программироваться, чтобы обеспечить правильную работу внутреннего подтипа проекта. Список функциональных обязанностей программирования включает:

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>Реализация подтипа проекта, который является оберткой внутреннего подтипа, должна делегировать <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> реализацию внутреннего подтипа проекта для <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> методов и.

- <xref:EnvDTE80.IInternalExtenderProvider>Реализация подтипа проекта-оболочки должна быть делегирована его внутреннему подтипу проекта. В частности, реализация <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> должна получить строку имен из внутреннего подтипа проекта, а затем сцепить строки, которые необходимо добавить в качестве расширителей.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>Реализация подтипа проекта-оболочки должна создать экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> объекта внутреннего подтипа проекта и сохранить его как закрытый делегат, так как только объект конфигурации проекта базового проекта непосредственно знает, что объект конфигурации подтипа проекта оболочки существует. Внешний подтип проекта может изначально выбрать интерфейсы конфигурации, которые требуется напрямую обменять, а затем делегировать оставшуюся реализацию внутреннего подтипа проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Вспомогательные интерфейсы

Базовый проект делегирует вызовы вспомогательных интерфейсов, добавленных подтипом проекта, для расширения различных аспектов его реализации. Сюда входит расширение объектов конфигурации проекта и различные объекты обозревателя свойств. Эти интерфейсы извлекаются путем вызова `QueryInterface` в `punkOuter` (указатель на `IUnknown` ) внешнего агрегатора подтипа проекта.

|Интерфейс|Подтип проекта|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Позволяет подтипу проекта:<br /><br /> — Предоставьте реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />— Управление запуском отладчика, позволяя подтипу проекта предоставлять собственную реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />— Отключение вычисления выражений во время разработки путем соответствующей обработки `DBGLAUNCH_DesignTimeExprEval` варианта в его реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Позволяет подтипу проекта:<br /><br /> — Расширение <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> проекта для добавления или удаления независимых от конфигурации свойств проекта.<br />— Расширение объекта автоматизации проекта ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ).<br /><br /> Приведенные выше значения свойств берутся из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> перечисления.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Позволяет подтипу проекта сопоставляться с <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> объектом, заданным объектом просмотра конфигурации проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Позволяет подтипу проекта сопоставляться с <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объектом или с `VSITEMID` заданным объектом просмотра конфигурации проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Позволяет подтипу проекта сохранять произвольные структурированные данные XML в файл проекта (VBPROJ или CSPROJ). Эти данные не видны в MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Позволяет подтипу проекта:<br /><br /> — Добавьте новые свойства MSBuild, которые должны быть сохранены.<br />— Удаление ненужных свойств из MSBuild.<br />— Запросить текущее значение свойства MSBuild.<br />— Изменение текущего значения свойства MSBuild.|

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
