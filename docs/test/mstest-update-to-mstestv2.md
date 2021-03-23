---
title: Обновление до MSTestV2
description: Узнайте, как выполнить обновление с MSTestV1 до MSTestV2
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffe45c444321a7efbaee0a2eb5729850a06c5910
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2021
ms.locfileid: "103366273"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>Обновление с MSTestV1 до MSTestV2

Вы можете обновить тестовый проект, изменив версию MSTest, указанную в файле *CSPROJ*, с MSTestV1 на MSTestV2. Не все функции в MSTestV1 были перенесены в MSTestV2, поэтому для устранения ошибок могут потребоваться некоторые изменения. Чтобы понять, какие функции больше не будут работать, см. раздел [Функции MSTestV1, которые не поддерживаются в MSTestV2](#mstestv1-features-that-are-not-supported-in-mstestv2). Возможно, потребуется удалить некоторые из этих функций из своих тестов.

1. Удалите ссылку на сборку Microsoft.VisualStudio.QualityTools.UnitTestFramework из проекта модульного теста.
2. Добавьте ссылки на пакеты NuGet в MSTestV2, включая пакеты [MSTest.TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) и [MSTest.TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) на nuget.org. Для установки пакетов в консоли диспетчера пакетов NuGet выполните следующие команды:

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>Пример старого стиля CSPROJ

Пример файла *CSPROJ* для MSTestV1:

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

Пример файла *CSPROJ*, который теперь нацелен на MSTestV2:

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> Тестовые проекты для закодированных тестов пользовательского интерфейса или нагрузочных веб-тестов не совместимы с MSTestV2. Эти типы проектов являются устаревшими. Дополнительные сведения см. в разделах [Прекращение использования закодированных тестов пользовательского интерфейса](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) и [Прекращение использования нагрузочных веб-тестов](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

### <a name="sdk-style-csproj-net-core-and-net-5"></a>Файл CSPROJ в стиле SDK (.NET Core и .NET 5)

Если ваш файл *CSPROJ* представляет собой более новую версию файлов *CSPROJ* в стиле SDK, то вы скорее всего уже используете MSTestV2. Пакеты NuGet для [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) и [Адаптера MSTestV2](https://www.nuget.org/packages/MSTest.TestAdapter/) можно найти в NuGet.

Пример

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>Зачем выполнять обновление до MSTestV2?

В 2016 году мы реализовали следующий шаг в развитии платформы MSTest, выпустив MSTestV2. Дополнительные сведения об этом изменении можно найти в [записи блога](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/) с объявлением.

* Платформу MSTestV2 проще получить и обновить, так как она предоставляется в виде [пакета NuGet](https://www.nuget.org/packages/MSTest.TestFramework/).
* MSTestV2 имеет [открытый код](https://github.com/microsoft/testfx).
* Единообразная поддержка платформы приложений. MSTestV2 — это объединенная реализация, которая обеспечивает единообразную поддержку платформы приложений в .NET Framework, .NET Core, ASP.NET Core и UWP. [Дополнительные сведения](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* Реализация является полностью кроссплатформенной (Windows, Linux, Mac). [Дополнительные сведения](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2 поддерживает целевые платформы .NET Framework 4.5.0 и более поздней версии, .NET Core 1.0 и более поздних версий (Universal Windows Apps 10 и более поздних версий), ASP.NET Core 1.0 и более поздних версий и .NET 5 и более поздних версий.
* Она предоставляет универсальный механизм расширяемости для одного пользователя. [Дополнительные сведения](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* Она предоставляет единообразную поддержку `DataRow` всех тестовых проектов на основе MSTest. [Дополнительные сведения](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Она позволяет размещать атрибут `TestCategory` на уровне класса или сборки. [Дополнительные сведения](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Методы тестов из базовых классов, определенных в другой сборке, теперь обнаруживаются и выполняются из производного тестового класса. Это изменение обеспечивает согласованное поведение для типов производных тестовых классов. Если такое поведение не требуется для обеспечения совместимости, его можно отключить, указав следующие параметры запуска:

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* Она обеспечивает более детальный контроль над параллельным выполнением за счет [параллельного выполнения тестов в сборке](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md). Это позволяет выполнять тесты внутри сборки в параллельном режиме.
* Метод `TestCleanup` класса `TestClass` вызывается, даже если соответствующий метод `TestInitialize` завершился сбоем. [Сведения о проблеме](https://github.com/Microsoft/testfx/issues/250).
* Время, затраченное на выполнение методов `AssemblyInitialize` и `ClassInitialize`, не учитывается в длительности теста. Это изменение ограничивает влияние этих методов на время ожидания теста.
* Тесты, которые не удается запустить, можно помечать как ошибочные, с помощью тега `MapNotRunnableToFailed`, который является частью узла адаптера в файле `.runsettings`.

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>Функции MSTestV1, которые не поддерживаются в MSTestV2

*   Тесты не могут быть включены в состав упорядоченного теста.
*   Адаптер не поддерживает настройку с помощью файла *TESTSETTINGS*. Используйте новый файл [*RUNSETTINGS*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) для настройки тестового запуска.
*   Адаптер не поддерживает списки тестов, указанные в виде файла *VSMDI*.
*   Типы "Проект закодированных тестов пользовательского интерфейса" и "Проект веб-тестов производительности и нагрузочных тестов" не поддерживаются. Дополнительные сведения см. в разделах [Прекращение использования закодированных тестов пользовательского интерфейса](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) и [Прекращение использования нагрузочных веб-тестов](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

## <a name="see-also"></a>См. также раздел

- [Настройка тестовых запусков с помощью `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Модульное тестирование кода](../test/unit-test-your-code.md)
- [Отладка модульных тестов с помощью Обозревателя тестов](../test/debug-unit-tests-with-test-explorer.md)
