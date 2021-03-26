---
title: Вклад в модель автоматизации | Документация Майкрософт
description: Узнайте, как внести вклад в модель автоматизации Visual Studio, следуя набору рекомендаций при проектировании VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44da0c91eb425cbd558aea4335447f9293684b90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057043"
---
# <a name="contribute-to-the-automation-model"></a>Участие в модели автоматизации
Visual Studio предоставляет набор интерфейсов автоматизации для настройки среды. Модель автоматизации — это объектная модель, позволяющая конечным пользователям создавать надстройки и расширения Visual Studio.

 Кроме того, в качестве разработчика VSPackage подходит для участия в модели автоматизации. Это позволит пользователям пакета VSPackage создавать надстройки и, как правило, обеспечить единообразную модель пользователя при использовании VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Чтобы обеспечить единообразное взаимодействие с конечным пользователем, вы можете следовать набору рекомендаций по разработке пакета VSPackage, чтобы модель автоматизации пакета VSPackage соответствовала идеям в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Содержание раздела
- [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)

 Определяет модель автоматизации как связанные группы объектов, которые управляют основными аспектами общей среды. Этот набор объектов изображен на схеме модели автоматизации.

- [Предоставление автоматизации для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)

 Обсуждаются два основных способа предоставления автоматизации для VSPackage.

- [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)

 Содержит пошаговые инструкции по созданию объектов, зависящих от VSPackage.

- [Моделирование проекта](../../extensibility/internals/project-modeling.md)

 Описание стандартных объектов проекта, необходимых для создания автоматизации для нового типа проекта, и показан путь, который следует за автоматизацией проекта. В этом разделе также приводятся списки объявлений и реализации классов.

- [Предоставление событий](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Содержит пошаговые инструкции по созданию событий для модели автоматизации.

- [Поддержка автоматизации для страниц параметров](../../extensibility/internals/automation-support-for-options-pages.md)

 Описывает, как вернуть объект автоматизации для поддержки свойств диалогового окна пользовательских **параметров** VSPackage в меню **инструментов** , расширив `DTE.Properties` объект.

- [Предоставление автоматизации для кода](../../extensibility/internals/providing-automation-for-code.md)

 Объясняется, что создание модели автоматизации для кода не является обязательным. Однако в этом разделе приведена ссылка, которая предоставляет сведения о моделях кода.

- [Руководство. предоставление автоматизации для Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Объясняется, что предоставление автоматизации является хорошей идеей при необходимости сделать объекты автоматизации доступными в окне, а среда еще не предоставляет готовый объект автоматизации. Описывает автоматизацию для окон инструментов и окон документов.

- [Использование модели автоматизации](../../extensibility/internals/using-the-automation-model.md)

 Содержит два примера кода, демонстрирующих, как потребитель автоматизации получает исходные объекты автоматизации проекта.

- [Автоматизация для объектов Configuration и SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Предоставляет сведения об автоматизации для объектов Configuration и SelectedItems.

## <a name="reference"></a>Справочник
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Содержит пример кода, показывающий, как VSPackage участвует в объектной модели автоматизации DTE. Перечисляет параметры, возвращаемые значения и выбранные примечания.
