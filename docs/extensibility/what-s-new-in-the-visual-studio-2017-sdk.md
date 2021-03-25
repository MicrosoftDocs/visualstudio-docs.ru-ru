---
title: '&apos;Новые возможности пакета SDK для Visual Studio 2017 | Документация Майкрософт'
description: В пакете SDK для Visual Studio есть новые и обновленные функции Visual Studio 2017, включая обновленный формат VSIX версии 3.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5a1e34ac23a0e6c298dae14c1613e7af0fc7b25d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061931"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Новые&#39;пакета SDK для Visual Studio 2017

Пакет SDK для Visual Studio содержит следующие новые и обновленные функции Visual Studio 2017.

## <a name="vsix-v3-format"></a>Формат VSIX v3

Для поддержки новой неплотной установки Visual Studio 2017 формат манифеста расширения VSIX был обновлен до версии 3 (VSIX v3).

Новый формат имеет поддержку:

* Явное объявление необходимых компонентов для обнаружения и установки с помощью Всиксинсталлер.
* Сборки NGen при установке расширения.
* Установка ресурсов за пределами обычного корня расширения.

Дополнительные сведения об этих изменениях см. в следующих разделах:

* [Изменения в расширяемости Visual Studio 2017](breaking-changes-2017.md)
* [Поддержка NGen в VSIX v3](ngen-support.md)
* [Установка за пределами папки расширений](set-install-root.md)
* [Часто задаваемые вопросы о расширяемости Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Перенос проекта расширения среды в Visual Studio 2017

Сведения о том, как обновить проекты расширяемости и их манифесты VSIX в Visual Studio 2017, см. в разделе [как перенести проекты расширяемости в Visual studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Пользовательские шаблоны проектов и элементов

Начиная с Visual Studio 2017 проверка наличия пользовательских шаблонов проектов и элементов больше не будет выполняться. Вместо этого расширение должно предоставлять файлы манифеста шаблона, в которых указано расположение установки этих шаблонов. Для обновления расширений VSIX можно использовать Visual Studio 2017. При развертывании расширения с помощью MSI необходимо создать файлы манифеста шаблона вручную. Дополнительные сведения см. в статье [Обновление пользовательских шаблонов проектов и элементов для Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Схема манифеста шаблона описана в [Справочнике по схемам манифестов шаблонов Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Обновленные рекомендации по повышению производительности расширений

В разделе Управление пакетами [VSPackage](managing-vspackages.md) содержится новая статья [о производительности расширения](how-to-diagnose-extension-performance.md) , в которой показано, как обнаруживать и анализировать влияние расширения на запуск Visual Studio и время загрузки решения.
