---
title: Рекомендации по обеспечению безопасности в VSPackage | Документация Майкрософт
description: Узнайте о рекомендациях по обеспечению безопасности в VSPackage, базовой единице безопасности и развертывании для приложения Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cca66d6c1fce0deb8103a7d626c16a4e81bc7b5f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086213"
---
# <a name="best-practices-for-security-in-vspackages"></a>Рекомендации по обеспечению безопасности в VSPackage
Чтобы установить [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] на компьютере, необходимо работать в контексте с административными учетными данными. Основной единицей безопасности и развертывания [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] приложения является пакет [VSPackage](../../extensibility/internals/vspackages.md). Пакет VSPackage должен быть зарегистрирован с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , который также требует учетных данных администратора.

 Администраторы имеют полные разрешения на запись в реестр и файловую систему, а также на выполнение любого кода. Эти разрешения необходимы для разработки, развертывания или установки пакета VSPackage.

 Как только оно будет установлено, VSPackage будет полностью доверенным. Из-за такого высокого уровня разрешений, связанных с VSPackage, можно случайно установить пакет VSPackage, имеющий вредоносную намерение.

 Пользователи должны убедиться, что они устанавливают пакеты VSPackage только из надежных источников. Компании, разрабатывающих пакеты VSPackage, должны строго присвоить имя и подписать их, чтобы предотвратить фальсификацию пользователя. Компании, разрабатывающих пакеты VSPackage, должны исследовать свои внешние зависимости, такие как веб-службы и удаленная установка, для анализа и устранения любых проблем безопасности.

 Дополнительные сведения см. [в разделе рекомендации по безопасному кодированию для платформа .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>См. также
- [Безопасность надстроек](/previous-versions/1326zbk3(v=vs.140))
- [Безопасность DDEX](/previous-versions/bb163703(v=vs.140))