---
title: Средства тестирования
description: Узнайте, как средства тестирования Visual Studio могут помочь вам и вашей команде в разработке и поддержке высоких стандартов качества кода.
ms.custom: SEO-VS-2020
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 7efc8e5955f4d11004d8408cadf312e6cbcb43eb
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607409"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Первое знакомство со средствами тестирования в Visual Studio

Средства тестирования Visual Studio могут помочь вам и вашей команде в разработке и поддержке высоких стандартов качества кода.

> [!NOTE]
> Модульное тестирование доступно во всех выпусках Visual Studio. Другие средства тестирования, такие как Live Unit Testing и IntelliTest, доступны только в выпуске Visual Studio Enterprise. Дополнительные сведения о выпусках см. в статье [Сравнение интегрированных сред разработки Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Обозреватель тестов

Окно **Обозреватель тестов** помогает разработчикам создавать и запускать модульные тесты, а также управлять ими. Можно использовать платформу для выполнения модульных тестов Microsoft или одну из нескольких сторонних платформ, в том числе платформы с открытым исходным кодом.

::: moniker range="vs-2017"
![Обозреватель тестов Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Обозреватель тестов Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Приступая к работе с модульным тестированием](unit-test-your-code.md)
* [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md)
* [Вопросы и ответы по обозревателю тестов](test-explorer-faq.md)
* [Установка платформ модульного тестирования сторонних поставщиков](install-third-party-unit-test-frameworks.md)

Visual Studio является расширяемой системой и позволяет использовать сторонние адаптеры модульного тестирования, такие как NUnit и xUnit.net. Кроме того, функция клонов кода обеспечивает высокое качество программного обеспечения, помогая определить блоки семантически сходного кода, которые являются кандидатами для совместного исправления ошибок или рефакторинга.

![Интеграция тестов сторонних разработчиков](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

Функция [Live Unit Testing](../test/live-unit-testing.md) автоматически выполняет модульные тесты в фоновом режиме и графически отображает объем протестированного кода и результаты тестирования в редакторе кода Visual Studio.

> [!NOTE]
> Функция "Live Unit Testing" доступна только в выпуске Enterprise и поддерживается только для кода .NET.

## <a name="intellitest"></a>IntelliTest

IntelliTest автоматически создает модульные тесты и тестовые данные для управляемого кода. IntelliTest улучшает покрытие и значительно сокращает усилия, необходимые для создания и обслуживания модульных тестов для нового и существующего кода.

![IntelliTest в действии](media/devtest-intellitest.png)

> [!NOTE]
> Инструмент IntelliTest доступен только в выпуске Enterprise. Он поддерживается только для кода C#, предназначенного для .NET Framework. В настоящее время инструмент не поддерживается для .NET Core и .NET Standard.

* [Создание модульных тестов для кода с помощью IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest — один тест на любой случай](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Справочное руководство по IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Покрытие кода

[Объем протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) позволяет определить, какая часть кода проекта в действительности тестируется закодированными тестами, такими как модульные тесты. Для обеспечения эффективной защиты от ошибок тесты должны выполнять ("покрывать") большую часть кода.

> [!NOTE]
> Объем протестированного кода доступен только в выпуске Enterprise.

Анализ объема протестированного кода может применяться и к управляемому, и к неуправляемому (машинному) коду.

Покрытие кода возможно при выполнении методов тестов с помощью обозревателя тестов. В таблице результатов отображается процент кода, который был выполнен в каждой сборке, классе и методе. Кроме того, редактор исходного кода показывает, какой код был протестирован.

* [Использование параметра объема протестированного кода для определения объема протестированного кода](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Модульное тестирование, объем протестированного кода и анализ клонов кода с помощью Visual Studio (лаборатория)](https://azuredevopslabs.com/labs/devopsserver/liveunittesting)
* [Настройка анализа объема протестированного кода](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) помогает изолировать тестируемый код, заменяя другие части приложения заглушками или оболочками.

> [!NOTE]
> Функция "Microsoft Fakes" доступна только в выпуске Enterprise и поддерживается только для кода .NET.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Тестирование пользовательского интерфейса с помощью закодированного теста и Selenium

Закодированные тесты пользовательского интерфейса позволяют создать полностью автоматические тесты для проверки функциональности и поведения пользовательского интерфейса приложения. Они автоматизируют тестирование пользовательского интерфейса в разных технологиях, включая приложения универсальной платформы Windows на основе XAML, приложения браузера и приложения SharePoint.

> [!NOTE]
> Закодированный пользовательский интерфейс является устаревшей функцией.

Если вам нужны лучшие в своем роде закодированные тесты пользовательского интерфейса или универсальные тесты на основе браузера с использованием Selenium, Visual Studio предоставляет все необходимые для этого инструменты.

![Тестирование пользовательского интерфейса с помощью закодированных тестов](media/devtest-codeduitest.png)

* [Использование автоматизации пользовательского интерфейса для тестирования кода](use-ui-automation-to-test-your-code.md)
* [Руководство по созданию, изменению и обслуживанию закодированного теста пользовательского интерфейса](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Тестирование приложений UWP с помощью закодированных тестов пользовательского интерфейса](test-uwp-app-with-coded-ui-test.md)
* [Введение в использование закодированных тестов пользовательского интерфейса с помощью Visual Studio Enterprise (лаборатория)](https://azuredevopslabs.com/labs/tfs/codedui)

## <a name="related-scenarios"></a>Связанные сценарии

* [Произвольное и ручное тестирование (Azure Test Plans)](/azure/devops/test/index?view=vsts&preserve-view=true)
* [Нагрузочное тестирование (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)
* [Непрерывное тестирование (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)
* [Средства анализа кода](../code-quality/code-analysis-for-managed-code-overview.md)
