---
title: Расширение меню и команд | Документация Майкрософт
description: Сведения о командах, которые добавляют действия и процессы в Visual Studio. Шаблон проекта VSPackage показывает, как реализовать очень простую команду.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a96978cdad45c669b607c18e12b2e492dcf95bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075215"
---
# <a name="extend-menus-and-commands"></a>Расширение меню и команд
Команды — это способ добавления действий и процессов в Visual Studio. В большинстве случаев команды отображаются в меню или на панелях инструментов. Шаблон проекта VSPackage показывает, как реализовать очень простую команду. Несколько более длинную, но все еще базовую реализацию см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

 Дополнительные сведения о командах, меню и панелях инструментов Visual Studio см. в разделе [команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).

 Команды, меню и панели инструментов определяются в *vsct* -файле, который является частью проектов VSPackage. Сведения о интегрированной среде разработки Visual Studio и файле *. vsct* см. в статье [Добавление элементов пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 В следующих разделах описывается добавление различных типов команд, меню и панелей инструментов.

## <a name="in-this-section"></a>Содержание раздела
- [Добавление меню в строку меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Объясняет, как добавить меню в верхнюю строку меню Visual Studio.

- [Привязка сочетаний клавиш к](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) пунктам меню Объясняет, как добавить сочетание клавиш (например, CTRL + 3) к пункту меню.

- [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md) Объясняет, как добавить подменю в верхнее меню.

- [Добавление списка недавно использовавшихся в подменю](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Объясняет, как добавить список недавно использованных.

- [Создание многократно используемых групп кнопок](../extensibility/creating-reusable-groups-of-buttons.md) Описывает, как группировать элементы команд, чтобы их можно было включить в несколько меню.

- [Добавление значков к командам меню](../extensibility/adding-icons-to-menu-commands.md) Описывает, как добавить значок в команду на панели инструментов и в меню.

- [Изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md) Описывает использование `TextChanges` флага для динамического изменения элемента меню.

- [Изменение внешнего вида команды](../extensibility/changing-the-appearance-of-a-command.md) Описание динамического включения или отключения команды.

- [Обновление пользовательского интерфейса](../extensibility/updating-the-user-interface.md) Описывает принудительное обновление пользовательского интерфейса для отражения последних изменений.

- [Команды меню "локализовать](../extensibility/localizing-menu-commands.md) " Объясняет, как локализовать команды меню.
