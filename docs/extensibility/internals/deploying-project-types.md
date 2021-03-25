---
title: Развертывание типов проектов | Документация Майкрософт
description: Узнайте, как развертывать типы проектов с управляемым кодом с помощью нового агрегатора типа проекта и установщик Windows пакета для повторного распространения в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121dda58b8e01c5b0029d8b3c93ef66d2657446e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090997"
---
# <a name="deploy-project-types"></a>Развертывание типов проектов
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] устанавливает новый агрегатор типа проекта (*ProjectAggregator2.dll*), а также пакет установщик Windows для распространения (*ProjectAggregator2.msi*). Для типов проектов с управляемым кодом необходимо использовать новый агрегатор. ProjectAggregator2 работает с ограничениями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] агрегаторе проекта, что предотвращает неправильную работу типов проектов управляемого кода. Следующие шаги описывают, как изменить пакет VSPackage для использования новой агрегаторы.

1. Удалите проект Нативехиерарчивраппер из решения.

2. Удалите из программы установки все двоичные файлы Нативехиерарчивраппер.

3. Добавьте *ProjectAggregator2.msi* в программу установки.
