---
title: Создание подключаемого модуля системы управления версиями | Документация Майкрософт
description: Узнайте, как создать подключаемый модуль системы управления версиями, который добавляет возможности системы управления версиями в интегрированную среду разработки Visual Studio (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc302ee7327740380bb02e28c99e5117c926c7bc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056900"
---
# <a name="create-a-source-control-plug-in"></a>Создание подключаемого модуля системы управления версиями
Пакет SDK для Visual Studio предоставляет ресурсы, позволяющие добавлять возможности системы управления версиями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированную среду разработки (IDE). Он позволяет использовать любую подключаемую библиотеку DLL, которая соответствует интерфейсу API подключаемого модуля системы управления версиями, описанному в этой документации.

## <a name="in-this-section"></a>Содержание раздела
- [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Описывает, как установить подключаемый модуль системы управления версиями и выделить доступные в настоящее время версии API подключаемого модуля системы управления версиями.

- [Архитектура](../../extensibility/internals/source-control-plug-in-architecture.md)

 Использует схему архитектуры для объяснения интеграции подключаемого модуля системы управления версиями с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной средой разработки.

- [Тестовый обзор](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Содержит рекомендации по тестированию установки и эксплуатации подключаемого модуля системы управления версиями.

## <a name="related-sections"></a>Связанные разделы
- [Создание пакета VSPackage для системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Описывает, как создать пакет VSPackage системы управления версиями, который не только обеспечивает функциональность системы управления версиями, но и заменяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Пользовательский интерфейс системы управления версиями.

- [Подключаемые модули системы управления версиями](../../extensibility/source-control-plug-ins.md)

 Содержит полный список всех элементов в интерфейсе API подключаемого модуля системы управления версиями.

- [Система управления версиями](../../extensibility/internals/source-control.md)

 Описывает варианты реализации системы управления версиями в качестве интегрированной функции [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
