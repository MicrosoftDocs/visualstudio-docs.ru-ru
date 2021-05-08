---
title: Анализ кода FxCop (двоичный анализ) и анализаторы .NET (исходный анализ)
ms.date: 09/06/2018
description: Узнайте о различиях между старыми FxCop (двоичным анализом) и анализаторами .NET (исходный анализ) в Visual Studio. См. Ответы на вопросы о том, как использовать эти анализаторы.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800452"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Часто задаваемые вопросы о устаревших анализаторах FxCop и .NET

Понимание различий между старыми FxCop (двоичным анализом) и анализаторами .NET (исходный анализ) может быть непростой путаницой. В этой статье будут раскрыты некоторые вопросы, которые могут возникать у вас.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>В чем разница между старыми анализаторами FxCop и .NET?

Устаревшие функции FxCop выполняют анализ после построения скомпилированной сборки. В этом случае запускается отдельный исполняемый файл **FxCopCmd.exe**. Средство FxCopCmd.exe загружает скомпилированную сборку, выполняет анализ кода и затем подготавливает отчет о результатах (или *данные диагностики*).

Анализаторы .NET основаны на .NET Compiler Platform ("Roslyn"). [Их можно включить из пакета SDK для .NET или установить в виде пакета NuGet](install-net-analyzers.md) , на который ссылается проект или решение. Анализаторы запускают анализ на основе исходного кода во время выполнения компилятора. Анализаторы размещаются в процессе компилятора: **csc.exe** или **vbc.exe**, а также выполнять анализ при построении проекта. Результаты работы анализатора выводятся вместе с результатами выполнения компилятора.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>В чем разница между анализаторами FxCop и анализаторами .NET?

Как средства FxCop Analyzer, так и анализаторы .NET относятся к реализации анализатора .NET Compiler Platform ("Roslyn") для правил ЦС FxCop. До Visual Studio 2019 16,8 и .NET 5,0 эти анализаторы поставляются как `Microsoft.CodeAnalysis.FxCopAnalyzers` [пакет NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Начиная с Visual Studio 2019 16,8 и .NET 5,0, эти анализаторы [входят в состав пакета SDK для .NET](/dotnet/fundamentals/code-analysis/overview). Они также доступны в виде `Microsoft.CodeAnalysis.NetAnalyzers` [пакета NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Попробуйте [выполнить миграцию с FxCop Analyzer на анализаторы .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>Выполняет ли команда анализа выполнения кода Запуск анализаторов .NET?

До выпуска Visual Studio 2019 16,5 **при выборе анализа**  >  **запустить анализ кода** выполняется анализ прежних версий. При запуске Visual Studio 2019 16,5 с помощью команды меню **выполнить анализ кода** выполняются анализаторы на основе Roslyn для выбранного проекта или решения. Если установлены анализаторы .NET, они также будут выполнены. Дополнительные сведения см. [в разделе инструкции. Запуск анализа кода вручную для управляемого кода](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Запускаются ли анализаторы с помощью свойства проекта msbuild RunCodeAnalysis?

Нет. Свойство **RunCodeAnalysis** в файле проекта (например, *.csproj*) используется только для выполнения устаревших функций FxCop. В этом случае после построения запускается задача msbuild, которая вызывает файл **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Итак, как запустить анализаторы .NET?

Чтобы запустить анализаторы .NET, сначала [включите их из пакета SDK для .NET или установите их в качестве пакета NuGet](install-net-analyzers.md). После этого следует построить проект или решение из среды Visual Studio или с помощью msbuild. Предупреждения и ошибки, создаваемые анализаторами Roslyn, отображаются в **Список ошибок** или командном окне.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Я получаю предупреждение CA0507 даже после установки пакета NuGet для .NET Analyzer

Если вы установили анализаторы .NET, но продолжаете получать предупреждение CA0507 **"" Запуск анализа кода "не рекомендуется в пользу средств FxCop Analyzer, которые запускаются во время сборки"**, может потребоваться задать для свойства **рункодеаналисис** MSBuild в [файле проекта](../ide/solutions-and-projects-in-visual-studio.md#project-file) значение **false**. В противном случае прежний анализ будет выполняться после каждой сборки.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Какие правила были перенесены в анализаторы .NET?

Сведения о том, какие правила анализа прежних версий были перенесены в анализаторы .NET, см. в разделе [состояние порта правила FxCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Предупреждения анализа кода обрабатываются как ошибки

Если в проекте используется параметр Build для обработки предупреждений как ошибок, то предупреждения анализатора могут отображаться как ошибки. Чтобы предотвратить невозможность обработки предупреждений анализа кода как ошибок, следуйте инструкциям в [разделе вопросы и ответы по анализу кода](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>См. также раздел

- [Обзор анализаторов на платформе .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Миграция на анализаторы .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Установка анализаторов .NET](install-net-analyzers.md)
