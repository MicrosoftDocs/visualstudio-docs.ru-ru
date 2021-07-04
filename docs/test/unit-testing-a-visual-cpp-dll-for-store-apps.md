---
title: Тестирование библиотеки DLL на C++ для приложений UWP
description: Узнайте, как создавать модульные тесты для библиотеки DLL на C++ для приложений универсальной платформы Windows с использованием среды тестирования Майкрософт для C++.
ms.custom: SEO-VS-2020
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: jmartens
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: f1981b3876d2e42e992ef261738da2443edfc114
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042916"
---
# <a name="how-to-test-a-c-dll"></a>Тестирование Библиотеки DLL C++

В этом разделе описывается один способ создания модульных тестов для библиотеки DLL на C++ для приложений на универсальной платформе Windows (UWP) с использованием среды тестирования Майкрософт для C++. Библиотека DLL RooterLib демонстрирует концепции теории пределов из математического анализа за счет реализации функции, которая вычисляет оценку квадратного корня из заданного числа. Библиотеки DLL могут быть включены в приложение UWP, демонстрирующее пользователям интересные вещи, которые можно сделать с помощью математических функций.

В этом разделе показано использование модульного тестирования в качестве первого шага разработки. При таком подходе сначала необходимо написать метод теста, который проверяет определенное поведение тестируемой системы, а затем написать код, который проходит этот тест. Порядок описанных ниже процедур можно изменить, и сначала написать код, который требуется протестировать, а затем написать сами модульные тесты.

В этом разделе также создается одно решение Visual Studio и отдельные проекты для модульных тестов и для тестируемой библиотеки DLL. Модульные тесты можно включить непосредственно в проект библиотеки DLL или создать отдельные решения для модульных тестов и для библиотеки DLL. Рекомендации по выбору структуры см. в разделе [Добавление модульных тестов в существующие приложения C++](../test/how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="Create_the_solution_and_the_unit_test_project"></a> Создание решения и проекта модульного теста

::: moniker range=">=vs-2019"

Начнем с создания нового тестового проекта. В меню **Файл** последовательно выберите пункты **Создать** > **Проект**. В диалоговом окне **Создание нового проекта** в поле поиска введите "тест" и задайте **Язык** как C++. В списке шаблонов проектов выберите **Приложение модульного тестирования (универсальное приложение Windows)** .

   ![Создание нового тестового проекта UWP](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Начнем с создания нового тестового проекта. В меню **Файл** последовательно выберите пункты **Создать** > **Проект**. В диалоговом окне **Новый проект** разверните узел **Установленные** > **Visual C++** и выберите **Универсальные приложения Windows**. В списке шаблонов проектов выберите **Приложение модульного тестирования (универсальное приложение Windows)** .

::: moniker-end

1. В диалоговом окне "Новый проект" разверните узел **Установленные** > **Visual C++** и выберите **Универсальные приложения Windows**. В списке шаблонов проектов выберите **Приложение модульного тестирования (универсальное приложение Windows)** .

2. Назовите проект `RooterLibTests`, укажите расположение, назовите решение `RooterLib`, установите флажок **Создать каталог для решения**.

     ![Задание решения, имени проекта и расположения](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. В новом проекте откройте файл **unittest1.cpp**.

     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Обратите внимание на следующее.

    - Каждый тест определяется с использованием `TEST_METHOD(YourTestName){...}`.

         Стандартную сигнатуру функции писать не требуется. Сигнатура создается макросом TEST_METHOD. Макрос создает функцию экземпляра, которая возвращает значение void. Она также создает статическую функцию, которая возвращает сведения о тестовом методе. Эти сведения позволят обозревателю тестов найти этот метод.

    - Тестовые методы группируются в классы с помощью `TEST_CLASS(YourClassName){...}`.

         Во время выполнения тестов создается экземпляр каждого тестового класса. Тестовые методы вызываются в неопределенном порядке. Можно задать особые методы, которые вызываются до и после каждого модуля, класса или метода. Дополнительные сведения см. в разделе [Использование Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="Verify_that_the_tests_run_in_Test_Explorer"></a> Проверка с помощью обозревателя тестов того, что тесты запускаются

1. Добавьте код теста:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Обратите внимание, что класс `Assert` содержит несколько статических методов, которые можно использовать для проверки результатов в тестовых методах.

2. В меню **Тест** выберите **Выполнить**, а затем выберите **Запустить все**.

     Будет построен и запущен проект теста. Появится окно **обозревателя тестов**, а тест будет указан в разделе **Пройденные тесты**. Область **сводки** в нижней части окна содержит дополнительные сведения о выбранном тесте.

     ![Обозреватель тестов](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-dll-project-to-the-solution"></a><a name="Add_the_DLL_project_to_the_solution"></a> Добавление в решение проекта библиотеки DLL

::: moniker range=">=vs-2019"

В **обозревателе решений** выберите имя решения. В контекстном меню выберите команду **Добавить**, а затем — пункт **Новый проект**. В диалоговом окне **Добавление нового проекта** задайте **Язык** как C++ и введите "DLL" в поле поиска. В списке результатов выберите **Приложение модульного тестирования (универсальная платформа Windows — C++ или CX)** .

![Создание проекта RooterLib](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
В **обозревателе решений** выберите имя решения. В контекстном меню выберите команду **Добавить**, а затем — пункт **Новый проект**.

![Создание проекта RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. В диалоговом окне **Добавление нового проекта** выберите **DLL (UWP apps)** (DLL — приложения UWP).

2. Добавьте следующий код в файл *RooterLib.h*:

    ```cpp
    // The following ifdef block is the standard way of creating macros which make exporting
    // from a DLL simpler. All files within this DLL are compiled with the ROOTERLIB_EXPORTS
    // symbol defined on the command line. This symbol should not be defined on any project
    // that uses this DLL. This way any other project whose source files include this file see
    // ROOTERLIB_API functions as being imported from a DLL, whereas this DLL sees symbols
    // defined with this macro as being exported.
    #ifdef ROOTERLIB_EXPORTS
    #define ROOTERLIB_API  __declspec(dllexport)
    #else
    #define ROOTERLIB_API __declspec(dllimport)
    #endif //ROOTERLIB_EXPORTS

    class ROOTERLIB_API CRooterLib {
    public:
        CRooterLib(void);
        double SquareRoot(double v);
    };
    ```

     Комментарии содержат пояснения к блоку ifdef не только для разработчика библиотеки DLL, но и для тех, кто ссылается на библиотеку DLL в своих проектах. С помощью свойств проекта библиотеки DLL можно добавить в командную строку символ ROOTERLIB_EXPORTS.

     Класс `CRooterLib` объявляет конструктор и метод оценки `SqareRoot`.

3. Добавьте символ ROOTERLIB_EXPORTS в командную строку.

    1. В **обозревателе решений** выберите проект **RooterLib**, а затем пункт **Свойства** в контекстном меню.

         ![Добавление определения символа препроцессора](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. В диалоговом окне **страницы свойств RooterLib** разверните узел **Свойства конфигурации**, затем — узел **C++** и выберите параметр **Препроцессор**.

    3. Выберите пункт **\<Edit...>** в списке **Определения препроцессора**, а затем добавьте `ROOTERLIB_EXPORTS` в диалоговом окне **Определения препроцессора**.

4. Добавьте минимальные реализации объявленных функций. Откройте файл *RooterLib.cpp* и добавьте следующий код:

    ```cpp
    // constructor
    CRooterLib::CRooterLib()
    {
    }

    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        return 0.0;
    }

    ```

## <a name="make-the-dll-functions-visible-to-the-test-code"></a><a name="make_the_dll_functions_visible_to_the_test_code"></a> Сделайте функции DLL доступными для кода тестов

1. Добавьте RooterLib в проект RooterLibTests.

   1. В **обозревателе решений** выберите проект **RooterLibTests**, а затем в контекстном меню последовательно выберите **Добавить** > **Ссылки**.

   1. В диалоговом окне **Добавление ссылки** откройте вкладку **Проекты**. Затем выберите элемент **RouterLib**.

2. Включите файл заголовка RooterLib в файл *unittest1.cpp*.

   1. Откройте файл *unittest1.cpp*.

   2. Добавьте следующий код ниже строки `#include "CppUnitTest.h"`:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Добавьте тест, который использует импортированную функцию. Добавьте следующий код в файл *unittest1.cpp*:

   ```cpp
   TEST_METHOD(BasicTest)
   {
       CRooterLib rooter;
       Assert::AreEqual(
           // Expected value:
           0.0,
           // Actual value:
           rooter.SquareRoot(0.0),
           // Tolerance:
           0.01,
           // Message:
           L"Basic test failed",
           // Line number - used if there is no PDB file:
           LINE_INFO());
   }
   ```

4. Постройте решение.

    Новый тест появится в **обозревателе тестов** в узле **Незапускавшиеся тесты**.

5. В **обозревателе тестов** выберите **Запустить все**.

    ![Основной тест пройден](../test/media/ute_cpp_testexplorer_basictest.png)

   Вы настроили тест и проекты кода и подтвердили, что можно выполнять тесты, которые запускают функции из проекта кода. Теперь можно начать писать реальные тесты и код.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="Iteratively_augment_the_tests_and_make_them_pass"></a> Итеративное расширение тестов и обеспечение их успешного выполнения

1. Добавьте новый тест.

    ```cpp
    TEST_METHOD(RangeTest)
    {
        CRooterLib rooter;
        for (double v = 1e-6; v < 1e6; v = v * 3.2)
        {
            double expected = v;
            double actual = rooter.SquareRoot(v*v);
            double tolerance = expected/1000;
            Assert::AreEqual(expected, actual, tolerance);
        }
    };
    ```

    > [!TIP]
    > Рекомендуется не изменять пройденные тесты. Вместо этого добавьте новый тест, обновите код так, чтобы тест проходил успешно, а затем добавьте еще один тест и т. д.
    >
    > При изменении пользователями требований отключите тесты, которые больше не являются корректными. Создайте новые тесты и сделайте так, чтобы они работали по одному в инкрементном режиме.

2. В **обозревателе тестов** выберите **Запустить все**.

3. Тест не пройден.

     ![Сбой теста RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Убедитесь в том, что каждый тест завершается сбоем, сразу после того, как вы написали его. Это поможет избежать распространенной ошибки, заключающейся в написании теста, который никогда не завершается сбоем.

4. Измените код теста, чтобы новый тест был пройден. Добавьте в файл *RooterLib.cpp* следующий код:

    ```cpp
    #include <math.h>
    ...
    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        double result = v;
        double diff = v;
        while (diff > result/1000)
        {
            double oldResult = result;
            result = result - (result*result - v)/(2*result);
            diff = abs (oldResult - result);
        }
        return result;
    }

    ```

5. Выполните сборку решения, а затем в **обозревателе тестов** щелкните **Запустить все**.

     Оба теста будут пройдены успешно.

> [!TIP]
> Разрабатывайте код, добавляя тесты по одному. После каждой итерации проверяйте, все ли тесты завершаются успешно.

## <a name="debug-a-failing-test"></a><a name="Debug_a_failing_test"></a> Отладка непройденного теста

1. Добавьте еще один тест в файл *unittest1.cpp*:

   ```cpp
   // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRooterLib rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          swprintf_s(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          swprintf_s(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
   };
   ```

2. В **обозревателе тестов** выберите **Запустить все**.

    Тест не пройден. Выберите имя теста в **обозревателе тестов**. Ошибочное проверочное утверждение будет выделено. Сообщение об ошибке отображается в области сведений **обозревателя тестов**.

    ![Сбой тестов NegativeRangeTests](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Чтобы увидеть, почему тест не был пройден, выполните функцию пошагово.

   1. Установите точку останова перед функцией `SquareRoot`.

   2. В контекстном меню непройденного теста выберите **Отладить выбранные тесты**.

        Когда выполнение прекратится на точке останова, выполните код по шагам.

   3. Добавьте код в файл *RooterLib.cpp*, чтобы перехватить исключение:

       ```cpp
       #include <stdexcept>
       ...
       double CRooterLib::SquareRoot(double v)
       {
           //Validate the input parameter:
           if (v < 0.0)
           {
             throw std::out_of_range("Can't do square roots of negatives");
           }
       ...

       ```

   1. В **обозревателе тестов** выберите **Запустить все**, чтобы протестировать исправленный метод и убедиться в том, что не была добавлена регрессия.

   Теперь все тесты проходят успешно.

   ![Все тесты пройдены](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code-without-changing-tests"></a><a name="Refactor_the_code_without_changing_tests"></a> Рефакторинг кода без изменения тестов

1. Упростите основной расчет функции `SquareRoot`:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Выберите команду **Запустить все**, чтобы протестировать подвергнутый рефакторингу метод и убедиться в том, что не была добавлена регрессия.

    > [!TIP]
    > Стабильный набор хороших модульных тестов придает уверенность в том, что изменение кода не привело к появлению ошибок.
    >
    > Рефакторинг должен осуществляться отдельно от других изменений.
