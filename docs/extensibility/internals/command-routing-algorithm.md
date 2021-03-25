---
title: Алгоритм маршрутизации команд | Документация Майкрософт
description: Сведения о порядке разрешения команд в Visual Studio, так как команды обрабатываются различными компонентами и направляются из самого внутреннего контекста в самый внешний.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e02493cbb2f872806ade33d77609d45d1938ccd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057316"
---
# <a name="command-routing-algorithm"></a>Алгоритм маршрутизации команд
В командах Visual Studio обрабатывается с помощью ряда различных компонентов. Команды направляются из самого внутреннего контекста, основанного на текущем выделении, к самому внешнему (также известному как глобальному) контексту. Дополнительные сведения см. в разделе [доступность команды](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Порядок разрешения команд
 Команды передаются через следующие уровни контекста команды:

1. Надстройки. среда сначала предоставляет команду для всех имеющихся надстроек.

2. Приоритетные команды. Эти команды регистрируются с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Они вызываются для каждой команды в Visual Studio и вызываются в том порядке, в котором они были зарегистрированы.

3. Команды контекстного меню: команда, расположенная в контекстном меню, сначала предлагается для целевого объекта команды, предоставленного контекстному меню, и после этого для обычной маршрутизации.

4. Целевые объекты команды панели инструментов. Эти целевые объекты команды регистрируются при вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . `pCmdTarget`Параметр может иметь значение `null` . Если это не так `null` , то этот целевой объект команды используется для обновления всех команд, расположенных на заданной панели инструментов. Если оболочка настраивает панель инструментов, она передается в качестве, `pCmdTarget` чтобы все обновления команд на панели инструментов передавались через рамку окна, даже если она не находится в фокусе.

5. Окно инструментов. окна инструментов, которые обычно реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс, должны также реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, чтобы Visual Studio мог получить целевой объект команды, когда окно инструментов является активным. Однако если окно инструментов, в котором находится фокус, является окном **проекта** , команда направляется к <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейсу, который является общим родителем выбранных элементов. Если этот выбор охватывает несколько проектов, команда направляется в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> иерархию. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Интерфейс содержит <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> методы и, которые аналогичны соответствующим командам в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейсе.

6. Окно документа. Если для команды `RouteToDocs` установлен флаг в *vsct* -файле, Visual Studio выполняет поиск целевого объекта команды в объекте представления документа, который является либо экземпляром <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейса, либо экземпляром объекта документа (обычно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейсом или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейсом). Если объект представления документа не поддерживает команду, Visual Studio направляет команду в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> возвращаемый интерфейс. (Это необязательный интерфейс для объектов данных документа.)

7. Текущая иерархия: текущая иерархия может быть проектом, владеющем активным окном документа, или иерархией, выбранной в **Обозреватель решений**. Visual Studio ищет <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, реализованный в текущей или активной иерархии. Иерархия должна поддерживать команды, которые являются допустимыми при активной иерархии, даже если окно документа элемента проекта имеет фокус. Однако команды, применяемые только в том случае, если в **Обозреватель решений** должен поддерживаться фокус, используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейс и его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> методы и.

     Для команд **вырезания**, **копирования**, **вставки**, **удаления**, **переименования**, **ввода** и **DoubleClick** требуется специальная обработка. Дополнительные сведения об обработке команд **Delete** и **Remove** в иерархиях см. в описании <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> интерфейса.

8. Глобальный. Если команда не была обработана ранее упомянутыми контекстами, Visual Studio пытается направить его в пакет VSPackage, который владеет командой, реализующей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс. Если пакет VSPackage еще не загружен, он не загружается, когда Visual Studio вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. Пакет VSPackage загружается только при <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> вызове метода.

## <a name="see-also"></a>См. также
- [Проектирование команд](../../extensibility/internals/command-design.md)
