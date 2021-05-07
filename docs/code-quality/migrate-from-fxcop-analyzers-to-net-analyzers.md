---
title: Миграция с анализаторов FxCop на анализаторы .NET
ms.custom: SEO-VS-2020
description: Сведения о переходе с средств FxCop Analyzer на анализаторы .NET
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: d6f9c36b1b64abe648c3aa9014c633e4e4949b1a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798262"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Миграция с анализаторов FxCop на анализаторы .NET

Анализ исходного кода с помощью анализаторов .NET Compiler Platform ("Roslyn") заменяет [устаревший анализ](code-analysis-for-managed-code-overview.md) управляемому коду. Многие правила традиционного анализа (FxCop) уже были переписаны в качестве исходных анализаторов.

До Visual Studio 2019 16,8 и .NET 5,0 эти анализаторы поставляются как `Microsoft.CodeAnalysis.FxCopAnalyzers` [пакет NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

Начиная с Visual Studio 2019 16,8 и .NET 5,0, эти анализаторы [входят в состав пакета SDK для .NET](/dotnet/fundamentals/code-analysis/overview). Если вы не хотите переходить на пакет SDK для .NET 5 + или если предпочитаете использовать модель на основе пакетов NuGet, анализаторы также доступны в `Microsoft.CodeAnalysis.NetAnalyzers` [пакете NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Возможно, вы предпочтете модель на основе пакета для обновлений версий по требованию.

> [!NOTE]
> Сторонние анализаторы .NET не зависят от платформы. То есть проект не обязан ориентироваться на конкретную платформу .NET. Анализаторы работают для проектов, предназначенных для, а также для `net5.0` более ранних версий .NET, таких как `netcoreapp` , `netstandard` и `net472` .

## <a name="migration-steps"></a>Этапы миграции

Начиная с версии `3.3.2` , `Microsoft.CodeAnalysis.FxCopAnalyzers` пакет NuGet является устаревшим. Выполните следующие действия, чтобы перенести проект или решение из `Microsoft.CodeAnalysis.FxCopAnalyzers` в анализаторы .NET:

1. Удаление `Microsoft.CodeAnalysis.FxCopAnalyzers` пакета NuGet

2. [Включение или установка анализаторов .NET](install-net-analyzers.md). Обратите внимание, что не нужно изменять целевую платформу проекта.

3. Включить дополнительные правила: `Microsoft.CodeAnalysis.NetAnalyzers` гораздо более консервативн по сравнению с `Microsoft.CodeAnalysis.FxCopAnalyzers` . В отличие от пакета Фкскопанализерс, у него есть только несколько правил исправления, которые [по умолчанию включены как предупреждения сборки](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Можно [включить дополнительные правила](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) , настроив свойство MSBuild [аналисисмоде](/dotnet/core/project-sdk/msbuild-props#analysismode) . Например, если задать для свойства значение, `AllEnabledByDefault` по умолчанию будут включены все применимые правила центра сертификации в качестве предупреждений сборки.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>См. также раздел

- [Сравнение анализа исходного кода и устаревшей функции анализа](net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)
- [Миграция с анализа прежних версий на анализаторы .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Включение или установка анализаторов .NET](install-net-analyzers.md)
- [Вопросы и ответы о анализаторах .NET](net-analyzers-faq.yml)
- [Настройка анализаторов .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
