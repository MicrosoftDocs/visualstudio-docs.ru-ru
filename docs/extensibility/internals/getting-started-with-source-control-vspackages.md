---
title: начало работы с пакетом VSPackage системы управления версиями | Документация Майкрософт
description: Сведения о пакетах VSPackage в системе управления версиями в Visual Studio и о том, как они являются более расширенной альтернативой подключаемым модулям системы управления версиями.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, getting started
- getting started, source control packages
ms.assetid: 049c68f4-a041-4f24-8575-4837e7f5cf3f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 163152e614cccfb2f2d46fdf68e0f4b9001b173c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061268"
---
# <a name="get-started-with-source-control-vspackages"></a>Приступая к работе с пакетом VSPackage в системе управления версиями

Пакет VSPackage системы управления версиями — это более сложная альтернатива подключаемому модулю системы управления версиями. Дополнительные сведения о подключаемых модулях системы управления версиями см. [в разделе Создание подключаемого модуля системы управления](../../extensibility/internals/creating-a-source-control-plug-in.md)версиями. Пакет VSPackage для управления исходным кодом обеспечивает полный контроль над моделью системы управления версиями, функциями и интерфейсом пользователя, а также интегрируется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среду как VSPackage.

## <a name="in-this-section"></a>Содержание раздела

[Определение необходимости реализации пакета VSPackage системы управления версиями](../../extensibility/internals/determining-whether-to-implement-a-source-control-vspackage.md)

Описывает варианты решений системы управления версиями и предоставляет широкие рекомендации по выбору соответствующего пути интеграции.

## <a name="related-sections"></a>Связанные разделы

- [Новые возможности системы управления версиями](../../extensibility/internals/what-s-new-in-source-control.md)

   Описание новых возможностей, использующих пакеты VSPackage с системой управления версиями.

- [Создание пакета VSPackage для системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

   Описывает, как создать пакет VSPackage системы управления версиями, который не только обеспечивает функциональность управления версиями, но и может использоваться для настройки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса системы управления версиями.
