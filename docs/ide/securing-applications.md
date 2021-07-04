---
title: безопасность
description: Сведения о концепциях и функциях безопасности, которые могут помочь эффективно разрабатывать безопасные приложения.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3dcd034a76fbc371c95a2bbf386687830e3b63d
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687659"
---
# <a name="secure-applications"></a>Защита приложений

Вопросы безопасности должны рассматриваться на всех этапах разработки приложения — от проектирования до развертывания. Начните работу с запуска Visual Studio в наиболее безопасном режиме. См. раздел [Разрешения пользователей](../ide/user-permissions-and-visual-studio.md).

Для успешной разработки безопасного приложения следует ознакомиться с основными понятиями безопасности и средствами защиты платформ, для которых разрабатывается приложение. Кроме того, необходимо понимать приемы безопасного кодирования.

## <a name="code-for-security"></a>Безопасность кода

Большинство ошибок кодирования, которые приводят к уязвимости системы безопасности, происходит из-за неправильных допущений разработчиков при работе с вводимыми пользователем данными или из-за неполного понимания принципов работы платформы, для которой разрабатывается приложение.

- [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines) описывают различные способы разработки кода .NET, взаимодействующего с системой безопасности.
- [Рекомендации по безопасности для C++](/cpp/top/security-best-practices-for-cpp) содержат сведения об инструментах и методиках обеспечения безопасности для разработчиков C++.

## <a name="build-for-security"></a>Безопасность сборки

При сборке безопасность играет немаловажную роль. Выполнив дополнительные процедуры, можно повысить безопасность развернутого приложения и защитить его от несанкционированного реконструирования, спуфинга и других атак:

- Бесплатное решение [Dotfuscator](dotfuscator/index.md) служит для защиты сборок .NET от реконструирования и несанкционированного использования, такого как несанкционированная отладка.
- [Подписывание с использованием строгих имен](managing-assembly-and-manifest-signing.md) можно применять для уникальной идентификации программных компонентов и предотвращения спуфинга имен.

## <a name="see-also"></a>См. также раздел

- [Безопасность в .NET](/dotnet/standard/security/index)
- [Безопасность в Azure](/azure/security/)
- [Руководство по безопасности системы Windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Функции безопасности платформы Apache Cordova](/previous-versions/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017&preserve-view=true)
- [Безопасность ASP.NET Core](/aspnet/core/security/?view=aspnetcore-2.1&preserve-view=true)
- [Безопасность Windows Forms](/dotnet/framework/winforms/windows-forms-security)
