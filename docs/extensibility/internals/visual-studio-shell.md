---
title: Оболочка Visual Studio | Документация Майкрософт
description: Оболочка Visual Studio является основным агентом интеграции в Visual Studio и предоставляет базовые функциональные возможности и поддерживает перекрестную связь между пакетами VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5dafd90294fd0968c78846d4162c1ff02c584f3f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074344"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Оболочка является основным агентом интеграции в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Оболочка предоставляет необходимые функции, позволяющие использовать пакеты VSPackage для совместного использования общих служб. Поскольку цель архитектуры заключается в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] том, чтобы направить в пакеты VSPackage основную функциональность, оболочка — это платформа для обеспечения базовой функциональности и поддержки перекрестной связи между компонентами пакетов VSPackage.

## <a name="shell-responsibilities"></a>Обязанности оболочки
 Оболочка имеет следующие ключевые обязанности:

- Поддержка (через COM-интерфейсы) основных элементов пользовательского интерфейса. К ним относятся меню и панели инструментов по умолчанию, рамки окон документов или дочерние окна многодокументного интерфейса (MDI), а также рамки окон инструментов и поддержка закрепления.

- Поддержание текущего списка всех открытых документов в работающей таблице документов (РДТ) для координации сохраняемости документов и обеспечения того, что один документ не может быть открыт несколькими способами или в несовместимых направлениях.

- Поддержка маршрутизации команд и интерфейса обработки команд `IOleCommandTarget` .

- Загрузка пакетов VSPackage в соответствующее время. Отложенная загрузка VSPackage необходима для повышения производительности оболочки.

- Управление определенными общими службами, такими как <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> , предоставляющей основные функциональные возможности оболочки, и, предоставляющее <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> базовые функциональные возможности для работы с окнами.

- Управление файлами решения (SLN). Решения содержат группы связанных проектов, аналогичные файлам рабочей области (DSW) в Visual C++ 6,0.

- Отслеживание выбора, контекста и валюты для всей оболочки. Оболочка отслеживает следующие типы элементов:

  - Текущий проект

  - Текущий элемент проекта или Идентификатор ItemID текущего <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Текущий выбор для окна " **Свойства** " или `SelectionContainer`

  - Идентификаторы контекста пользовательского интерфейса или Кмдуигуидс, управляющие видимостью команд, меню и панелей инструментов

  - Активные в данный момент элементы, такие как активное окно, документ и диспетчер отмены

  - Атрибуты контекста пользователя, которые управляют динамической справкой

  Оболочка также устраняет связь между установленными пакетами VSPackage и текущими службами. Он поддерживает основные функции оболочки и делает их доступными для всех пакетов VSPackage, интегрированных в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . К этим основным функциям относятся следующие компоненты.

- Диалоговое окно " **о программе** " и экран-заставка

- Диалоговое окно " **Добавление новых и Добавление существующих элементов** "

- Обозреватель окон и **объектов** **представление классов**

- Диалоговое окно " **ссылки** "

- Окно **структуры документа**

- Окно **динамической справки**

- **Поиск** и **Замена**

- **Открытие** диалоговых окон "проект" и " **Открыть файл** " в меню " **создать** "

- Диалоговое окно " **Параметры** " в меню " **Сервис** "

- Окно " **Свойства** "

- **Обозреватель решений**

- Окно **список задач**

- **Панель элементов**

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
