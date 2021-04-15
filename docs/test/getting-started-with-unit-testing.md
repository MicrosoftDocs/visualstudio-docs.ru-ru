---
title: Приступая к работе с модульным тестированием
description: Используйте Visual Studio, чтобы определить и запустить модульные тесты для обеспечения работоспособности кода и для обнаружения ошибок и сбоев, прежде чем с ними столкнутся клиенты.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e1576f8865fc5945514ce6965cdba66a1cfda55
ms.sourcegitcommit: 3985d0ae8d6332f4682c82a10897763173d52961
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107386054"
---
# <a name="get-started-with-unit-testing"></a>Приступая к работе с модульным тестированием

Используйте Visual Studio, чтобы определить и запустить модульные тесты для обеспечения работоспособности кода, нужного объема протестированного кода, а также для обнаружения ошибок и сбоев, прежде чем с ними столкнутся клиенты. Выполняйте модульные тесты регулярно, чтобы обеспечить правильную работу вашего кода.

В этой статье используются код и иллюстрации для C#, однако основные понятия и функции применимы также к языкам .NET, C++ , Python, JavaScript и TypeScript.

## <a name="create-unit-tests"></a>Создание модульных тестов.

В этом разделе описывается создание проекта модульного теста.

1. Откройте проект, который хотите протестировать в Visual Studio.

   Для наглядности в статье проводится модульный тест простого C#-проекта "Hello World" с именем **HelloWorldCore**. Пример кода для такого проекта выглядит следующим образом:

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. Выберите узел решения в **обозревателе решений**. Затем в верхней строке меню выберите **Файл** > **Добавить** > **Новый проект**.

1. В диалоговом окне создания проекта найдите шаблон проекта модульных тестов, который требуется использовать, например MSTest, и выберите его.

   Начиная с Visual Studio 2017 версии 14.8, языки .NET включают встроенные шаблоны для NUnit и xUnit. Для C++ потребуется выбрать платформу тестирования, поддерживаемую языком. Сведения о настройке тестового проекта на Python см. в статье [Настройка модульного тестирования для кода Python](../python/unit-testing-python-in-visual-studio.md).

   > [!TIP]
   > Если вы используете C#, проекты модульного тестирования можно создать на основе кода с помощью более быстрого метода. Дополнительные сведения см. в разделе [Создание проектов модульных тестов и методов теста](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods). Чтобы использовать этот метод для .NET Core или .NET Standard, требуется Visual Studio 2019.

   На следующем рисунке показано модульный тест MSTest, поддерживаемый в .NET.

   ::: moniker range=">=vs-2019"

   ![Шаблон проекта модульных тестов в Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Нажмите **Далее**, выберите имя для тестового проекта и нажмите **Создать**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Шаблон проекта модульных тестов в Visual Studio 2019](media/mstest-test-project-template.png)

   Выберите имя для тестового проекта, например HelloWorldTests, и нажмите **OK**.

   ::: moniker-end

   Проект добавляется в решение.

   ![Проект модульного теста в обозревателе решений](media/vs-2019/solution-explorer.png)

1. В проекте модульных тестов добавьте ссылку на проект, который необходимо протестировать, щелкнув правой кнопкой мыши **Ссылки** или **Зависимости**, и выберите **Добавить ссылку**.

1. Выберите проект, содержащий код, который будет тестироваться, и нажмите **OK**.

   ![Добавление ссылок на проект в Visual Studio](media/vs-2019/reference-manager.png)

1. Добавьте код в метод модульных тестов.

   Например, вы можете использовать следующий код, выбрав правильную вкладку документации, которая соответствует вашей платформе тестирования: MSTest, NUnit или xUnit (поддерживается только в .NET).

   ### <a name="mstest"></a>[MSTest](#tab/mstest)

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   ### <a name="nunit"></a>[NUnit](#tab/nunit)

   ```csharp
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

    ### <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

    ---

## <a name="run-unit-tests"></a>Запуск модульных тестов

1. Откройте [обозреватель тестов](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Откройте обозреватель тестов, выбрав **Тест** > **Обозреватель тестов** в верхней строке меню (или нажмите клавиши **CTRL** + **E**, **T**).
   ::: moniker-end
   ::: moniker range="vs-2017"
   Откройте Обозреватель тестов, выбрав **Тест** > **Windows** > **Обозреватель тестов** в верхней строке меню.
   ::: moniker-end

1. Запустите модульные тесты, нажав **Запустить все** (или нажмите клавиши **CTRL** + **R**, **V**).

   ![Выполнение модульных тестов в обозревателе тестов](media/vs-2019/test-explorer-run-all.png)

   После завершения зеленый флажок указывает, что тест пройден. Красный значок "x" указывает на сбой теста.

   ![Просмотр результатов тестов в обозревателе тестов](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Используйте [обозреватель тестов](../test/run-unit-tests-with-test-explorer.md) для запуска модульных тестов из встроенной платформы тестирования (MSTest) или сторонней платформы тестирования. Вы можете группировать тесты по категориям, фильтровать список тестов, а также создавать, сохранять и запускать списки воспроизведения тестов. Кроме того, с его помощью можно выполнять отладку тестов и анализировать производительность тестов и покрытие кода.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Просмотр результатов динамического модульного тестирования (Visual Studio Enterprise)

Если вы используете платформу тестирования MSTest, xUnit или NUnit в Visual Studio 2017 или более поздней версии, можно просмотреть динамические результаты модульных тестов.

> [!NOTE]
> Чтобы выполнить эти действия, необходим выпуск Visual Studio Enterprise.

1. Включите Live Unit Testing в меню **Тест**, выбрав **Тест** > **Live Unit Testing** > **Запустить**.

   ::: moniker range="vs-2017"

   ![Включение Live Unit Testing](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Запуск Live Unit Testing в Visual Studio 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Вы можете просматривать результаты тестов в окне редактора кода по мере написания и редактирования кода.

   ![Просмотр результатов тестов](media/vs-2019/live-unit-testing-results.png)

1. Щелкните индикатор результатов теста для просмотра дополнительных сведений, таких как имена тестов для этого метода.

   ![Выберите индикаторы результатов тестов](media/vs-2019/live-unit-testing-details.png)

Дополнительные сведения о Live Unit Testing см. в разделе [Live Unit Testing](../test/live-unit-testing-intro.md).

## <a name="use-a-third-party-test-framework"></a>Использование сторонней платформы тестирования

Модульные тесты можно выполнять в Visual Studio с помощью сторонних платформ тестирования, таких как Boost, Google и NUnit, в зависимости от языка программирования. Чтобы использовать стороннюю платформу тестирования, выполните следующие действия.

- Используйте **диспетчер пакетов NuGet**, чтобы установить пакет NuGet для выбранной платформы.

- (.NET) Начиная с Visual Studio 2017 версии 14.6, Visual Studio включает в себя предварительно настроенные шаблоны тестовых проектов для платформ тестирования NUnit и xUnit. Шаблоны также содержат необходимые пакеты NuGet, чтобы обеспечить поддержку.

- (C++) В Visual Studio 2017 и более поздних версиях некоторые платформы, такие как Boost, уже включены. Дополнительные сведения см. в статье [Написание модульных тестов для C/C++ в Visual Studio](../test/writing-unit-tests-for-c-cpp.md).

Добавление проекта модульного тестирования:

1. Откройте решение, содержащее код, который нужно протестировать.

2. В **обозревателе решений** щелкните решение правой кнопкой мыши и выберите **Добавить** > **Создать проект**.

3. Выберите шаблон проекта модульного теста.

   Для того примера — [NUnit](https://nunit.org/)

   ::: moniker range=">=vs-2019"

   ![Шаблон проекта тестирования NUnit в Visual Studio 2019](media/vs-2019/nunit-test-project-template.png)

   Щелкните **Далее**, назовите проект и нажмите кнопку **Создать**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Задайте проекту имя и нажмите **ОК**, чтобы создать его.

   ::: moniker-end

   Шаблон проекта содержит ссылки на пакеты NuGet для NUnit и NUnit3TestAdapter.

   ![Зависимости NUnit NuGet в обозревателе решений](media/vs-2019/nunit-nuget-dependencies.png)

4. Добавьте ссылку из проекта тестирования на проект, содержащий код, который вы хотите протестировать.

   В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Добавить** > **Ссылка**. (Ссылку также можно добавить из контекстного меню узла **Ссылки** или **Зависимости**.)

5. Добавьте код в метод теста.

   ![Добавление кода в файл кода модульного теста](media/vs-2019/unit-test-method.png)

6. Запустите тест в **обозревателе тестов** или щелкните правой кнопкой мыши в коде теста и выберите **Запустить тесты** (или нажмите клавиши **CTRL** + **R**, **T**).

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Основные сведения о модульных тестах](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Создание и запуск модульных тестов для управляемого кода](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
