---
title: Как реализовать вложенные проекты | Документация Майкрософт
description: Сведения о реализации вложенных проектов в Visual Studio путем вызова событий из решения и родительских проектов для построения иерархии проектов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 49f2e3b971c16b63f900424aa99649e424490d30
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078868"
---
# <a name="how-to-implement-nested-projects"></a>Руководство. Реализация вложенных проектов

При создании вложенного типа проекта необходимо реализовать несколько дополнительных действий. Родительский проект принимает некоторые из тех же обязанностей, которые имеет решение для вложенных (дочерних) проектов. Родительский проект — это контейнер проектов, аналогичный решению. В частности, существует несколько событий, которые должны быть вызваны решением и родительскими проектами для построения иерархии вложенных проектов. Эти события описаны в следующем процессе создания вложенных проектов.

## <a name="create-nested-projects"></a>Создание вложенных проектов

1. Интегрированная среда разработки (IDE) загружает файл проекта родительского проекта и сведения о запуске путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> интерфейса. Родительский проект создается и добавляется в решение.

    > [!NOTE]
    > На этом этапе в процессе создания вложенного проекта в родительском проекте слишком рано или поздно, так как родительский проект должен быть создан до того, как дочерние проекты могут быть созданы. После выполнения этой последовательности родительский проект может применять параметры к дочерним проектам, и дочерние проекты могут при необходимости получать сведения из родительских проектов. Эта последовательность необходима для клиентов, таких как система управления исходным кодом (SCC) и **Обозреватель решений**.

     Родительский проект должен ожидать <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> вызова метода интегрированной средой разработки, прежде чем он сможет создать вложенный (дочерний) проект или проекты.

2. Среда IDE вызывает `QueryInterface` родительский проект для <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . Если этот вызов будет выполнен, интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> метод родительского элемента, чтобы открыть все вложенные проекты для родительского проекта.

3. Родительский проект вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> метод для уведомления прослушивателей о создании вложенных проектов. Например, SCC прослушивает эти события, чтобы убедиться в том, что шаги в процессе создания решения и проекта выполняются по порядку. Если действия выполняются не по порядку, решение может быть неправильно зарегистрировано в системе управления исходным кодом.

4. Родительский проект вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> метод или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> метод для каждого из его дочерних проектов.

     Передайте <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> метод, `AddVirtualProject` чтобы указать, что виртуальный (вложенный) проект должен быть добавлен в окно проекта, исключен из сборки, добавлен в систему управления исходным кодом и т. д. `VSADDVPFLAGS` позволяет управлять видимостью вложенного проекта и указывать, какие функции связаны с ним.

     При перезагрузке ранее существующего дочернего проекта с идентификатором GUID проекта, хранящимся в файле проекта родительского проекта, родительский проект вызывает `AddVirtualProjectEx` . Единственное различие между `AddVirtualProject` и `AddVirtualProjectEX` состоит в том, что имеет параметр, позволяющий `AddVirtualProjectEX` родительскому проекту указывать для каждого экземпляра `guidProjectID` дочернего проекта, который должен быть включен <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> правильно функционировать.

     Если идентификатор GUID недоступен, например, при добавлении нового вложенного проекта, решение создает его для проекта во время добавления в родительский проект. Родительский проект несет ответственность за сохранение идентификатора GUID проекта в файле проекта. При удалении вложенного проекта идентификатор GUID для этого проекта также можно удалить.

5. Интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> метод для каждого дочернего проекта родительского проекта.

     Родительский проект должен быть реализован, `IVsParentProject` Если нужно вложить проекты. Но родительский проект никогда не `QueryInterface` вызывает `IVsParentProject` , даже если у него есть родительские проекты под ним. Решение обрабатывает вызов функции `IVsParentProject` и, если он реализован, вызывается `OpenChildren` для создания вложенных проектов. `AddVirtualProjectEX` метод всегда вызывается из `OpenChildren` . Он никогда не должен вызываться родительским проектом для сохранения порядка событий создания иерархии.

6. Интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> метод для дочернего проекта.

7. Родительский проект вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> метод для уведомления прослушивателей о том, что дочерние проекты для родителя были созданы.

8. Интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> метод родительского проекта после открытия всех дочерних проектов.

     Если он еще не существует, родительский проект создает идентификатор GUID для каждого вложенного проекта путем вызова `CoCreateGuid` .

    > [!NOTE]
    > `CoCreateGuid` — Это COM-API, вызываемый при создании идентификатора GUID. Дополнительные сведения см `CoCreateGuid` . в разделе и идентификаторы GUID в библиотеке MSDN.

     Родительский проект сохраняет этот GUID в файле проекта для извлечения при следующем открытии в интегрированной среде разработки. Дополнительные сведения о вызове метода для `AddVirtualProjectEX` получения `guidProjectID` для дочернего проекта см. в разделе Шаг 4.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Затем метод вызывается для родительского элемента ItemId, который в соответствии с соглашением делегируется вложенному проекту. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Возвращает свойства узла, который вкладывает проект, в который необходимо делегировать, при вызове в родительском объекте.

     Так как экземпляры родительских и дочерних проектов создаются программно, на этом этапе можно установить свойства для вложенных проектов.

    > [!NOTE]
    > Вы можете не только получить сведения о контексте из вложенного проекта, но и узнать, есть ли в родительском проекте контекст для этого элемента, проверив [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). Таким образом можно добавить дополнительные атрибуты динамической справки и параметры меню, относящиеся к отдельным вложенным проектам.

10. Иерархия строится для вывода в **Обозреватель решений** с вызовом <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> метода.

     Иерархия передается в среду с помощью `GetNestedHierarchy` для построения иерархии для вывода в Обозреватель решений. Таким образом, решение знает, что проект существует и может управляться построением с помощью диспетчера сборок, или может разрешить размещение файлов в проекте в системе управления исходным кодом.

11. После создания всех вложенных проектов для проект1 управление передается обратно в решение, а процесс повторяется для Project2.

     Этот же процесс создания вложенных проектов происходит для дочернего проекта, у которого есть дочерний проект. В этом случае, если BuildProject1, который является дочерним по отношению к проект1, имел дочерние проекты, они будут созданы после BuildProject1 и до Project2. Процесс является рекурсивным, и иерархия строится сверху вниз.

     При закрытии вложенного проекта, поскольку пользователь закрыл решение или сам проект, вызывается другой метод метода `IVsParentProject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> . Родительский проект инкапсулирует вызовы к <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> методу с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> методов и для уведомления прослушивателей о событиях решения о закрытии вложенных проектов.

В следующих разделах рассматриваются некоторые другие концепции, которые следует учитывать при реализации вложенных проектов.

- [Рекомендации по выгрузке и перезагрузке вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Реализация обработки команд для вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Фильтрация диалогового окна AddItem для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>См. также

- [Добавление элементов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Контрольный список: создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Файл мастера (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
