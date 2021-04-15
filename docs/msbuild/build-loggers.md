---
title: Средства ведения журнала сборки | Документация Майкрософт
description: Узнайте, как с помощью средств ведения журнала MSBuild настраивать выходные данные сборки и управлять ими, а также отображать сообщения, ошибки или предупреждения в ответ на определенные события сборки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b676fe015f5f513a069ffaf6ae4fac59c1a5fa68
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213905"
---
# <a name="build-loggers"></a>Средства ведения журнала сборки

Средства ведения журнала позволяют настраивать выходные данные сборки и отображать сообщения, ошибки или предупреждения в ответ на определенные события сборки. Каждое средство ведения журнала существует в виде класса .NET, который реализует интерфейс <xref:Microsoft.Build.Framework.ILogger>, определенный в сборке *Microsoft.Build.Framework.dll*.

Для средства ведения журнала можно использовать два подхода к реализации:

- Прямая реализация интерфейса <xref:Microsoft.Build.Framework.ILogger>.
- Произведите класс от вспомогательного класса <xref:Microsoft.Build.Utilities.Logger>, который определен в сборке *Microsoft.Build.Utilities.dll*. <xref:Microsoft.Build.Utilities.Logger> реализует <xref:Microsoft.Build.Framework.ILogger> и предоставляет реализацию по умолчанию некоторых элементов <xref:Microsoft.Build.Framework.ILogger>.

  В этой статье мы расскажем, как создать простое средство ведения журнала, унаследованное от <xref:Microsoft.Build.Utilities.Logger>, которое отображает в консоли сообщения в ответ на определенные события сборки.

## <a name="register-for-events"></a>Регистрация для событий

Средство ведения журнала предназначено для сбора сведений о выполнении сборки, которые поступает от обработчика сборки, и для представления этой информации в полезном формате. Все средства ведения журнала должны переопределять метод <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, в котором средство ведения журнала регистрируется для событий. В этом примере средство ведения журнала регистрируется для событий <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> и <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet2":::

## <a name="respond-to-events"></a>Реагирование на события

Теперь, когда средство ведения журнала зарегистрировано для определенных событий, оно будет обрабатывать эти события при их возникновении. Для событий <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> и <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> средство ведения журнала просто записывает короткую фразу и имя файла проекта, связанного с событием. Все сообщения из средства ведения журнала записываются в окно консоли.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet3":::

## <a name="respond-to-logger-verbosity-values"></a>Реагирование на значения детализации для средства ведения журнала

В некоторых случаях информацию о событии нужно записывать, только если параметр **-verbosity** для MSBuild.exe содержит определенное значение. В этом примере обработчик событий <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> записывает сообщение, только если свойство <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, которое задается параметром **-verbosity**, равно <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet4":::

## <a name="specify-a-logger"></a>Указание средства ведения журнала

Когда средство ведения журнала скомпилировано в сборку, нужно передать в MSBuild информацию о том, что это средство ведения журнала следует использовать во время сборки. Для этого используйте параметр **-logger** в *MSBuild.exe*. Дополнительные сведения о доступных параметрах *MSBuild.exe* см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md).

Следующая команда выполняет сборку проекта *MyProject.csproj* с использованием класса ведения журнала, который реализован в *SimpleLogger.dll*. Параметр **-nologo** позволяет скрыть баннер и сообщение об авторских правах, а параметр **-noconsolelogger** отключает используемое по умолчанию консольное средство ведения журнала MSBuild.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Следующая командная строка выполняет сборку проекта с тем же средством ведения журнала, но уже с уровнем `Verbosity` для `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example-1"></a>Пример 1

### <a name="description"></a>Описание

В следующем примере приведен полный код средства ведения журнала.

### <a name="code"></a>Код

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet1":::

## <a name="example-2"></a>Пример 2

### <a name="description"></a>Описание

В следующем примере показано, как реализовать средство ведения журнала, которое записывает журнал в файл, а не окно консоли.

### <a name="code"></a>Код

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs" id="Snippet1":::

## <a name="see-also"></a>См. также

- [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
