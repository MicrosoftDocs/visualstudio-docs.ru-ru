---
title: Миграция с FxCop на исходный анализ (анализаторы .NET)
ms.custom: SEO-VS-2020
description: Узнайте, как анализировать код в первый раз или как выполнить миграцию из двоичного анализа (FxCop) к новому способу анализа управляемого кода с помощью анализа источника (анализаторы .NET).
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
ms.openlocfilehash: 9a673e7467816e71b8240de9e5f68840c9188dcd
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798236"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Переход от традиционного анализа (FxCop) к исходному анализу (анализаторы .NET)

Анализ исходного кода с помощью анализаторов .NET Compiler Platform ("Roslyn") заменяет [устаревший анализ](../code-quality/code-analysis-for-managed-code-overview.md) управляемому коду. Для новых шаблонов проектов, таких как проекты .NET Core и .NET Standard, устаревший анализ недоступен.

Многие правила традиционного анализа (FxCop) уже были переписаны для анализаторов .NET, набора Roslyn Code Analyzer. Анализаторы Roslyn выполняют анализ на основе исходного кода во время выполнения компилятора. Результаты работы анализатора выводятся вместе с результатами выполнения компилятора.

Дополнительные сведения о различиях между анализом прежних версий и анализом исходного кода см. в следующих статьях:

- [Сравнение анализа исходного кода и устаревшей функции анализа](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [Вопросы и ответы о анализаторах .NET](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>Миграция

Чтобы выполнить миграцию в исходный анализ, [включите или установите анализаторы .NET](install-net-analyzers.md). Как и в случае нарушений правил устаревшей функции анализа, нарушения анализа исходного кода отображаются в Visual Studio в окне списка ошибок. Кроме того, нарушения анализа исходного кода выделяются в редакторе кода с помощью *волнистых линий* под соответствующим кодом. Цвет волнистой линии зависит [параметра серьезности](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) правила. Сведения о состоянии правил, переданных на новые анализаторы .NET, см. в разделе [переносные и неперенесенные правила](../code-quality/fxcop-rule-port-status.md).

> [!NOTE]
> До Visual Studio 2019 16,8 и .NET 5,0 эти анализаторы поставляются как `Microsoft.CodeAnalysis.FxCopAnalyzers` [пакет NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Начиная с Visual Studio 2019 16,8 и .NET 5,0, эти анализаторы [входят в состав пакета SDK для .NET](/dotnet/fundamentals/code-analysis/overview). Они также доступны в виде `Microsoft.CodeAnalysis.NetAnalyzers` [пакета NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Дополнительные сведения см. [в статье миграция из FxCop Analyzer в анализаторы .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="configuration"></a>Конфигурация

Дополнительные сведения о настройке анализаторов .NET:

- Сведения о настройке анализаторов .NET см. в разделе [Настройка .NET Analyzer](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Чтобы узнать о настройке анализаторов с помощью стандартных правил с EditorConfig или файла набора правил, см. раздел [Включение категории правил](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

## <a name="see-also"></a>См. также раздел

- [Миграция с анализаторов FxCop на анализаторы .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
