---
title: Добавление шаблонов проектов и элементов проектов | Документация Майкрософт
description: Сведения о добавлении шаблонов проектов и элементов проектов в диалоговые окна в интегрированной среде разработки Visual Studio (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3f2c10b310569a412025fd114f7818734106bc18
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079063"
---
# <a name="add-project-and-project-item-templates"></a>Добавление шаблонов проектов и элементов проектов
При создании собственных типов проектов необходимо обеспечить поддержку добавления новых проектов и элементов проектов с помощью стандартных [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диалоговых окон интегрированной среды разработки (IDE). В следующих разделах рассматриваются различные методы добавления проектов и элементов проектов.

## <a name="in-this-section"></a>Содержание раздела
- [Контекст проекта](../../extensibility/internals/project-context.md)

 Объясняет, что проект предоставляет большую часть контекстных сведений о том, что происходит в среде.

- [Приоритет проекта](../../extensibility/internals/project-priority.md)

 Объясняется, что элемент проекта обычно является членом одного проекта, чтобы избежать неоднозначности в том, какой проект используется для открытия элемента.

- [Проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md)

 Предоставляет сведения о двух типах редакторов, которые можно использовать для открытия файлов в проекте, и роль, которую играет проект при определении того, какой редактор следует использовать при открытии элемента проекта.

- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)

 Объясняет, что происходит при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] создании проекта.

- [Добавление элементов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Описание процесса добавления элементов в диалоговое окно " **Добавление нового элемента** ".

- [Добавление каталогов в диалоговое окно "новый проект"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Содержит пример регистрации нового каталога, содержащего пользовательские шаблоны, доступные в VSPackage.

- [Добавление каталогов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Содержит пример регистрации нового набора каталогов для диалогового окна **Добавление нового элемента** .

- [Команды, определяемые интегрированной средой разработки для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Список различных типов командных элементов, используемых для расширения систем проектов.

- [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Список CATID для объектов, используемых для расширения [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] систем проектов, и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .

## <a name="related-sections"></a>Связанные разделы
- [Пошаговое руководство. открытие редакторов, зависящих от проекта](../../extensibility/how-to-open-project-specific-editors.md)

 Содержит пошаговые инструкции по открытию элемента, привязанного к конкретному редактору для проекта.

- [Руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)

 Содержит пошаговые инструкции по открытию стандартного редактора.

- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)

 Содержит ссылки на основные разделы о подтипах проектов. Подтипы проектов расширяют существующие [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проекты и.

- [Типы проектов](../../extensibility/internals/project-types.md)

 Ссылки на дополнительные разделы, в которых содержатся сведения о проектировании новых типов проектов.
