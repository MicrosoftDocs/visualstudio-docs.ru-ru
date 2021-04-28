---
title: 'Документация по Visual Studio. История изменений '
titleSuffix: ''
description: История новых возможностей в документации по Visual Studio
ms.date: 03/08/2021
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: d29c8be82ba0461231d9cd02eb6799dd38a690ed
ms.sourcegitcommit: 5fb684ff8729eb118aa91ce9f049c79eeb9747b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2021
ms.locfileid: "107913037"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>История новых возможностей в документации по Visual Studio

Добро пожаловать в историю изменений документации по Visual Studio. В этой статье приведены основные изменения в документации до марта 2021 г. (начиная с июля 2020 г.). Последние изменения см. в разделе [Документация по Visual Studio. Обновления в документации за июль 2020 г.](whats-new-visual-studio-docs.md)

## <a name="february-2021"></a>Февраль 2021 года

### <a name="debugger"></a>Отладчик

**Обновленные статьи**

- [Использование точек останова в отладчике Visual Studio](../debugger/using-breakpoints.md) — обновления для специальных возможностей

### <a name="get-started"></a>Начало работы

**Обновленные статьи**

- [Учебник. Открытие проекта из репозитория в Visual Studio 2017](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md) — обновление ссылок "См. также" в статье "Открытие проекта из репозитория" для VS2017
- [Учебник. Открытие проекта из репозитория](../get-started/tutorial-open-project-from-repo-visual-studio-2019.md) — добавление ссылки в версию страницы "Открытие проекта из репозитория" для VS2017

### <a name="ide"></a>IDE

**Обновленные статьи**

- [Устранение неполадок и создание журналов по проблемам MSBuild](./msbuild-logs.md) — добавление инструкций по использованию расширения средств системы проектов

### <a name="install"></a>Установка

**Обновленные статьи**

- [Обновление Visual Studio с использованием минимального автономного макета](../install/update-minimal-layout.md)
  - Добавление примера VS2017 в таблицу параметров
  - Добавление примеров для VS2017

### <a name="msbuild"></a>MSBuild

**Новые статьи**

- [MSB3644: ссылочные сборки для версии платформы "FrameworkVersion" не найдены](../msbuild/errors/msb3644.md) — ошибки MSBuild
- [MSB8036: версия "version" Windows SDK не найдена](../msbuild/errors/msb8036.md) — ошибки MSBuild

### <a name="test"></a>Тест

**Обновленные статьи**

- [Использование платформы модульного тестирования Майкрософт для C++ в Visual Studio](../test/how-to-use-microsoft-test-framework-for-cpp.md) — небольшие обновления и изменения содержимого
- [Написание модульных тестов для библиотек DLL C++ в Visual Studio](../test/how-to-write-unit-tests-for-cpp-dlls.md) — небольшие обновления и изменения содержимого
- [Выполнение модульных тестов с помощью Обозревателя тестов](../test/run-unit-tests-with-test-explorer.md) — обновления для специальных возможностей
- [Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) — обновления для специальных возможностей
- [Изоляция тестируемого кода с помощью Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) — явное упоминание .NET 5.0 в документации по Fakes

## <a name="january-2021"></a>Январь 2021 г.
### <a name="azure"></a>Azure

**Новые статьи**

- [Создание и развертывание в облачных службах (расширенная поддержка) в Visual Studio (предварительная версия)](../azure/cloud-services-extended-support.md) — расширенная поддержка облачных служб — без шаблона

### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [Метрики кода — взаимозависимость классов](../code-quality/code-metrics-class-coupling.md) — обновление метрик кода
- [Метрики кода — диапазон индексов удобства поддержки и их значения](../code-quality/code-metrics-maintainability-index-range-and-meaning.md) — обновление метрик кода

### <a name="debugger"></a>Отладчик

**Новые статьи**

- [Отладка приложений .NET Core в WSL 2 с помощью Visual Studio](../debugger/debug-dotnet-core-in-wsl-2.md) — отладка .NET Core в WSL2

**Обновленные статьи**

- [Создание настраиваемых представлений объектов C++ в отладчике с помощью платформы Natvis](../debugger/create-custom-views-of-native-objects.md) — пояснения к форматированию специальных символов в формате XML в NatVis
- [Предупреждение системы безопасности. Подключение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md) — обновленное предупреждение безопасности о присоединении к процессу, к которому нет доверия

### <a name="deployment"></a>Развертывание

**Обновленные статьи**

- [Элемент &lt;InstallChecks&gt; (начальный загрузчик)](../deployment/installchecks-element-bootstrapper.md) — обновленная документация по пакету начального загрузчика с учетом нового элемента BeforeInstallChecks

### <a name="extensibility"></a>Расширение среды

**Обновленные статьи**

- [Пошаговое руководство: Публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md) — фиксация [PUBLIC_MOVE] из общедоступного запроса на вытягивание 6214

### <a name="get-started"></a>Начало работы

**Новые статьи**

- [Учебник. Открытие проекта из репозитория в Visual Studio 2017](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md) — обновленное руководство "Открытие проекта из репозитория"

**Обновленные статьи**

- [Учебник. Открытие проекта из репозитория](../get-started/tutorial-open-project-from-repo.md) — обновленное руководство "Открытие проекта из репозитория"

### <a name="ide"></a>IDE

**Новые статьи**

- [Справка, вызываемая клавишей F1, по JavaScript для Visual Studio](./not-in-toc/default-f1-javascript.md) — добавлены страницы JS и TS по умолчанию, вызываемые клавишей F1
- [Справка, вызываемая клавишей F1, по TypeScript для Visual Studio](./not-in-toc/default-f1-typescript.md) — добавлены страницы JS и TS по умолчанию, вызываемые клавишей F1

**Обновленные статьи**

- [Решения и проекты в Visual Studio](./solutions-and-projects-in-visual-studio.md) — добавлена ссылка на библиотеку изображений Visual Studio

### <a name="install"></a>Установка

**Обновленные статьи**

- [Номера сборок и даты выпуска Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md) — обновления в день установки исправлений

### <a name="msbuild"></a>MSBuild

**Обновленные статьи**

- [Глоссарий MSBuild](../msbuild/msbuild-glossary.md) — повышение уровня ключей глоссария до H2

### <a name="profiling"></a>Профилирование

**Новые статьи**

- [Визуализация счетчиков dotnet из профилировщика Visual Studio](../profiling/dotnet-counters-tool.md) — добавлена документация по средству "Счетчики .NET"

### <a name="test"></a>Тест

**Обновленные статьи**

- [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md) — добавлена документация по звуковой подсказке для тестов

## <a name="december-2020"></a>Декабрь 2020 г.
### <a name="azure"></a>Azure

**Новые статьи**

- [Добавление конфигурации приложений Azure с помощью подключенных служб Visual Studio](../azure/vs-azure-tools-connected-services-app-configuration.md). Руководство по подключенным службам конфигурации приложений

### <a name="code-quality"></a>Качество кода

**Обновленные статьи**

- [Обзор](../code-quality/use-roslyn-analyzers.md). Создание из командной строки с помощью editorconfig
- [Включение или установка сторонних анализаторов .NET](../code-quality/install-net-analyzers.md)
  - Добавлены уточнения в документацию по миграции с анализаторов FxCop на анализаторы .NET
  - Изменено оглавление для анализаторов .NET
- [Миграция с анализаторов FxCop на анализаторы .NET](../code-quality/migrate-from-fxcop-analyzers-to-net-analyzers.md). Добавлены уточнения в документацию по миграции с анализаторов FxCop на анализаторы .NET

### <a name="containers"></a>Контейнеры

**Обновленные статьи**

- [Устранение неполадок при разработке в Visual Studio с использованием Docker](../containers/troubleshooting-docker-errors.md). Обновлено руководство по устранению неполадок с Docker для Visual Studio

### <a name="debugger"></a>Отладчик

**Обновленные статьи**

- [Часто задаваемые вопросы. Поиск нужной функции отладки в Visual Studio](../debugger/find-your-debugging-task.md). Действия по обнаружению для поиска задачи отладки и обзорных тем

### <a name="get-started"></a>Начало работы

**Обновленные статьи**

- [Учебник. Создание простого консольного приложения C# в Visual Studio](../get-started/csharp/tutorial-console.md). Руководство по консольным приложениям C#: Часть 2 относится только к VS 2019

### <a name="ide"></a>IDE

**Обновленные статьи**

- [Решения и проекты в Visual Studio](./solutions-and-projects-in-visual-studio.md). Обновлены темы, посвященные решениям и проектам
- [Создание проекта в Visual Studio](./create-new-project.md)
  - Внесены уточнения в замещающий текст для снимков экрана и диаграмм
  - Обновлены дополнительные темы, посвященные решениям и проектам
- [Ресурсы, посвященные устранению ошибок интегрированной среды разработки](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md). Пересмотрен устаревший раздел "Ресурсы форума"
- [Работа с решениями и проектами](./creating-solutions-and-projects.md). Обновлены дополнительные темы, посвященные решениям и проектам
- [Как сообщить о проблеме с Visual Studio или Visual Studio Installer](./how-to-report-a-problem-with-visual-studio.md)
  - Обновлен снимок экрана
  - Изменения в сообществе разработчиков
- [Советы и рекомендации по улучшению работы Visual Studio](./visual-studio-performance-tips-and-tricks.md). Обновлен раздел "Отключение средств диагностики"
- [Введение в проекты и решения](../get-started/tutorial-projects-solutions.md)
  - Обновлены темы, посвященные решениям и проектам
  - Обновлен файл tutorial-projects-solutions.md
  - Отсутствующий в меню параметр

### <a name="test"></a>Тест

**Обновленные статьи**

- [Приступая к работе с модульным тестированием](../test/getting-started-with-unit-testing.md). Действия по обнаружению и другие улучшения, связанные со средствами тестирования
- [Первое знакомство со средствами тестирования в Visual Studio](../test/improve-code-quality.md). Действия по обнаружению и другие улучшения, связанные со средствами тестирования
- [Средства тестирования Visual Studio; требуемый номер и заголовок страницы отображаются в результатах поиска. Включено название торговой марки. Менее 60 символов.](../test/index.yml) – Действия по обнаружению и другие улучшения, связанные со средствами тестирования
- [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md). Добавлен XML-формат динамического списка воспроизведения для различных платформ

## <a name="november-2020"></a>Ноябрь 2020 г.
### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [Включение или установка анализаторов .NET](../code-quality/install-net-analyzers.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET
- [Миграция с анализаторов FxCop на анализаторы .NET](../code-quality/migrate-from-fxcop-analyzers-to-net-analyzers.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET
- [Миграция с анализаторов прежних версий (FxCop) на анализаторы исходного кода (.NET)](../code-quality/migrate-from-legacy-analysis-to-net-analyzers.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET
- [Вопросы и ответы по анализаторам прежних версий FxCop и анализаторам .NET](../code-quality/net-analyzers-faq.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET

**Обновленные статьи**

- [Вопросы и ответы по анализу кода](../code-quality/analyzers-faq.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET
- [Состояние порта правила Fxcop](../code-quality/fxcop-rule-port-status.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET
- [Нерекомендуемые правила](../code-quality/fxcop-unported-deprecated-rules.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET
- [Неперенесенные правила, которые можно перенести](../code-quality/fxcop-unported-rules-may-get-ported.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET
- [Неперенесенные правила](../code-quality/fxcop-unported-rules.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET
- [Установка сторонних анализаторов](../code-quality/install-roslyn-analyzers.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET
- [Обзор](../code-quality/use-roslyn-analyzers.md). Добавлена документация по миграции с анализаторов FxCop на анализаторы .NET

### <a name="containers"></a>Контейнеры

**Обновленные статьи**

- [Как работает Bridge to Kubernetes](../containers/overview-bridge-to-kubernetes.md). Раздел разрешений Kubernetes

### <a name="debugger"></a>Отладчик

**Новые статьи**

- [Присоединение к процессу, выполняющемуся в контейнере Docker](../debugger/attach-to-process-running-in-docker-container.md). Рефакторинг документации по присоединению к процессу для сценариев Linux

**Обновленные статьи**

- [Присоединение к выполняемым процессам с использованием отладчика Visual Studio](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Рефакторинг документации по присоединению к процессу для сценариев Linux
- [Отладка .NET Core в Linux с помощью SSH путем присоединения к процессу](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). Рефакторинг документации по присоединению к процессу для сценариев Linux

### <a name="deployment"></a>Развертывание

**Новые статьи**

- [Развертывание классического приложения Windows .NET с помощью ClickOnce](../deployment/quickstart-deploy-using-clickonce-folder.md). Добавлено краткое руководство по ClickOnce для проектов Windows .NET

**Обновленные статьи**

- [Знакомство с возможностями развертывания в Visual Studio](../deployment/deploying-applications-services-and-components.md)
  - Внесены редакторские правки
  - Обновлены возможности обнаружения и ссылки для .NET 5
- [Обязательное развертывание в Visual Studio #; заголовок страницы отображается в результатах поиска. Включено название торговой марки. Менее 60 символов.](../deployment/index.yml) — Обновлены возможности обнаружения и ссылки для .NET 5
- [Сборка приложений ClickOnce из командной строки](../deployment/building-clickonce-applications-from-the-command-line.md). Добавлено краткое руководство по ClickOnce для проектов Windows .NET
- [Развертывание приложения в папке, IIS, Azure или другом расположении](../deployment/deploying-applications-services-and-components-resources.md). Добавлено краткое руководство по ClickOnce для проектов Windows .NET
- [Развертывание приложения в папку с помощью Visual Studio](../deployment/quickstart-deploy-to-local-folder.md). Добавлено краткое руководство по ClickOnce для проектов Windows .NET

### <a name="designers"></a>Конструкторы

**Обновленные статьи**

- [Учебник. Начало работы с конструктором Windows Forms](../designers/walkthrough-windows-forms-designer.md). Исправлена опечатка

### <a name="get-started"></a>Начало работы

**Обновленные статьи**

- [Сведения о проектах и решениях](../get-started/tutorial-projects-solutions.md). Обновлены замещающий текст и метаданные, а также добавлено примечание о шаблоне пустого решения
- [Учебник. Открытие проекта из репозитория](../get-started/tutorial-open-project-from-repo.md). Добавлены примечание, а также ссылка на дополнительные ресурсы для нового интерфейса Git

### <a name="ide"></a>IDE

**Новые статьи**

- [Работа с учетными записями GitHub в Visual Studio](./work-with-github-accounts.md). Добавлены сведения о работе со страницей GitHub и входе с использованием GitHub на другие страницы
- [Извлечение базового класса](./reference/extract-base-class.md). Добавлены функции повышения производительности dotnet
- [Встроенный метод](./reference/inline-method.md). Добавлены функции повышения производительности dotnet
- [Преобразование класса в абстрактный](./reference/make-class-abstract.md). Добавлены функции повышения производительности dotnet
- [Использование `new()`](./reference/use-new.md). Добавлены функции повышения производительности dotnet
- [Использование сопоставления шаблонов](./reference/use-pattern-matching.md). Добавлены функции повышения производительности dotnet

**Обновленные статьи**

- [Интерфейс GIT в Visual Studio](../version-control/git-with-visual-studio.md)
  - Обновлены замещающий текст и метаданные
  - Обновлен раздел "Содержимое нового интерфейса Git" для общедоступной версии 16.8
- [Новые возможности Visual Studio 2019](./whats-new-visual-studio-2019.md)
  - Обновлены замещающий текст и метаданные
  - Обновлена страница "Новые возможности Visual Studio 2019" для общедоступной версии 16.8
- [Подключение к проектам в Team Explorer](./connect-team-project.md). Обновлена страница Team Explorer с добавлением примечания и ссылки для нового интерфейса Git
- [Работа с несколькими учетными записями пользователя](./work-with-multiple-user-accounts.md). Добавлены сведения о входе с использованием GitHub на другие страницы
- [Соглашения о форматировании EditorConfig на C++](./cpp-editorconfig-properties.md)
  - В параметрах C++ в файле EDITORCONFIG используется префикс cpp_ вместо _cpp_ _
  - Удален недопустимый символ в примере файла EDITORCONFIG для C++
- [Преобразование `typeof` в `nameof`](./reference/convert-typeof-to-nameof.md). Добавлены функции повышения производительности dotnet

### <a name="install"></a>Установка

**Обновленные статьи**

- [Номера сборки и даты выпуска Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md)
  - Добавлены данные для версии 16.8.2
  - Добавлено: 16.8.1
  - Обновлены номера сборок для общедоступной версии 16.8 и т. д.
- [Образы Visual Studio в Azure](../install/using-visual-studio-vm.md). Изменена дата публикации и обновлены версии с дополнительными редакциями
- [Идентификаторы рабочих нагрузок и компонентов Visual Studio](../install/workload-and-component-ids.md). Обновлена документация по компонентам для версии 16.8
- [Каталог компонентов для Visual Studio Build Tools](../install/workload-component-id-vs-build-tools.md). Обновлена документация по компонентам для версии 16.8
- [Каталог компонентов для Visual Studio Community](../install/workload-component-id-vs-community.md). Обновлена документация по компонентам для версии 16.8
- [Каталог компонентов для Visual Studio Enterprise](../install/workload-component-id-vs-enterprise.md). Обновлена документация по компонентам для версии 16.8
- [Каталог компонентов для Visual Studio Team Explorer](../install/workload-component-id-vs-team-explorer.md). Обновлена документация по компонентам для версии 16.8
- [Каталог компонентов для агента тестирования Visual Studio](../install/workload-component-id-vs-test-agent.md). Обновлена документация по компонентам для версии 16.8
- [Каталог компонентов для контроллера тестирования Visual Studio](../install/workload-component-id-vs-test-controller.md). Обновлена документация по компонентам для версии 16.8
- [Установка и использование Visual Studio и служб Azure, расположенных за брандмауэром или прокси-сервером](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md). Добавлен отсутствующий домен

### <a name="msbuild"></a>MSBuild

**Новые статьи**

- [Волны изменений](../msbuild/change-waves.md). MSBuild: новый раздел "Волны изменений"

**Обновленные статьи**

- [Функции свойств](../msbuild/property-functions.md). Выпуск 16.8
- [Общие элементы проектов MSBuild](../msbuild/common-msbuild-project-items.md). Восстановлено содержимое для элемента InternalsVisibleTo

### <a name="profiling"></a>Профилирование

**Обновленные статьи**

- [Измерение производительности приложения из командной строки](../profiling/profile-apps-from-command-line.md). Обновлены сведения о профилировании в документации по командной строке

### <a name="test"></a>Тест

**Обновленные статьи**

- [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md). Добавлен небольшой раздел, посвященный XML-формату списка воспроизведения
- [Изоляция тестируемого кода с помощью Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md). Обновлена документация с добавлением сведений о поддержке .NET Core
- [Использование оболочек совместимости для изоляции приложения при модульном тестировании](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md). Обновлена документация с добавлением сведений о поддержке .NET Core

### <a name="xaml-tools"></a>Средства XAML

**Обновленные статьи**

- [Использование данных времени разработки в Конструкторе XAML в Visual Studio](../xaml-tools/xaml-designtime-data.md)
  - Обновлен раздел "Требования" для общедоступной версии 16.8
  - Изменен раздел "Требования"
  - Обновлены комментарии к предварительной версии 16.8 и добавлена ссылка на общедоступную версию

## <a name="october-2020"></a>Октябрь 2020 г.
### <a name="code-quality"></a>Качество кода

**Обновленные статьи**
- [Анализаторы кода](../code-quality/index.yml) — рефакторинг CA для .NET 5

### <a name="containers"></a>Контейнеры

**Обновленные статьи**

- [Краткое руководство. Использование Docker с одностраничным приложением React в Visual Studio](../containers/container-tools-react.md)
  - Средства контейнеров: удалены ссылки на старый репозиторий образов
  - Обновлено руководство по контейнерам React для .NET 3.1 и VS 16.7
- [Как работает Bridge to Kubernetes](../containers/overview-bridge-to-kubernetes.md) — Bridge to Kubernetes: добавлены ограничения
- [Отладка приложений в локальном контейнере Docker](../containers/edit-and-refresh.md) — панель элементов Docker

### <a name="debugger"></a>Отладчик

**Новые статьи**

- [Поддержка DirectX 12 в Visual Studio](../debugger/graphics/visual-studio-graphics-diagnostics-directx-12.md) — Vsdg dx12

**Обновленные статьи**

- [Отладка приложений ASP.NET или ASP.NET Core в Visual Studio](../debugger/how-to-enable-debugging-for-aspnet-applications.md) — исправления содержимого отладчика для проблем GitHub
- [Использование точек останова в отладчике Visual Studio](../debugger/using-breakpoints.md) — исправления содержимого отладчика для проблем GitHub
- [Отладка служб Azure в Visual Studio](../debugger/debug-azure-apps.md) — обновления SEO и ссылок для отладчика моментальных снимков
- [Отладке интерактивных приложений ASP.NET Azure с использованием Snapshot Debugger](../debugger/debug-live-azure-applications.md) — обновления SEO и ссылок для отладчика моментальных снимков
- [Удаленная отладка](../debugger/remote-debugging.md) — обновления SEO и ссылок для отладчика моментальных снимков
- [Обзор диагностики графики Visual Studio](../debugger/graphics/overview-of-visual-studio-graphics-diagnostics.md) — Vsdg dx12
- [Диагностика графики Visual Studio](../debugger/graphics/visual-studio-graphics-diagnostics.md) — Vsdg dx12

### <a name="get-started"></a>Начало работы

**Обновленные статьи**

- [Учебник. Расширение простого консольного приложения C# ](../get-started/csharp/tutorial-console-part-2.md) — дополнения отладки для расширенного учебника по C#

### <a name="ide"></a>IDE

**Новые статьи**

- [Использование поиска Visual Studio](./visual-studio-search.md) — документ по поиску VS

### <a name="install"></a>Установка

**Обновленные статьи**

- [Номера сборки и даты выпуска Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md)
  - Добавлены данные о 16.7.7 и 16.8 Preview 6
  - Добавлены сведения о 16.8 Preview 5

### <a name="msbuild"></a>MSBuild

**Обновленные статьи**

- [Пошаговое руководство: Использование MSBuild](../msbuild/walkthrough-using-msbuild.md) — пошаговое руководство по MSBuild: добавлены действия по автономной установке

### <a name="profiling"></a>Профилирование

**Обновленные статьи**

- [Анализ данных об использовании памяти](../profiling/analyze-memory-usage.md)
  - Обновления использования памяти для профилирования — ссылки и пояснения
  - Обновления средств использования памяти
- [Анализ использования памяти без использования отладки в Профилировщике производительности](../profiling/memory-usage-without-debugging2.md)
  - Обновления использования памяти для профилирования — ссылки и пояснения
  - Обновления средств использования памяти
- [Первое знакомство со средствами профилирования](../profiling/profiling-feature-tour.md)
  - Обновления использования памяти для профилирования — ссылки и пояснения
  - Обновления средств использования памяти
- [Запуск средств профилирования с отладчиком или без него](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
  - Обновления использования памяти для профилирования — ссылки и пояснения
  - Обновления средств использования памяти
- [Анализ загрузки ЦП без использования отладки в Профилировщике производительности](../profiling/cpu-usage.md) — обновления средств использования памяти

### <a name="windows"></a>Windows

**Обновленные статьи**

- [Документация по Visual Studio | Документация Майкрософт](../windows/index.yml) — обновления центра Windows

### <a name="xaml-tools"></a>Средства XAML

**Новые статьи**

- [Использование данных времени разработки в Конструкторе XAML в Visual Studio](../xaml-tools/xaml-designtime-data.md)
  - Добавлен раздел о расширяемости расширения в документы по времени разработки XAML
  - Новая статья о времени разработки XAML

## <a name="september-2020"></a>Сентябрь 2020 г.
### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1416. Проверка совместимости платформы](/dotnet/fundamentals/code-analysis/quality-rules/ca1416) — задокументировано исправление CA1416 "Проверка совместимости платформы"
- [CA1834. Использование StringBuilder.Append(char) для строк с одним символом](/dotnet/fundamentals/code-analysis/quality-rules/ca1834) — документация по CA1834

**Обновленные возможности**

- [Обзор анализа исходного кода](../code-quality/roslyn-analyzers-overview.md) — обновления анализа кода для рефакторинга .NET
- [Настройка анализа качества кода](../code-quality/use-roslyn-analyzers.md) — обновления анализа кода для рефакторинга .NET

### <a name="containers"></a>Контейнеры

**Новые статьи**

- [Локальный процесс с Kubernetes](../containers/bridge-to-kubernetes.md) — переименование функции "Локальный процесс с Kubernetes" в Bridge to Kubernetes
- [Как работает Bridge to Kubernetes](../containers/overview-bridge-to-kubernetes.md) — переименование функции "Локальный процесс с Kubernetes" в Bridge to Kubernetes

### <a name="deployment"></a>Развертывание

**Обновленные статьи**

- [Развертывание приложения в папке, IIS, Azure или другом расположении](../deployment/deploying-applications-services-and-components-resources.md) — обновления развертывания.
- [Развертывание приложения в папку с помощью Visual Studio](../deployment/quickstart-deploy-to-local-folder.md) — обновления, касающиеся развертывания

### <a name="ide"></a>IDE

**Новые статьи**

- [Новый интерфейс GIT в Visual Studio (предварительная версия)](../version-control/git-with-visual-studio.md) — добавлено содержимое о новом интерфейсе GIT (предварительная версия)
- [Соглашения о форматировании EditorConfig на C++](./cpp-editorconfig-properties.md) — новая статья
- [Что такое GitHub Codespaces? (предварительная версия)](./codespaces/codespaces-overview.md) — добавлено содержимое о Codespaces (предварительная версия)
- [Настройка codespace (предварительная версия)](./codespaces/customize-codespaces.md) — добавлено содержимое о Codespaces (предварительная версия)
- [Поддерживаемые функции Visual Studio (предварительная версия)](./codespaces/supported-features-codespaces.md) — добавлено содержимое о Codespaces (предварительная версия)
- [Использование Visual Studio с codespace (предварительная версия)](./codespaces/use-visual-studio-with-codespaces.md) — добавлено содержимое о Codespaces (предварительная версия)

**Обновленные статьи**

- [Параметры соглашений о написании кода .NET в EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) — обновление editorconfig
- [Языковые соглашения](/dotnet/fundamentals/code-analysis/style-rules/language-rules) — отсутствовали примеры

### <a name="install"></a>Установка

**Новые статьи**

- [Visual Studio на устройствах ARM](../install/visual-studio-on-arm-devices.md) — добавлен документ о Visual Studio на ARM

**Обновленные статьи**

- [Исправление ошибок сети при установке или использовании Visual Studio](../install/troubleshooting-network-related-errors-in-visual-studio.md) — добавлено описание решения проблемы с аварийным завершением работы прокси-сервера при авторизации

### <a name="profiling"></a>Профилирование

**Обновленные статьи**

- [Измерение использования памяти в Visual Studio](../profiling/memory-usage.md) — обновления в обзоре возможностей профилирования
- [PerfTips](../profiling/perftips.md) — обновления в обзоре возможностей профилирования
- [Первое знакомство со средствами профилирования](../profiling/profiling-feature-tour.md) — обновления в обзоре возможностей профилирования
- [Запуск средств профилирования с отладчиком или без него](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
  - Обновления в обзоре возможностей профилирования
  - Улучшения производительности

## <a name="august-2020"></a>Август 2020 г.
### <a name="azure"></a>Azure

**Новые статьи**

- [Добавление Azure Application Insights с использованием Подключенных служб Visual Studio](../azure/azure-app-insights-add-connected-service.md) — Подключенные службы для VS 2019 16.7
- [Добавление Кэша Azure для Redis с использованием Подключенных служб Visual Studio](../azure/azure-cache-for-redis-add-connected-service.md) — Подключенные службы для VS 2019 16.7
- [Добавление Azure Cosmos DB в приложение с использованием Подключенных служб Visual Studio](../azure/azure-cosmosdb-add-connected-service.md) — Подключенные службы для VS 2019 16.7
- [Добавление Azure SignalR с использованием Подключенных служб Visual Studio](../azure/azure-signalr-add-connected-service.md) — Подключенные службы для VS 2019 16.7
- [Добавление подключения к Базе данных SQL Azure](../azure/azure-sql-database-add-connected-service.md) — Подключенные службы для VS 2019 16.7

**Обновленные статьи**

- [Добавление хранилища Azure с использованием подключенных служб Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Подключенные службы для VS 2019 16.7.
  - Статья о подключенных службах службы хранилища Azure: обновление пользовательского интерфейса обновления и поддерживаемых типов проектов.

### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1310. Определите StringComparison для правильности](/dotnet/fundamentals/code-analysis/quality-rules/ca1310) — добавлена документация по CA1310 и обновлена документация по CA1307.
- [CA1837. Используйте Environment.ProcessId вместо Process.GetCurrentProcess().Id](/dotnet/fundamentals/code-analysis/quality-rules/ca1837) — документация по CA1837.
- [CA1838. Не используйте строковые параметры `StringBuilder` для P/Invoke](/dotnet/fundamentals/code-analysis/quality-rules/ca1838) — добавлена документация по CA1838.
- [CA2008. Не создавайте задачи без передачи TaskScheduler](/dotnet/fundamentals/code-analysis/quality-rules/ca2008) — добавлена документация по CA2008.
- [CA2249. Попробуйте использовать String.Contains вместо String.IndexOf](/dotnet/fundamentals/code-analysis/quality-rules/ca2249) — добавлена документация по СА2249.
- [CA2361. Убедитесь, что автоматически сформированный класс, который содержит DataSet.ReadXml(), не используется с ненадежными данными](/dotnet/fundamentals/code-analysis/quality-rules/ca2361) — добавлены правила для DataSet и DataTable.
- [CA2362. Ненадежные данные DataSet или DataTable в автоматически созданном сериализуемом типе могут быть уязвимыми для атак удаленного выполнения кода](/dotnet/fundamentals/code-analysis/quality-rules/ca2362) — добавлены правила для DataSet и DataTable.
- [IL3000. Не используйте путь к файлу сборки при публикации в виде одного файла](/dotnet/fundamentals/code-analysis/quality-rules/il3000) — добавлена документация по IL3000.
- [IL3001. Не используйте путь к файлу сборки при публикации в виде одного файла](/dotnet/fundamentals/code-analysis/quality-rules/il3001) — добавлена документация по IL3001.

**Обновленные возможности**

- [CA1002. Не предоставляйте универсальные списки](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1046. Не перегружайте оператор равенства для ссылочных типов](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1307. Определите StringComparison для ясности](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) — добавлена документация по CA1310 и обновлена документация по CA1307.
- [CA1700. Не включайте в имя значений перечисления слово reserved](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1707. Идентификаторы не должны содержать символы подчеркивания](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1822. Пометьте элементы как статические](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) — добавлен раздел о настройке для использования контактной зоны API.
- [CA2351. Убедитесь, что входные данные DataSet.ReadXml() являются доверенными](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) — добавлены правила для DataSet и DataTable.
- [Установите сторонние анализаторы](../code-quality/install-roslyn-analyzers.md) — изменены структура и заголовки в документации по анализу кода.

### <a name="containers"></a>Контейнеры

**Обновленные статьи**

- [Развертывание контейнера ASP.NET в реестр контейнеров из Visual Studio](../containers/hosting-web-apps-in-docker.md) — обновление инструментов для контейнера для пользовательского интерфейса публикации Visual Studio 16.7.
- [Начало работы со Средствами Visual Studio для Kubernetes](../containers/bridge-to-kubernetes.md) — руководство по Kubernetes: добавление шагов для удаления.

### <a name="deployment"></a>Развертывание

**Новые статьи**

- [Расширение проектов Visual Studio Installer и .NET Core 3.1](../deployment/installer-projects-net-core.md) — создание новой страницы справки о возможностях установщика проектов .NET Core 3.1.

**Обновленные статьи**

- [Развертывание приложения в папке, IIS, Azure или другом расположении](../deployment/deploying-applications-services-and-components-resources.md) — обновления развертывания.
- [Документация по развертыванию Visual Studio](../deployment/index.yml) — обновления развертывания.

### <a name="extensibility"></a>Расширение среды

**Обновленные статьи**
- [Подтипы проектов](../extensibility/internals/project-subtypes.md) — исправлены отступы для элементов списка.
- [Справочник по значениям цветов для Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) — AB#1759333: исправлены отсутствующие заголовки столбцов.

### <a name="get-started"></a>Начало работы

**Обновленные статьи**

- [Шаг 5. Развертывание приложения ASP.NET Core в Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) — обновления видеоруководства по новому пользовательскому интерфейсу Подключенных служб.

### <a name="ide"></a>IDE

**Новые статьи**

- [Изменение клавиши справки F1 в Visual Studio](./not-in-toc/change-f1-help-key.md) — рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Справка по клавише F1 для текстового редактора](./not-in-toc/default-f1-text-editor.md) —рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Преобразование `typeof` в `nameof`](./reference/convert-typeof-to-nameof.md) — рефакторинг страницы, посвященной преобразованию typeof в nameof.
- [Упрощение выражения LINQ](./reference/simplify-linq-expression.md) — рефакторинг страницы, посвященной упрощению выражения LINQ.

**Обновленные статьи**

- [Настройка макетов окон в Visual Studio](./customizing-window-layouts-in-visual-studio.md) — добавлены сведения о вертикальных вкладках документов с моникерами в статье о настройке макетов окон.
- [Как сообщить о проблеме с Visual Studio или Visual Studio Installer](./how-to-report-a-problem-with-visual-studio.md)
  - Добавлены дополнительные сведения о NMI.
  - Переработана страница со сведениями о том, как отправить сообщение о проблеме.
- [Справка F1](./not-in-toc/default.md) —рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"](./reference/autorecover-environment-options-dialog-box.md) — добавлены сведения о обновленных расположениях файлов автосохранения.
- ["Параметры", "Текстовый редактор", Basic (Visual Basic), "Дополнительно"](./reference/options-text-editor-basic-visual-basic.md) — добавлена базовая документация по встроенным указаниям имен параметров.
- ["Параметры", "Текстовый редактор", C#, "Дополнительно"](./reference/options-text-editor-csharp-advanced.md) — добавлена базовая документация по встроенным указаниям имен параметров.
- [Советы и рекомендации по улучшению работы Visual Studio](./visual-studio-performance-tips-and-tricks.md) — добавлены сведения об отключении режима карты и переноса по словам.
- [Новые возможности Visual Studio 2019](./whats-new-visual-studio-2019.md) — обновлены сведения о новых возможностях общедоступной версии Visual Studio 2019 16.7.

### <a name="rtvs"></a>RTVS

**Обновленные статьи**

- [Работа с SQL Server и R](../rtvs/integrating-sql-server-with-r.md) — в таблицы включены заголовки столбцов.

## <a name="july-2020"></a>Июль 2020 г.
### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1417. Не используйте в строковых параметрах `OutAttribute` для P/Invoke](/dotnet/fundamentals/code-analysis/quality-rules/ca1417). Добавлена документация по CA1417.
- [CA1805. Не делайте лишних инициализаций.](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) Добавлена документация по CA1805.
- [CA1836. Отдавайте предпочтение IsEmpty перед Count (при наличии)](/dotnet/fundamentals/code-analysis/quality-rules/ca1836). Добавлена документация по CA1836 (предпочтение IsEmpty вместо Count)
- [CA2016. Переадресуйте параметр CancellationToken методам, которые его принимают](/dotnet/fundamentals/code-analysis/quality-rules/ca2016). Документ CA2016 (переадресация параметра CancellationToken методам, которые его принимают).
- [CA2350. Убедитесь, что входные данные DataTable.ReadXml() являются доверенными](/dotnet/fundamentals/code-analysis/quality-rules/ca2350) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2351. Убедитесь, что входные данные DataSet.ReadXml() являются доверенными](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2352. Ненадежные данные DataSet или DataTable в сериализуемом типе могут быть уязвимыми для атак удаленного выполнения кода](/dotnet/fundamentals/code-analysis/quality-rules/ca2352) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2353. Ненадежные данные DataSet или DataTable в сериализуемом типе](/dotnet/fundamentals/code-analysis/quality-rules/ca2353) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2354. Ненадежные данные DataSet или DataTable в графе десериализованных объектов могут быть уязвимыми для атаки удаленного выполнения кода](/dotnet/fundamentals/code-analysis/quality-rules/ca2354) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2355. Ненадежные данные DataSet или DataTable в графе десериализованных объектов](/dotnet/fundamentals/code-analysis/quality-rules/ca2355) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2356. Ненадежные данные DataSet или DataTable в графе десериализованных веб-объектов](/dotnet/fundamentals/code-analysis/quality-rules/ca2356) (базовая документация по правилам десериализации DataSet и DataTable).

### <a name="containers"></a>Контейнеры

**Новые статьи**

- [Настройка функции "Локальный процесс с Kubernetes"](../containers/configure-bridge-to-kubernetes.md) (конфигурация YAML для локального процесса с Kubernetes).
- [Использование Локального процесса с Kubernetes (предварительная версия)](../containers/bridge-to-kubernetes.md) — перенос Dev Spaces.
- [Принцип работы функции "Локальный процесс с Kubernetes"](../containers/overview-bridge-to-kubernetes.md)
  - Локальный процесс для Kubernetes. Добавлен раздел по маршрутизации.
  - Перенос Dev Spaces.

### <a name="cross-platform"></a>Кроссплатформенные

**Обновленные статьи**

- [Журнал изменений (инструменты Visual Studio для Unity, Windows)](/gamedev/unity/change-log-visual-studio-tools-for-unity.md), версия журнала изменений VSTU увеличена до 4.7.1.0
- [Журнал изменений (инструменты Visual Studio для Unity, Mac)](/gamedev/unity/change-log-visual-studio-tools-for-unity-mac.md), версия журнала изменений VSTUM увеличена до 2.7.1.0

### <a name="get-started"></a>Начало работы

**Новые статьи**

- [Учебник. Расширение простого консольного приложения C#](../get-started/csharp/tutorial-console-part-2.md), выпущена первая версия руководства по расширению Sidewalk

### <a name="ide"></a>IDE

**Новые статьи**

- [Рекомендации сообщества разработчиков](./developer-community-guidelines.md), добавлены рекомендации по DevCom
- [Завершение IntelliSense для неимпортируемых типов и методов расширения](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Установка

**Новые статьи**

- [Обновление Visual Studio с использованием минимального автономного макета](../install/update-minimal-layout.md), задокументирована возможность минимального макета
- [Руководство по Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) — инструкции по использованию Enterprise.

### <a name="javascript"></a>JavaScript

**Новые статьи**

- [Компиляция кода TypeScript (Node.js)](../javascript/compile-typescript-code-npm.md) — компиляция и сборка для TypeScript.
- [Компиляция кода TypeScript (ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) — компиляция и сборка для TypeScript.

### <a name="msbuild"></a>MSBuild

**Новые статьи**

- [Общие метаданные элементв MSBuild](../msbuild/common-msbuild-item-metadata.md), добавлена таблица в MSBuild для необязательных метаданных с элементами Link и LinkBase
- [Фильтры решений в MSBuild](../msbuild/solution-filters.md) — фильтры решений MSBuild.

### <a name="test"></a>Тест

**Новые статьи**

- [Отладка и анализ модульных тестов с помощью Обозревателя тестов](../test/debug-unit-tests-with-test-explorer.md) — работа по улучшению производительности в обозревателе тестов.

**Обновленные статьи**

- [Настройка модульных тестов с помощью файла *.runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Внесены сведения о настройке модульных тестов с помощью файла .runsettings
  - Изменено описание параметра blame, добавлен пример.