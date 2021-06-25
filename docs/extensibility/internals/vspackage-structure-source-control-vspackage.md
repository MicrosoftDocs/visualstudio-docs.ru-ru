---
title: Структура VSPackage (пакет VSPackage системы управления версиями) | Документация Майкрософт
description: Узнайте о пакете SDK для пакетов управления версиями, который содержит рекомендации для пакета VSPackage с реализацией системы управления версиями для интеграции с Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b95c382342675d79c0c6e854b5fc087d495827e2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898826"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Структура VSPackage (пакет VSPackage системы управления версиями)

Пакет SDK пакета системы управления версиями содержит рекомендации по созданию VSPackage, позволяющему разработчику системы управления версиями интегрировать свои функции управления версиями с средой Visual Studio. VSPackage — это COM-компонент, который обычно загружается по запросу интегрированной средой разработки (IDE) Visual Studio на основе служб, объявленных пакетом в записях реестра. Каждый пакет VSPackage должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Пакет VSPackage обычно использует службы, предлагаемые интегрированной средой разработки Visual Studio, и профферс некоторые службы.

Пакет VSPackage объявляет свои пункты меню и устанавливает состояние элемента по умолчанию с помощью файла. vsct. Интегрированная среда разработки Visual Studio отображает пункты меню в этом состоянии до тех пор, пока не будет загружен пакет VSPackage. Затем <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> для включения или отключения пунктов меню вызывается реализация метода VSPackage.

## <a name="source-control-package-characteristics"></a>Характеристики пакета системы управления версиями

Пакет VSPackage для системы управления версиями тесно интегрирован в Visual Studio. Семантика VSPackage включает в себя следующее:

- Интерфейс, который должен быть реализован с помощью VSPackage ( `IVsPackage` интерфейс)

- Реализация команд пользовательского интерфейса (vsct-файл и реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса)

- Регистрация пакета VSPackage в Visual Studio.

Пакет VSPackage системы управления версиями должен взаимодействовать с этими другими сущностями Visual Studio:

- Проекты

- Редакторы

- Решения

- Windows

- Таблица выполняющегося документа

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Службы среды Visual Studio, которые могут быть использованы

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Служба СвсрегистерскЦипровидер

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Реализованные и вызываемые интерфейсы VSIP

Пакет управления версиями — это VSPackage, поэтому он может напрямую взаимодействовать с другими пакетами VSPackage, зарегистрированными в Visual Studio. Чтобы обеспечить полный спектр функций управления версиями, пакет VSPackage системы управления версиями может работать с интерфейсами, предоставляемыми проектами или оболочкой.

Каждый проект в Visual Studio должен <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> быть реализован для распознавания как проект в интегрированной среде разработки Visual Studio. Однако этот интерфейс не является достаточно специализированным для системы управления версиями. Проекты, которые должны находиться в системе управления версиями, реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Этот интерфейс используется пакетом VSPackage системы управления версиями для запроса содержимого проекта и предоставления ему глифов и сведений о привязке (сведения, необходимые для установления соединения между расположением сервера и расположением на диске проекта, который находится в системе управления версиями).

Пакет VSPackage для системы управления версиями реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , который, в свою очередь, позволяет проектам регистрировать себя для системы управления версиями и извлекать их глифы состояния.

Полный список интерфейсов, которые должен учитывать пакет VSPackage системы управления версиями, см. в разделе [связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>См. также

- [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
