---
title: Установка пакетов VSPackage с помощью установщик Windows | Документация Майкрософт
description: Узнайте, как использовать Microsoft установщик Windows для установки VSPackage и зависимых файлов, а также для регистрации и интеграции их в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1638f6d041dda28ca79492ba2c8e6ef772ce8bc7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074672"
---
# <a name="installing-vspackages-with-windows-installer"></a>Установка пакетов VSPackage с помощью установщика Windows
Интеграция пакета VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] требует больше, чем просто копирование файлов на компьютер пользователя. Установщик VSPackage должен установить пакет VSPackage и зависимые от него файлы, а также зарегистрировать и интегрировать их в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Пакет VSPackage может использовать преимущества функций интеграции, таких как отображение значка на [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] экране-заставке и диалоговом окне о программе.

 Файлы Microsoft установщик Windows являются рекомендуемым способом распространения пакетов VSPackage. Простые в использовании пакеты установщик Windows могут работать в любой операционной системе Windows, поддерживаемой [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Дополнительные сведения см. в разделе [установщик Windows](/previous-versions/2kt85ked(v=vs.120)).

## <a name="in-this-section"></a>в этом разделе
- [Основные сведения об установщике Windows](../../extensibility/internals/windows-installer-basics.md)

 Содержит общие сведения о установщик Windows.

- [Сценарии установки VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Обсуждаются различные способы поддержки параллельной установки как пакетов VSPackage, так и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Создание пакета установщика Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Общие сведения о стандартных шагах установки, которые следует выполнить для правильной установки и интеграции пакетов VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)

 Описывает, как установщик может обнаружить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и его компоненты, и отменить установку, если требования VSPackage не выполнены.

- [Управление компонентами](../../extensibility/internals/component-management.md)

 Описывает, как разработать установщик, который будет поддерживать целостность предыдущих версий продукта.

- [Выбор каталога установки для VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Содержит сводку параметров для поиска пакетов VSPackage.

- [Регистрация VSPackage](../../extensibility/internals/vspackage-registration.md)

 Описывает, как пакеты VSPackage регистрируются во время установки и почему самостоятельная регистрация является неправильной идеей.

- [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)

 Описывает, как использовать новый агрегатор типа проекта для типов проектов управляемого кода.

- [Практическое руководство. Создание сведений реестра для установщика](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Объясняется, как использовать RegPkg.exe для создания манифеста регистрации для управляемого пакета VSPackage.

- [Команды, которые необходимо выполнить после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Объясняет, как выполнять команды после установки для интеграции пакетов VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Удаление пакета VSPackage с помощью установщика Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Описание шагов, которые должен выполнить установщик при удалении пакета VSPackage.