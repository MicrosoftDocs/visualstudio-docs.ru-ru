---
title: Поддержка системы управления версиями | Документация Майкрософт
description: Узнайте, как Visual Studio поддерживает извлечение, возвраты и другие операции с системой управления версиями для проекта или редактора.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 56880cab310367a5c4da3af0cf310867a5519495
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080610"
---
# <a name="supporting-source-control"></a>Поддержка системы управления версиями
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает извлечение файлов, возвраты и другие операции системы управления версиями для проекта или редактора. Как клиент системы управления версиями, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предназначен для взаимодействия с пакетом управления версиями, например [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , который обеспечивает архивацию, управление версиями и средства управления для динамически определяемого набора файлов.

## <a name="in-this-section"></a>в этом разделе
- [Модель для пакетов системы управления версиями](../../extensibility/internals/model-for-source-control-packages.md)

 Описывает интерфейсы, которые должен реализовать тип проекта для поддержки системы управления версиями.

- [Проектные решения](../../extensibility/internals/source-control-design-decisions.md)

 Предоставляет вопросы, ответы на которые меняются при реализации типа проекта.

- [Сведения о конфигурации](../../extensibility/internals/source-control-configuration-details.md)

 Описывает, как поддерживающая управление версиями изменяет реализацию типа проекта.

- [Дополнительные рекомендации для проектов и редакторов](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Обсуждаются рекомендации по типам проектов и редакторам.

- [Сведения о среде выполнения](../../extensibility/internals/source-control-runtime-details.md)

 Описывает, как зарегистрировать проект при его добавлении пользователем в систему управления версиями.

## <a name="reference"></a>Справочник
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Указывает среде или пакету системы управления версиями, что файл будет изменен в памяти или сохранен.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> Позволяет проектам и иерархиям регистрировать себя в системе управления версиями и получать сведения о состоянии системы управления версиями.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Реализован в системе проектов для обеспечения системы управления версиями файлов проектов и элементов проектов.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Используется проектами для запроса к среде разрешения на добавление, удаление или переименование файла или каталога в решении.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> Уведомляет клиентов об изменениях, внесенных в файлы проекта или каталоги.

## <a name="related-sections"></a>Связанные разделы
- [Типы проектов](../../extensibility/internals/project-types.md)

 Содержит общие сведения о проектах в качестве основных стандартных блоков [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Имеются ссылки на дополнительные разделы, объясняющие, как проекты управляют сборкой и компиляцией кода.
