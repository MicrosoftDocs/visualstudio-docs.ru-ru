---
title: Создание пакета VSPackage для системы управления версиями | Документация Майкрософт
description: Узнайте, как создать пакет VSPackage системы управления версиями, который создает путь глубокой интеграции для системы управления версиями для интеграции с Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1085275427aeb02a767a66088ee58ced890dcb05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056861"
---
# <a name="create-a-source-control-vspackage"></a>Создание пакета VSPackage для системы управления версиями
Эта документация содержит ссылки на обзор архитектуры пакета управления версиями, интегрированного с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , API, который определяется реализуемыми интерфейсами и используемыми службами, а также пример, иллюстрирующий простую реализацию пакета управления версиями.

 С помощью пакета VSPackage системы управления версиями можно создать путь к глубокой интеграции для системы управления версиями, с которой будет осуществляться интеграция [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Он позволяет пакету обходить пользовательский интерфейс системы управления версиями по умолчанию [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , отвечающий на запросы к системе управления версиями, и взаимодействовать с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] такими компонентами, как **Обозреватель решений**. Предоставляет [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] партнерам механизм создания пакета VSPackage, который может интегрироваться с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] моделью службы.

## <a name="in-this-section"></a>Содержание раздела
- [Начало работы](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Описывает пакет управления версиями, который является более сложной альтернативой подключаемому модулю системы управления версиями для реализации функций системы управления версиями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Архитектура](../../extensibility/internals/source-control-vspackage-architecture.md)

 Представлена схема и объясняются компоненты пакета системы управления версиями.

- [Функции](../../extensibility/internals/source-control-vspackage-features.md)

 Описывает различные функции пакета системы управления версиями.

- [Элементы дизайна](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Описывает структуру VSPackage, которую должен реализовать пакет системы управления версиями для глубокой интеграции.

## <a name="related-sections"></a>Связанные разделы
- [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Описывает создание подключаемого модуля системы управления версиями, предоставляющего функции управления версиями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательском интерфейсе системы управления версиями.

- [Система управления версиями](../../extensibility/internals/source-control.md)

 Описывает варианты реализации системы управления версиями в качестве интегрированной функции [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
