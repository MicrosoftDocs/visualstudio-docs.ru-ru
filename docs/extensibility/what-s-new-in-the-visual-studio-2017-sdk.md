---
title: '&apos;новые возможности пакета SDK для Visual Studio 2017 | Документация Майкрософт'
description: в пакете SDK для Visual Studio есть новые и обновленные функции для Visual Studio 2017, включая обновленный формат VSIX версии 3.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0b0b7852fa7e20f4ee6951e57c5c19f4b5454028
ms.sourcegitcommit: 3c6c263a1c0b20f084290ce45295a46027da33b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2021
ms.locfileid: "113756902"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>новые&#39;пакета SDK для Visual Studio 2017

пакет SDK для Visual Studio содержит следующие новые и обновленные функции для Visual Studio 2017.

## <a name="vsix-v3-format"></a>Формат VSIX v3

для поддержки новой неплотной установки Visual Studio 2017 формат манифеста расширения VSIX обновлен до версии 3 (VSIX v3).

Новый формат имеет поддержку:

* Явное объявление необходимых компонентов для обнаружения и установки с помощью Всиксинсталлер.
* Сборки NGen при установке расширения.
* Установка ресурсов за пределами обычного корня расширения.

Дополнительные сведения об этих изменениях см. в следующих разделах:

* [изменения в расширяемости для Visual Studio 2017](breaking-changes-2017.md)
* [Поддержка NGen в VSIX v3](ngen-support.md)
* [Установка за пределами папки расширений](set-install-root.md)
* [часто задаваемые вопросы о расширяемости Visual Studio 2017](faq-2017.yml)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>перенос проекта расширяемости в Visual Studio 2017

чтобы узнать, как обновить проекты расширяемости и манифесты VSIX до Visual Studio 2017, см. статью [как перенести проекты расширяемости в Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Пользовательские шаблоны проектов и элементов

Начиная с Visual Studio 2017 проверка наличия пользовательских шаблонов проектов и элементов больше не будет выполняться. Вместо этого расширение должно предоставлять файлы манифеста шаблона, в которых указано расположение установки этих шаблонов. Для обновления расширений VSIX можно использовать Visual Studio 2017. При развертывании расширения с помощью MSI необходимо создать файлы манифеста шаблона вручную. дополнительные сведения см. в статье [обновление пользовательских шаблонов проектов и элементов для Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Схема манифеста шаблона описана в [Справочнике по схемам манифестов шаблонов Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Обновленные рекомендации по повышению производительности расширений

в разделе управление пакетами [vspackage](managing-vspackages.md) содержится новая статья [о производительности расширения](how-to-diagnose-extension-performance.md) , в которой показано, как обнаружить и проанализировать влияние расширения на Visual Studio запуска и времени загрузки решения.
