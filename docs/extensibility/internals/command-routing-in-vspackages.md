---
title: Маршрутизация команд в пакетах VSPackage | Документация Майкрософт
description: Сведения о маршрутизации команд в пакетах VSPackage и способах маршрутизации команд в зависимости от контекста, в котором они выполняются в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35ab5e7989fdeb46592f38cb7e55854885e076d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057303"
---
# <a name="command-routing-in-vspackages"></a>Маршрутизация команд в пакетах VSPackage
Команда направляется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] зависимости от контекста, в котором она выполняется. Он направляется от первоначального контекста к глобальному контексту.

## <a name="in-this-section"></a>Содержание раздела
- [Алгоритм маршрутизации команд](../../extensibility/internals/command-routing-algorithm.md)

 Описывает порядок разрешения маршрутизации команд.

- [Доступность команды](../../extensibility/internals/command-availability.md)

 Обсуждается маршрутизация команд.

- [Команды и меню, использующие сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Обсуждаются вопросы в командах маршрутизации между управляемым кодом и COM.

## <a name="related-sections"></a>Связанные разделы
- [Объекты контекста выделения](../../extensibility/internals/selection-context-objects.md)

 Обсуждается модель того, как можно определить фокус контекста выбора пользователя в окне.

- [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.
