---
title: Определение состояния команды с помощью сборок взаимодействия | Документация Майкрософт
description: Узнайте, как определить состояние команд, обрабатываемых в VSPackage, с помощью интерфейса Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef6940aef83ad3865385b4e39fd9cfd62b8866d7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090906"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Определение состояния команды с помощью сборок взаимодействия
Пакет VSPackage должен отследить состояние команд, которые он может выполнять. Среда не может определить, когда команда, обрабатываемая в VSPackage, станет включенной или отключенной. Пакет VSPackage служит для информирования среды о состояниях команд, например о состоянии общих команд, таких как **вырезание**, **копирование** и **Вставка**.

## <a name="status-notification-sources"></a>Источники уведомлений о состоянии
 Среда получает сведения о командах через <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод VSPackage, который является частью реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса VSPackage. Среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод VSPackage в двух случаях:

- Когда пользователь открывает главное меню или контекстное меню (щелкнув правой кнопкой мыши), среда выполняет <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод для всех команд в этом меню, чтобы определить их состояние.

- Когда пакет VSPackage запрашивает обновление текущего пользовательского интерфейса в среде. Это обновление происходит как команды, видимые пользователю, такие как **вырезание**, **копирование** и **Вставка** группирования на стандартной панели инструментов, становятся доступными и отключаются в ответ на контекст и действия пользователя.

  Поскольку оболочка размещает несколько пакетов VSPackage, производительность интерпретатора команд будет неприемлемым, если бы требовалось опросить каждый пакет VSPackage для определения состояния команды. Вместо этого VSPackage должен активно уведомлять среду об изменении пользовательского интерфейса во время изменения. Дополнительные сведения о уведомлении об обновлении см. в разделе [Обновление пользовательского интерфейса](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Сбой уведомления о состоянии
 Сбой VSPackage для уведомления среды об изменении состояния команды может привести к непротиворечивости пользовательского интерфейса. Помните, что любое из меню или команд контекстного меню может быть размещено пользователем на панели инструментов. Поэтому обновление пользовательского интерфейса происходит только при открытии меню или контекстного меню.

## <a name="see-also"></a>См. также
- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Реализация](../../extensibility/internals/command-implementation.md)
