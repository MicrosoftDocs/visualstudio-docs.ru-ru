---
title: Команды и меню, использующие сборки взаимодействия | Документация Майкрософт
description: Сведения о задачах, которые должны быть выполнены при реализации команд меню и панелей инструментов в VSPackage с помощью сборок взаимодействия.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5a487c2fe6f97e338924a0b8c682f9dd9798571
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057238"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Команды и меню, использующие сборки взаимодействия
Пакет VSPackage, который реализует команды меню и панели инструментов с помощью сборок взаимодействия, должен:

- Сообщите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) о поддерживаемых командах и о том, включены ли они в данный момент.

- Придерживайтесь правил (контракта) для обработки команд.

- Явная реализация обработки команд с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейса или.

  В следующем разделе описывается выполнение этих задач.

## <a name="in-this-section"></a>Содержание раздела
- [Определение состояния команды с помощью сборок взаимодействия](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Описывает, как VSPackage уведомляет интегрированную среду разработки о том, какие команды она поддерживает, и включены ли они в данный момент.

- [Контракты команд в сборках взаимодействия](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Предоставляет определение базового контракта команды, используемого всеми пакетами VSPackage, которые реализуют команды с помощью сборок взаимодействия.

- [Реализация команды](../../extensibility/internals/command-implementation.md)

 Содержит общие сведения о том, как VSPackage реализует команду.

- [Регистрация обработчиков команд сборки взаимодействия](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Описание записей реестра, необходимых для уведомления интегрированной среды разработки о том, что пакет VSPackage предоставляет обработчик команд.

## <a name="related-sections"></a>Связанные разделы
- [Доступность команды](../../extensibility/internals/command-availability.md)

 Описывает критерии, которые используются интегрированной средой разработки для определения доступности команд VSPackage и объектов, которые их обрабатывает.

- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Содержит сведения о создании пользовательского интерфейса, использующего [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддержку команды.

- [Маршрутизация команд в пакетах VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)

 Обзор процесса, используемого для связи объекта с правильным запросом команды.
