---
title: Основные компоненты модели проекта | Документация Майкрософт
description: В этой статье содержатся описания интерфейсов и служб, определенных в ядре модели проекта, а также интерфейсы и службы, связанные с объектами.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ae01d149611afe5bf75a6952f19baff7d70f6210
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062815"
---
# <a name="project-model-core-components"></a>Основные компоненты модели проекта
В следующих таблицах расширена модель проекта. В таблицах представлены краткие описания интерфейсов и служб, определенных в модели, а также интерфейсы и службы, связанные с определенными объектами. Кроме того, в таблицах подробно описываются другие интерфейсы, которые являются необязательными при создании и обслуживании проекта в зависимости от требований конкретного типа проекта.

 Дополнительные сведения см. в разделе [Поддержка средств Symbol-Browsing](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Объект Package

|Интерфейс|Комментарии|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Инициализирует VSPackage в интегрированной среде разработки и делает его службы доступными для интегрированной среды разработки.|

### <a name="project-factory-object"></a>Объект фабрики проектов

|Интерфейс|Комментарии|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Управляет созданием новых проектов и открытием существующих проектов.|

### <a name="project-objects"></a>Объекты проекта

|Интерфейсы|Комментарии|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Управляет добавлением и удалением элементов проекта, открывает редакторы и поддерживает сопоставление между каждым моникером документа и `VSITEMID` . Наследует от `IVsProject` и `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Управление навигацией и отображением свойств и предоставлением событий.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Включает выполнение команды аналогично тому, что `IOleCommandTarget` используется для таких команд, как Cut и Rename, которые применяются только в том случае, если фокус находится в Обозреватель решений.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Служит в качестве целевого интерфейса основной команды для иерархии проекта. Это стандартный интерфейс для запроса объектов состояния команды или состояния и выполнения команд. Доступно, если вы не сосредоточены в окне проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Координирует сохраняемость состояния проекта. Как правило, состояние проекта хранится в виде файла проекта, но может быть адаптировано к системам хранения, не основанным на файлах.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Позволяет проекту управлять всеми аспектами сохраняемости для элементов проекта, как файлами на дисках, так и объектами в других системах хранения. `IVsPersistHierarchyItem2`Интерфейс используется для элементов, которые не реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> интерфейс.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Координирует взаимодействие с системой управления исходным кодом.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Позволяет проектам управлять сведениями о конфигурации.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Управляет объектами конфигурации проекта, такими как конфигурации отладки и выпуска. Операции сборки, развертывания и отладки согласовываются с помощью объектов конфигурации проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Реализуется иерархиями для управления параметрами удаления (уничтожения) или удаления (неразрушающих) для элементов иерархии. Вызов интерфейса запроса интерфейса `IVsHierarchyDeleteHandler` из `IVsHierarchy` интерфейса.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Предоставляет параметр реализации для объекта, который поддерживает `IVsCfgProvider2` интерфейс на различных удостоверениях com, чем объект проекта, реализующий `IVsHierarchy` интерфейс.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Необязательный интерфейс, обеспечивающий расширение проекта другими разработчиками. `IVsProjectStartupServices`Интерфейс позволяет пакету VSPackage стороннего производителя зарегистрировать идентификатор GUID, который вы сохранили в файле проекта, чтобы каждый раз при загрузке проекта в файл проекта загрузился идентификатор GUID службы стороннего производителя и вызывался метод `QueryService` для этого идентификатора GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Реализуется исходными иерархиями в `UIHierarchy` окне для координации операций с буфером обмена, таких как вырезание, копирование и вставка. Используйте `AdviseClipboardHelperEvents` интерфейс для регистрации событий буфера обмена.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Предоставляет сведения о перемещенном элементе относительно его источника данных во время операции перетаскивания в окне иерархии пользовательского интерфейса. Вызывается из `IVsHierarchy` интерфейса.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Предоставляет сведения о перемещенном элементе относительно целевого объекта перетаскивания во время операции перетаскивания в окне иерархии пользовательского интерфейса. Вызывается из `IVsHierarchy` интерфейса.|

### <a name="configuration-object"></a>Объект конфигурации

|Интерфейсы|Комментарии|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Предоставляет сведения о конфигурации.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Позволяет проектам управлять сведениями о конфигурации.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Позволяет запускать проект под управлением отладчика.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Реализуется проектами развертывания, выполняющими операции развертывания для других проектов.|

### <a name="configuration-builder-object"></a>Объект построителя конфигурации

|Интерфейсы|Комментарии|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Управляет операцией построения конфигурации проекта.|

### <a name="additional-project-objects"></a>Дополнительные объекты проекта

|Интерфейсы|Комментарии|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Отображает свойства элемента в окне **Свойства** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Отображает выходные данные для развертывания.|

 В следующей таблице представлены краткие описания служб, определенных в модели проекта.

### <a name="services"></a>Службы

|Служба|Комментарии|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Используется пакетами VSPackage, которые реализуют типы проектов для регистрации, что их фабрика проектов существует в интегрированной среде разработки. Пакет VSPackage должен вызвать `QueryService` для этой службы и зарегистрировать фабрику проекта при `IVsPackage::SetSite` вызове метода. Если `SetSite` метод не вызывается, экземпляр проекта не создается.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Предоставляет доступ к внутреннему встроенному сопредставлению текущего решения интегрированной среды разработки, например возможность перечисления проектов, создания новых проектов, уведомления об изменениях проекта и т. д.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Вызывается проектами, которые хотят участвовать в системе управления версиями.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Поддерживает таблицу открытых документов, чтобы определить, открыты ли уже один или несколько элементов проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Содержит интерфейсы и методы, вызываемые для фактического открытия элемента проекта с помощью стандартного редактора или конкретного редактора.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Должен вызываться всеми проектами при добавлении, удалении или переименовании элементов.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Управляет изменениями в файле или каталоге и уведомляет клиентов, когда выбранные файлы были изменены на диске.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Должен вызываться всеми проектами и редакторами до их «грязных» элементов или их сохранения.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Управляет порядком операций сборки и развертывания для конфигураций проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Предоставляет доступ к службам отладчика низкого уровня, используемым для большинства элементов управления отладкой.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Включает доступ VSPackage к сведениям о текущем выборе и позволяет обмениваться данными с окном **свойств** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет базовые функции интегрированной среды разработки, связанные с пользовательским интерфейсом, такие как возможность создавать и перечислять окна инструментов или окна документов, а также сообщать пользователю об ошибке.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Предоставляет доступ к строке состояния интегрированной среды разработки.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Используется для реализации модели автоматизации. В модели проекта будет возвращен объект свойств, позволяющий создать экземпляр этого объекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Используется для реализации событий буфера обмена в объекте проекта в иерархии. `SVsUIHierWinClipboardHelper` позволяет правильно управлять операциями вырезания, копирования и вставки.|

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Контрольный список. Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Не в сборке. Использование классов проектов HierUtil7 для реализации типа проекта (C++)](/previous-versions/bb166212(v=vs.100))
- [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)