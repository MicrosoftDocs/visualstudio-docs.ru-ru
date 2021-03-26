---
title: Управление загрузкой проекта в решении | Документация Майкрософт
description: Узнайте, как разработчики могут сократить время загрузки решения и управлять поведением при загрузке проекта, создав диспетчер загрузки решения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 425f610e8a473460cb7d9170138521e2e7bee08a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073096"
---
# <a name="manage-project-loading-in-a-solution"></a>Управление загрузкой проекта в решении
Решения Visual Studio могут содержать большое количество проектов. Поведение Visual Studio по умолчанию — загружать все проекты в решении во время открытия решения, а не разрешать пользователю обращаться к каким-либо проектам до завершения загрузки всех этих проектов. Когда процесс загрузки проекта будет более двух минут, отображается индикатор выполнения, отображающий количество загруженных проектов и общее число проектов. Пользователь может выгружать проекты при работе в решении с несколькими проектами, но эта процедура имеет некоторые недостатки: выгруженные проекты не строятся в составе команды Rebuild Solution, а описания IntelliSense типов и членов закрытых проектов не отображаются.

 Разработчики могут сократить время загрузки решения и управлять поведением загрузки проекта, создав диспетчер загрузки решения. Диспетчер загрузки решения может обеспечить загрузку проектов перед началом фоновой сборки, отложить фоновую загрузку до завершения других фоновых задач и выполнить другие задачи по управлению загрузкой проекта.

## <a name="create-a-solution-load-manager"></a>Создание диспетчера загрузки решения
 Разработчики могут создать диспетчер загрузки решения, реализовав и предприняв <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> Visual Studio, что диспетчер загрузки решения активен.

### <a name="activate-a-solution-load-manager"></a>Активация диспетчера загрузки решения
 Visual Studio допускает только один диспетчер загрузки решения в определенный момент времени, поэтому необходимо рекомендовать Visual Studio, если нужно активировать Диспетчер загрузки решения. Если второй диспетчер загрузки решения будет активирован позже, диспетчер загрузки решения будет отключен.

 Необходимо получить <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> службу и задать [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) свойство:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Метод вызывается либо при завершении работы Visual Studio, либо при использовании другого пакета в качестве активного диспетчера загрузки решения путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> с помощью [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) свойство.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Стратегии для различных типов диспетчера нагрузки решений
 Вы можете реализовать диспетчеры загрузки решений различными способами в зависимости от типов решений, которыми они предназначены для управления.

 Если диспетчер нагрузки решения предназначен для управления загрузкой решения в целом, его можно реализовать как часть VSPackage. Для пакета необходимо задать значение автозагрузки, добавив в <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> VSPackage со значением <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Диспетчер загрузки решения может быть активирован в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> методе.

> [!NOTE]
> Дополнительные сведения о пакетах автозагрузки см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).

 Поскольку Visual Studio распознает только последний диспетчер загрузки решения, который должен быть активирован, общие диспетчеры загрузки решений всегда должны определять наличие существующего диспетчера, прежде чем активировать его. При вызове `GetProperty()` в службе решения для [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) возвращает `null` , активный диспетчер загрузки решений отсутствует. Если он не возвращает значение null, проверьте, совпадает ли объект с диспетчером загрузки решения.

 Если диспетчер загрузки решения предназначен для управления только решениями нескольких типов, пакет VSPackage может подписываться на события загрузки решения (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) и использовать обработчик событий для <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> активации диспетчера загрузки решения.

 Если диспетчер загрузки решения предназначен для управления только конкретными решениями, сведения об активации можно сохранить как часть файла решения, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> для раздела предварительной версии решения.

 Определенные диспетчеры загрузок решений должны деактивироваться в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> обработчике событий, чтобы не конфликтовать с другими диспетчерами загрузки решений.

 Если диспетчер загрузки решения необходим только для сохранения свойств загрузки глобальных проектов (например, для свойств, заданных на странице параметров), можно активировать Диспетчер загрузки решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> обработчике событий, сохранить параметр в свойствах решения, а затем отключить диспетчер загрузки решения.

## <a name="handle-solution-load-events"></a>Обработку событий загрузки решения
 Чтобы подписываться на события загрузки решения, вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> при активации диспетчера загрузки решения. При реализации можно <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> реагировать на события, связанные с различными свойствами загрузки проекта.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Это событие возникает перед открытием решения.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Это событие возникает после полной загрузки решения, но до начала фоновой загрузки проекта.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Это событие возникает после первоначальной загрузки решения, независимо от наличия диспетчера загрузки решения. Он также срабатывает после загрузки в фоновом режиме или по требованию, когда решение становится полностью загруженным. В то же время <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> активируется повторно.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Это событие возникает перед загрузкой проекта (или проектов). Чтобы обеспечить завершение других фоновых процессов до загрузки проектов, установите значение `pfShouldDelayLoadToNextIdle` **true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Это событие возникает при загрузке пакета проектов. Если `fIsBackgroundIdleBatch` имеет значение true, проекты должны загружаться в фоновом режиме; Если значение `fIsBackgroundIdleBatch` равно false, проекты должны загружаться синхронно в результате запроса пользователя, например, если пользователь развертывает ожидающий проект в Обозреватель решений. Это событие можно обрабатывать, чтобы выполнять дорогостоящую работу, которая в противном случае должна быть выполнена в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Это событие возникает после загрузки пакета проектов.

## <a name="detect-and-manage-solution-and-project-loading"></a>Обнаружение и управление загрузкой решений и проектов
 Чтобы определить состояние загрузки проектов и решений, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> со следующими значениями:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` возвращает значение `true` , если решение и все его проекты загружены. в противном случае — значение `false` .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` возвращает `true` , если пакет проектов в данный момент загружается в фоновом режиме. в противном случае — значение `false` .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` возвращает значение `true` , если пакет проектов в данный момент загружается синхронно в результате выполнения пользовательской команды или другой явной загрузки `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` возвращает значение `true` , если решение в данный момент закрывается, в противном случае — `false` .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` возвращает значение `true` , если решение открыто в данный момент; в противном случае — `false` .

Также можно убедиться, что проекты и решения загружены, вызвав один из следующих методов:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: вызов этого метода приводит к принудительной загрузке проектов в решении перед возвратом метода.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: вызов этого метода приводит к принудительной `guidProject` загрузке проектов в перед возвратом из метода.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: вызов этого метода приводит к принудительной `guidProjectID` загрузке проекта в перед возвратом метода.
