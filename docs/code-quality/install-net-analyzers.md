---
title: Включение или установка сторонних анализаторов .NET
ms.date: 08/03/2018
description: Узнайте, как включить сторонние анализаторы .NET из пакета SDK для .NET или установить эти анализаторы как пакет NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 368fd5bc9c8b7e2659c86b6e3dc69a609da37617
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144667"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Включение или установка сторонних анализаторов .NET

## <a name="overview"></a>Обзор

Анализаторы .NET Compiler Platform (Roslyn) проверяют качество кода C# или Visual Basic и выявляют в нем проблемы. Сторонние анализаторы .NET не зависят от **платформы**. То есть проект не обязан ориентироваться на конкретную платформу .NET. Анализаторы работают для проектов, предназначенных для, а также для `net5.0` более ранних версий .NET, таких как `netcoreapp` , `netstandard` и `net472` .

Включить или установить первую версию анализаторов .NET можно одним из следующих способов.

- **Включение из пакета SDK для .NET**: начиная с Visual Studio 2019 16,8 и .NET 5,0, эти анализаторы [входят в состав пакета SDK для .NET](/dotnet/fundamentals/code-analysis/overview). По умолчанию для проектов, предназначенных для .NET 5,0 или более поздней версии, включен анализ. Вы можете включить анализ кода для проектов, предназначенных для более ранних версий .NET, задав для свойства [ЕНАБЛЕНЕТАНАЛИЗЕРС](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) MSBuild значение `true` . Можно также отключить анализ кода для проекта, задав для значение `EnableNETAnalyzers` `false` .

- **Установить как пакет NuGet**. Если вы не хотите переходить на пакет SDK для .NET 5 + или если предпочитаете использовать модель на основе пакетов NuGet, анализаторы также доступны в `Microsoft.CodeAnalysis.NetAnalyzers` [пакете nuget](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) в Visual Studio 2019.  Вы можете предпочесть модели на основе пакетов для обновления версий по требованию. Если вы используете Visual Studio 2017, установите последнюю `2.9.x` версию `Microsoft.CodeAnalysis.FxCopAnalyzers` [пакета NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) .

> [!NOTE]
> Рекомендуется включить анализаторы из пакета SDK для .NET, а не устанавливать `Microsoft.CodeAnalysis.NetAnalyzers` [пакет NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), если это возможно. При включении анализаторов из пакета SDK для .NET автоматически получаются исправления ошибок анализатора и новые анализаторы, как только вы обновите пакет SDK. В модели NuGet необходимо обновлять пакет NuGet каждый раз, когда необходимо устранить последние исправления ошибок. Пакет NuGet обновляется чаще.

## <a name="see-also"></a>См. также раздел

- [Обзор анализаторов кода в Visual Studio](roslyn-analyzers-overview.md)
- [Использование анализаторов кода в Visual Studio](use-roslyn-analyzers.md)
- [Миграция с анализа прежних версий на анализаторы .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Миграция с анализаторов FxCop на анализаторы .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
