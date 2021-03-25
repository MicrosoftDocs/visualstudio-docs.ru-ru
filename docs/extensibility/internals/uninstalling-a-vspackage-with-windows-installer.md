---
title: Удаление VSPackage с установщик Windows | Документация Майкрософт
description: Установщик Windows можете удалить пакет VSPackage, отменив установку. Узнайте, как работать с настраиваемыми действиями в пакете установщик Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb5d0fe0e4812d66f6981ea58dfb51f19336d98b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090724"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Удаление пакета VSPackage с помощью установщика Windows
В большинстве случаев установщик Windows может удалить пакет VSPackage, просто отменив его, чтобы установить пакет VSPackage. Пользовательские действия, описанные в [командах, которые должны быть выполнены после установки,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) должны быть выполнены и после удаления. Поскольку вызовы devenv.exe происходят непосредственно перед стандартным действием функции InstallFinalize как для установки, так и для удаления, записи в таблице CustomAction и Инсталлексекутесекуенце служат обоим случаям.

> [!NOTE]
> Запустите `devenv /setup` после удаления пакета MSI.

 Как правило, при добавлении настраиваемых действий в пакет установщик Windows необходимо выполнять эти действия во время удаления и отката. При добавлении настраиваемых действий для самостоятельной регистрации пакета VSPackage, например, необходимо добавить настраиваемые действия, чтобы отменить его регистрацию.

> [!NOTE]
> Пользователь может установить пакет VSPackage, а затем удалить версии, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с которыми он интегрируется. Чтобы убедиться в том, что удаление VSPackage работает в этом сценарии, следует исключить пользовательские действия, которые выполняют код с зависимостями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Обработка условий запуска во время удаления
 Стандартное действие Лаунчкондитионс считывает строки таблицы Лаунчкондитион для отображения сообщений об ошибках, если условия не выполнены. Поскольку условия запуска обычно используются для обеспечения соответствия требованиям к системе, обычно можно пропустить условия запуска во время удаления, добавив условие, `NOT Installed` в строку лаунчкондитионс таблицы лаунчкондитион.

 Альтернативой является добавление `OR Installed` в условия запуска, которые не важны во время удаления. Это гарантирует, что условие будет всегда истинно во время удаления, и поэтому не отобразит сообщение об ошибке условия запуска.

> [!NOTE]
> `Installed` Свойство установщик Windows задается при обнаружении того, что пакет VSPackage уже установлен в системе.

## <a name="see-also"></a>См. также
- [Установщик Windows](/previous-versions/ee231230(v=vs.100))
- [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)