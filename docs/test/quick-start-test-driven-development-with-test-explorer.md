---
title: Пошаговое руководство по разработке на основе тестирования
description: Узнайте, как разработать проверенный метод в среде C# с помощью Microsoft Test Framework, который можно легко адаптировать для других языков или платформ тестирования, например NUnit.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 294c99081668baa2ed19df00989ceac768979481
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683953"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Пошаговое руководство. Разработка на основе тестирования с помощью обозревателя тестов

Создавайте модульные тесты, чтобы обеспечить правильную работу кода с помощью добавочных изменений кода. Существует несколько платформ, которые можно использовать для написания модульных тестов, в том числе разработанные третьими сторонами. Некоторые тестовые среды специализируются на тестировании на различных языках или платформах. Обозреватель тестов предоставляет единый интерфейс модульных тестов для любых таких платформ. Дополнительные сведения об использовании **обозревателя тестов** см. в разделе [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md) и [Вопросы и ответы по обозревателю тестов](test-explorer-faq.md).

В данном пошаговом руководстве показано, как разработать тестируемый метод в C# с помощью платформы тестирования Microsoft (MSTest). Можно легко адаптировать его для других языков или других тестовых платформ, например NUnit. Дополнительные сведения см. в разделе [Установка платформ модульного тестирования сторонних поставщиков](install-third-party-unit-test-frameworks.md).

## <a name="create-a-test-and-generate-code"></a>Создание теста и создание кода

1. Создайте проекта C# **Библиотека классов (.NET Standard)**. Данный проект будет содержать код, который мы хотим протестировать. Назовите проект **MyMath**.

2. В том же решении добавьте новый тестовый проект MSTest.

   Начиная с Visual Studio 2019 версии 16.9, название шаблона проекта MSTest изменено с **Проект тестов MSTest (.NET Core)** на **Проект модульного теста**.

   Назовите тестовый проект **MathTests**.

   ![Новые проекты кода и тестов](../test/media/test-driven-development-ide.png)

3. Напишите простой метод теста, который проверяет результат, полученный для конкретных входных данных. Добавьте в класс `UnitTest1` приведенный ниже код.

   ```csharp
   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. Создайте тип на основе кода теста.

   1. Установите курсор на `Rooter`, а затем в меню лампочки выберите **Создать тип "Rooter"**  > **Создать новый тип**.

      ![Быстрое действие "Создать новый тип"](media/test-driven-development-generate-new-type.png)

   2. В диалоговом окне **Создать тип** установите для параметра **Проект** значение **MyMath**, проект библиотеки классов, и нажмите **OK**.

      ![Диалоговое окно "Создать тип" в Visual Studio 2019](media/test-driven-development-generate-type-dialog.png)

5. Создайте метод из кода теста. Установите курсор на `SquareRoot`, а затем в меню лампочки выберите **Создать метод Rooter.SquareRoot**.

6. Выполните модульный тест.

   1. Чтобы открыть **Обозреватель тестов**, в меню **Тест** выберите **Windows** > **Обозреватель тестов**.

   2. В **обозревателе тестов** выберите **Запустить все**, чтобы запустить тест.

   Выполняется сборка решения, тест запускается и завершается ошибкой.

7. Выберите имя теста.

   Дополнительные сведения о тесте появятся на панели **Сводка теста**.

   ![Сводка теста в обозревателе тестов](media/test-driven-development-test-detail-summary.png)

8. Перейдите по верхней ссылке в разделе **Трассировка стека**, чтобы перейти к расположению, в котором произошел сбой теста.

На данном этапе создан тест и заглушка, которые будут изменены таким образом, что тест будет успешно пройден.

## <a name="verify-a-code-change"></a>Проверка изменения кода

1. В файле *Class1.cs* улучшите код `SquareRoot`:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. В **обозревателе тестов** выберите **Запустить все**.

   Выполняется сборка решения, тест запускается и завершается успешно.

   ![Обозреватель тестов с пройденным тестом](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Расширение диапазона входных данных

Для уверенности, что код работает во всех случаях, добавьте тесты, которые используют более широкий диапазон входных значений.

> [!TIP]
> Избегайте изменения существующих успешно выполненных тестов. Вместо этого добавьте новые тесты. Изменяйте существующие тесты только в тех случаях, когда меняются пользовательские требования. Такой подход позволяет не потерять существующие функциональные возможности при работе с расширенным кодом.

1. В тестовом классе добавьте следующий тест, который использует диапазон входных значений:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. В **обозревателе тестов** выберите **Запустить все**.

   Новый тест завершается неудачей (несмотря на то, что первый тест по-прежнему завершается успешно). Чтобы найти точку сбоя, выберите тест, который не пройден, и просмотрите сведения на панели **Сводка теста**.

3. Проверьте тестируемый метод, чтобы узнать, что не так. Измените код `SquareRoot`, как показано:

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4. В **обозревателе тестов** выберите **Запустить все**.

   Теперь оба теста завершаются успешно.

## <a name="add-tests-for-exceptional-cases"></a>Добавление тестов для исключительных случаев

1. Добавьте новый тест для отрицательных входных значений:

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. В **обозревателе тестов** выберите **Запустить все**.

   Тестируемый метод зацикливается, его необходимо отменить вручную.

3. На панели инструментов **обозревателя тестов** нажмите **Отмена**.

   Выполнение теста останавливается.

4. Исправьте код `SquareRoot`, добавив следующую инструкцию `if` в начало метода:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. В **обозревателе тестов** выберите **Запустить все**.

   Все тесты завершаются успешно.

## <a name="refactor-the-code-under-test"></a>Рефакторинг тестируемого кода

Выполните рефакторинг кода, но не изменяйте тесты.

> [!TIP]
> *Рефакторинг* — это изменение, которое делает код более производительным или более понятным. Это действие не предназначено для изменения поведения кода, поэтому тесты не изменяются.
>
> Рекомендуется выполнять рефакторинг отдельно от расширения функциональности. Неизменяемость тестов уменьшает шансы случайных ошибок во время рефакторинга.

1. Измените строку, которая вычисляет `result` в методе `SquareRoot`, следующим образом:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }

        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
            previousResult = result;
            result = (result + input / result) / 2;
            //was: result = result - (result * result - input) / (2*result);
        }
        return result;
    }
    ```

2. Выберите **Выполнить все** и убедитесь, что все тесты по-прежнему завершаются успехом.

   ![Обозреватель тестов с тремя пройденными тестами](../test/media/test-driven-development-three-passed-tests.png)
