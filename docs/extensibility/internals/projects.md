---
title: Проекты | Документация Майкрософт
description: Узнайте о том, как пакеты VSPackage могут расширять систему проектов Visual Studio, включая типы проектов, подтипы проектов и пользовательские инструменты.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73f685707d6c9f7a8b40bb57c5207c6a538fd1f4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081026"
---
# <a name="projects"></a>Проекты
В Visual Studio проекты — это контейнеры, используемые разработчиками для организации файлов исходного кода и других ресурсов, которые отображаются в **Обозреватель решений**. Как правило, проекты — это файлы (например, CSPROJ-файл для проекта C#), которые хранят ссылки на файлы исходного кода и ресурсы, такие как растровые файлы. Проекты позволяют упорядочивать, собирать, отлаживать и развертывать исходный код, ссылки на веб-службы и базы данных, а также другие ресурсы. Пакеты VSPackage могут расширять систему проектов Visual Studio тремя основными способами: *типы проектов*, *подтипы проектов* и *пользовательские инструменты*.

## <a name="in-this-section"></a>в этом разделе
- [Типы проектов](../../extensibility/internals/project-types.md)

 *Типы проектов* добавляют поддержку новых типов проектов, таких как языки программирования. Например, каждый язык, поддерживаемый Visual Studio, имеет собственный тип проекта, а пример интеграции IronPython включает тип проекта для языка IronPython. Необходимо создать тип проекта для языков, отличных от C# или Visual Basic, чтобы настроить построение, отладку, развертывание и отображение элементов в **Обозреватель решений**. Дополнительные сведения см. в разделе [типы проектов](../../extensibility/internals/project-types.md).

- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)

 *Подтипы проектов* основываются на типах проектов и могут использоваться для настройки способа построения, отладки и развертывания проектов. Visual Studio использует подтипы проектов для проектов смарт-устройств; они настраивают развертывание путем копирования недавно созданной программы с компьютера разработчика на целевое устройство. Типы проектов C# и Visual Basic можно использовать в качестве базиса для подтипов проектов. Типы проектов C++ не могут. Собственные типы проектов также можно использовать в качестве базиса для подтипов проектов. Дополнительные сведения см. в разделе [Project подтипы](../../extensibility/internals/project-subtypes.md).

- [Веб-проекты](../../extensibility/internals/web-projects.md)

 Описывает веб-проект, который, в свою очередь, создает веб-приложения.

- Создание [новых проектов.](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) в рамках этой части одна и [Новая версия проекта: внутри, часть 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Объясняет, что происходит при создании нового проекта.

- [Примеры VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Содержит примеры в VSSDK, которые работают с проектами и решениями.

## <a name="related-sections"></a>Связанные разделы
- [Компоненты пакета SDK для Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Объясните различные аспекты расширения среды Visual Studio.
