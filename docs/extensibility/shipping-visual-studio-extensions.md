---
title: Доставка расширений Visual Studio | Документация Майкрософт
description: Узнайте, как опубликовать и поддерживать расширение пакета SDK для Visual Studio, включая работу с файлами VSIX, публикацией, локализацией и обновлением.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c88c80ffbc1e80815b8370a940a75c0eb197ff78
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090139"
---
# <a name="shipping-visual-studio-extensions"></a>Доставка расширений Visual Studio
После завершения разработки расширения вы можете установить его на других компьютерах, поделиться им с вашими друзьями и сотрудниками или опубликовать на Visual Studio Marketplace. В этом разделе описываются все вещи, необходимые для публикации и обслуживания расширения: работа с файлами VSIX, публикация, локализация и обновление.

## <a name="working-with-vsix-extensions"></a>Работа с расширениями VSIX
 Расширения VSIX можно создать, создав пустой проект VSIX, а затем добавив в него различные шаблоны элементов. Дополнительные сведения см. в разделе [шаблон проекта VSIX](../extensibility/vsix-project-template.md).

 Формат VSIX можно использовать для упаковки шаблонов проектов, шаблонов элементов, пакетов VSPackage, Managed Extensibility Framework (MEF), элементов управления **панели элементов** , сборок и пользовательских типов (включая пользовательские начальные страницы для Visual Studio 2017). Формат VSIX использует развертывание на основе файлов. Дополнительные сведения о пакетах VSIX см. [в разделе Анатомия пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Формат VSIX не поддерживает установку фрагментов кода. Он также не поддерживает некоторые другие сценарии, такие как запись в глобальный кэш сборок (GAC) или в системный реестр. Если необходимо выполнить запись в глобальный кэш сборок или в реестр в установке, необходимо использовать установщик Windows. Дополнительные сведения см. в разделе [Подготовка расширений для установщик Windows развертывания](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Публикация расширения в Visual Studio Marketplace
 Вы можете распространить расширение другим людям, просто передавая им VSIX-файл или поместив его на сервер. Но лучший способ получить код в практических занятиях — поместить его в [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Для пользователей Visual Studio доступны расширения Visual Studio Marketplace с помощью **расширений и обновлений**. Дополнительные сведения см. в разделе [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Полный пример, демонстрирующий передачу расширения в Visual Studio Marketplace, см. в разделе [Пошаговое руководство. публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 При разработке элементов управления, шаблонов и средств вы можете поделиться ими с Организацией, разместив их в частную галерею в интрасети. Дополнительные сведения см. в разделе [частные галереи](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Локализация расширения
 Если вы планируете выпустить расширение в разных языковых стандартах, рекомендуется локализовать его. Объяснение того, что участвует в этой статье, см. в разделе [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Обновление и управление версиями вашего расширения
 После публикации расширения появится время, когда необходимо обновить его. Чтобы узнать, как обновить расширение, опубликованное в Visual Studio Marketplace, см. статью [как обновить расширение](../extensibility/how-to-update-a-visual-studio-extension.md).

 Вы можете настроить расширение для поддержки нескольких версий Visual Studio. Дополнительные сведения см. в разделе [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Начало работы с шаблоном проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Объясняется, как использовать шаблон проекта VSIX для установки пользовательского шаблона проекта.|
|[Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Описывает компоненты пакета VSIX.|
|[Шаблон проекта VSIX](../extensibility/vsix-project-template.md)|Содержит пошаговые инструкции по упаковке и публикации расширения.|
|[Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)|Объясняет, как предоставить локализованный текст для процесса установки с помощью файлов extension. всикслангпакк.|
|[Практическое руководство: обновление расширения](../extensibility/how-to-update-a-visual-studio-extension.md)|Описывает, как обновить расширение в системе и как развернуть обновление для существующего расширения Visual Studio.|
|[Практическое руководство. Добавление зависимости в пакет VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Описывает добавление ссылок в пакеты развертывания VSIX.|
|[Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|В этой статье объясняется, как развернуть расширение с помощью установщик Windows.|
|[Подписывание пакетов VSIX](../extensibility/signing-vsix-packages.md)|Описывает, как подписывать пакеты VSIX.|
|[Частные галереи](../extensibility/private-galleries.md)|Описание создания частных коллекций для расширений.|
|[Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Показывает, как расширение поддерживает несколько версий Visual Studio.|
|[Обнаружение Visual Studio](locating-visual-studio.md)|Описание процесса размещения экземпляров Visual Studio для пользовательского развертывания расширения.|
