---
title: IDE-Defined команд, меню и групп | Документация Майкрософт
description: Сведения о меню, командах и группах команд, которые определены в интегрированной среде разработки Visual Studio (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b88bbab9c92cdd8627521eaa58284fd33964b7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085953"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Команды, меню и группы, определенные в интегрированной среде разработки
Многие меню, команды и группы команд уже определены для использования [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной средой разработки. Эти команды также доступны для использования при расширении [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Поиск команд Environment-Defined
 Команды среды определены в наборе из четырех vsct-файлов:

- Шаредкмддеф. vsct

- Шаредкмдплаце. vsct

- Шеллкмддеф. vsct

- Шеллкмдплаце. vsct

  Эти файлы находятся в *\<Visual Studio SDK installation path>* \висуалстудиоинтегратион\коммон\инк \\ . Эти файлы содержат определения и идентификаторы GUID меню и групп, которые можно использовать в файле конфигурации командной таблицы (. vsct) пакета VSPackage в качестве контейнеров для собственных меню, групп и команд.

## <a name="in-this-section"></a>в этом разделе
- [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Предоставляет значения GUID и идентификатора меню в строке меню Visual Studio и содержащихся в них группах.

- [Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Предоставляет идентификатор GUID и значения идентификатора панелей инструментов в интегрированной среде разработки Visual Studio и содержащихся в них групп.

- [Идентификаторы GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Предоставляет идентификаторы GUID и ИДЕНТИФИКАТОРы команд, определенных интегрированной средой разработки Visual Studio.

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
