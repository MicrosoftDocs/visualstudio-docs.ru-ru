---
title: Сравнение папки проекта с хранилищем системы управления версиями | Документация Майкрософт
description: В интерфейсе API подключаемого модуля системы управления версиями сравнение между локальной папкой проекта и системой управления версиями осуществляется с помощью Сккдиркуеринфо и Сккдирдифф.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7b334bb6e1b73dd31060020378e91b74e5af102
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063049"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Необязательное сравнение папки локального проекта с системой управления версиями
В API подключаемого модуля системы управления версиями 1,2 Сравнение между локальной папкой проекта и системой управления версиями осуществляется с помощью функций [сккдиркуеринфо](../../extensibility/sccdirqueryinfo-function.md) и [сккдирдифф](../../extensibility/sccdirdiff-function.md).

 В **Обозреватель решений**, если вместо отдельного файла выбрана папка, контекстное меню **Compare Versions** вызывает New [сккдиркуеринфо](../../extensibility/sccdirqueryinfo-function.md) и [сккдирдифф](../../extensibility/sccdirdiff-function.md) в подключаемом модуле системы управления версиями.

## <a name="new-capability-flags"></a>Новые флаги возможностей
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Новые функции
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 `SccDirQueryInfo`Функция вызывается до того, как `SccDirDiff` определить, является ли рабочий каталог управляемым источником. `SccDirDiff`Функция отображает различия между текущим локальным каталогом и соответствующей папкой системы управления версиями. Эта команда запрашивает у подключаемого модуля системы управления версиями список изменений, внесенных в каталог. Подключаемый модуль системы управления версиями предоставляет собственный пользовательский интерфейс для просмотра различий.

> [!NOTE]
> Эта функция использует те же флаги команд, что и [сккдифф](../../extensibility/sccdiff-function.md). В качестве поставщика подключаемого модуля системы управления версиями вы можете не поддерживать операцию быстрого поиска в каталогах.

## <a name="see-also"></a>См. также
- [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
