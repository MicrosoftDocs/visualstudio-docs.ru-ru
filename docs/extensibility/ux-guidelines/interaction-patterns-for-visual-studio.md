---
title: Шаблоны взаимодействия для Visual Studio | Документация Майкрософт
description: Сведения о библиотеке распространенных шаблонов взаимодействия, которые можно использовать при создании новых функций для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: reference
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a2ec4332cf8010dc5d214dfd61936725ac2063
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900555"
---
# <a name="interaction-patterns-for-visual-studio"></a>Шаблоны взаимодействия для Visual Studio
## <a name="overview"></a>Обзор
 Шаблон разработки, как правило, является ядром проекта, который можно применять в конкретных ситуациях для решения проблем с аналогичными наборами ограничений. Конструкторы функций и систем используют эти конструктивные шаблоны в качестве начальных точек, которые затем можно адаптировать к конкретной ситуации.

 В Visual Studio имеется библиотека распространенных шаблонов взаимодействия, которые следует учитывать при создании новых функций. Существуют два основных контекста для шаблонов разработки: Visual Studio Client (devenv) и GitHub Кодеспацес (ранее — Visual Studio Online). Для некоторых проблем проектирования существует повсеместный шаблон, который хорошо работает во всех ситуациях. Однако во многих случаях решение может отличаться для пользовательского интерфейса, представленного в браузере и размещенного в клиентском приложении.

### <a name="visual-studio-client-pattern-types"></a>Типы клиентских шаблонов Visual Studio

|Тип шаблона|Описание|Примеры|
|------------------|-----------------|--------------|
|**Шаблоны уровня приложения**|Шаблоны высокого уровня, общие для приложения, определяющие или отображающие контекст приложения, а также содержащие составные шаблоны и элементы управления в них|— Окна инструментов<br />— Окна документов|
|**Составные шаблоны**|Общие шаблоны, которые могут охватывать несколько шаблонов приложений, или распознанный шаблон, состоящие из нескольких элементов управления в отдельной конфигурации.|— Переключение представлений<br />-Построители списков<br />-Отображение данных<br />— Уведомления<br />— Проверка<br />-Модели выбора|
|**Шаблоны элементов управления**|Особенности, которые должны вести себя элементы управления низкого уровня|— Представления в виде дерева<br />-Редактирование в элементе управления "Сетка"|

## <a name="application-patterns"></a>Шаблоны приложений
 На высоком уровне интерфейс Visual Studio состоит из нескольких окон, диалоговых окон, команд и панелей инструментов в одной интегрированной среде разработки. Иерархия Visual Studio определяет контекстные меню и диски. Основными точками интеграции в пользовательском интерфейсе IDE являются окна документов, окна инструментов, проекты, структура команд, текстовый редактор, панель элементов, окно свойств и средства > параметры.

 Существуют основные шаблоны использования для каждой из ключевых точек интеграции в пользовательском интерфейсе интегрированной среды разработки:

- [Меню и команды для Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Шаблоны приложений для Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Взаимодействие окон](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Окна инструментов](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Соглашения редактора документов](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Диалоги](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Проекты](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Общие шаблоны элементов управления
 Шаблоны элементов управления главным образом определяют, как должны вести себя отдельные элементы управления. Это одна область, в которой наиболее критична согласованность.

 Большинство стандартных элементов управления в Visual Studio должны соответствовать рекомендациям для настольных систем Windows. Наши рекомендации включают только те области, в которых нам нужно дополнить распространенные соглашения при взаимодействии с Visual Studio, или места, в которых мы полностью заменяем правила, чтобы адаптировать Visual Studio в соответствии с потребностями наших опытных пользователей.

- [Шаблоны распространенных элементов управления для Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Общие элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Текстовые элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Кнопки и гиперссылки](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Составные шаблоны
 Существует несколько способов, с помощью которых пользователи хотят выполнять задачи. Везде, где это возможно, функции должны быть разработаны для использования этих шаблонов как для взаимодействия, так и для визуального проектирования.

 Хотя в Visual Studio существует множество составных шаблонов, некоторые из них наиболее важны в отношении согласованности:

- [Составные шаблоны для Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Пользовательский интерфейс для объекта и просмотр](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Модели выбора](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Параметры сохраняемости и сохранения](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Сенсорный ввод](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
