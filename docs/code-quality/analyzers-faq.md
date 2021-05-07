---
title: EditorConfig и анализаторы
ms.date: 03/11/2019
description: Сведения об анализе кода на основе .NET Compiler Platform в Visual Studio. См. Ответы на вопросы о файлах EditorConfig, наборах правил и других разделах.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d67471027f36d0e22c055f4306ce2137d972463
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800453"
---
# <a name="code-analysis-faq"></a>Анализ кода: вопросы и ответы

На этой странице содержатся ответы на некоторые часто задаваемые вопросы об анализе кода на основе .NET Compiler Platform в Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Анализ кода и EditorConfig

**Вопрос**. следует ли использовать анализ кода или EditorConfig для проверки стиля кода?

Ответ **. анализ** кода и файлы EditorConfig работают с руки. При определении стилей кода [в файле EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) или на странице [параметров текстового редактора](../ide/code-styles-and-code-cleanup.md) вы фактически настраиваете анализаторы кода, встроенные в Visual Studio. Файлы EditorConfig можно использовать для включения или отключения правил анализатора, а также для настройки пакетов анализатора NuGet.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig и наборы правил

**Вопрос**. следует ли настроить мои анализаторы с помощью набора правил или файла EditorConfig?

Ответ **. наборы** правил и файлы EditorConfig могут сосуществовать, и их можно использовать для настройки анализаторов. Как файлы EditorConfig, так и наборы правил позволяют включать и отключать правила и задавать их серьезность.

Однако EditorConfig файлы предлагают дополнительные способы настройки правил.

- Для анализаторов качества кода .NET файлы EditorConfig позволяют [определить типы анализируемого кода](/dotnet/fundamentals/code-analysis/code-quality-rule-options).
- Для анализаторов в стиле кода .NET, встроенных в Visual Studio, файлы EditorConfig позволяют [определить предпочтительные стили кода](/dotnet/fundamentals/code-analysis/code-style-rule-options) для базы кода.

Помимо наборов правил и файлов EditorConfig, некоторые анализаторы настраиваются с помощью текстовых файлов, помеченных как [Дополнительные файлы](../ide/build-actions.md#build-action-values) для компиляторов C# и VB.

> [!NOTE]
> - Файлы EditorConfig можно использовать только для включения правил и настройки их серьезности в Visual Studio 2019 версии 16,3 и более поздних.
> - EditorConfig файлы нельзя использовать для настройки анализа прежних версий, тогда как наборы правил могут.

## <a name="code-analysis-in-ci-builds"></a>Анализ кода в сборках CI

**Вопрос**. работает ли анализ кода на основе .NET Compiler Platform в сборках непрерывной интеграции (CI)?

**Ответ**. Да. Для анализаторов, установленных из пакета NuGet, эти правила [применяются во время сборки, в](roslyn-analyzers-overview.md#build-errors)том числе во время сборки CI. Анализаторы, используемые в CI, строят конфигурацию правил из наборов правил и файлов EditorConfig. В настоящее время анализаторы кода, встроенные в Visual Studio, недоступны в качестве пакета NuGet, поэтому эти правила не могут быть применены в сборке CI.

## <a name="ide-analyzers-versus-stylecop"></a>Анализаторы IDE и StyleCop

**Вопрос**. в чем разница между анализаторами кода IDE Visual Studio и анализаторами StyleCop?

Ответ **. в** интегрированной среде разработки Visual Studio имеются встроенные анализаторы, которые ищут как проблемы, связанные с стилем кода, так и качеством. Эти правила помогают использовать новые возможности языка по мере их появлении и улучшают удобство обслуживания кода. Анализаторы IDE постоянно обновляются в каждом выпуске Visual Studio.

[Анализаторы StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) — это сторонние анализаторы, установленные в виде пакета NuGet, который проверяет согласованность стилей в коде. Как правило, правила StyleCop позволяют задавать персональные настройки для базы кода без необходимости использовать один стиль в другом.

## <a name="code-analyzers-versus-legacy-analysis"></a>Анализаторы кода и анализ прежних версий

**Вопрос**. в чем разница между устаревшим анализом и анализом кода на основе .NET Compiler Platform?

Ответ **. анализ кода на основе**.NET Compiler Platform анализирует исходный код в режиме реального времени и во время компиляции, в то время как устаревший анализ анализирует двоичные файлы после завершения сборки. Дополнительные сведения см. в разделе [анализ на основе .NET Compiler Platform и анализ прежних версий](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers).

## <a name="fxcop-analyzers-versus-net-analyzers"></a>Анализаторы FxCop и анализаторы .NET

**Вопрос**. в чем разница между анализаторами FxCop и анализаторами .NET?

Ответ. как анализаторы **FxCop, так** и анализаторы .NET относятся к реализации анализаторов FxCop .NET Compiler Platform ("Roslyn"). До Visual Studio 2019 16,8 и .NET 5,0 эти анализаторы поставляются как `Microsoft.CodeAnalysis.FxCopAnalyzers` [пакет NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Начиная с Visual Studio 2019 16,8 и .NET 5,0, эти анализаторы [входят в состав пакета SDK для .NET](/dotnet/fundamentals/code-analysis/overview). Они также доступны в виде `Microsoft.CodeAnalysis.NetAnalyzers` [пакета NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Попробуйте [выполнить миграцию с FxCop Analyzer на анализаторы .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="treat-warnings-as-errors"></a>Рассматривать предупреждения как ошибки

**Вопрос**. в моем проекте используется параметр сборки для обработки предупреждений как ошибок. После перехода с предыдущего анализа на анализ исходного кода все предупреждения анализа кода будут отображаться как ошибки. Как предотвратить это?

Ответ **. чтобы** предотвратить невозможность обработки предупреждений анализа кода как ошибок, выполните следующие действия.

  1. Создайте файл. props со следующим содержимым:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Добавьте строку в файл проекта. csproj или. vbproj, чтобы импортировать файл PROPS, созданный на предыдущем шаге. Эту строку необходимо поместить перед любыми строками, которые импортируют файлы Analyzer. props. Например, если файл. props имеет имя CODEANALYSIS. props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Страница свойств решения "анализ кода"

**Вопрос**. где находится страница свойств "анализ кода" для решения?

Ответ **. Страница свойств "анализ** кода" на уровне решения была удалена в пользу более надежной общей группы свойств. Для управления анализом кода на уровне проекта страница свойств анализ кода по-прежнему доступна. (Для управляемых проектов мы также рекомендуем переходить с набора правил на EditorConfig для конфигурации правила.)  Для совместного использования наборов правил в нескольких и всех проектах в решении или репозитории рекомендуется определить группу свойств с помощью свойства [кодеаналисисрулесет](../code-quality/using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) в общем файле PROPS/targets или *Directory. props/Directory. targets* . Если у вас нет таких общих свойств или целевых объектов, которые импортируются всеми проектами, рекомендуется добавить такую группу свойств в каталог [. props или файл Directory. targets](../msbuild/customize-your-build.md) в каталоге решения верхнего уровня, который автоматически импортируется во все файлы проекта, определенные в каталоге или его подкаталогах.

## <a name="see-also"></a>См. также раздел

- [Обзор анализаторов](roslyn-analyzers-overview.md)
- [Параметры соглашений о написании кода .NET в EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)