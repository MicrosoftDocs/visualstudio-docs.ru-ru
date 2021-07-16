---
title: 'Учебник. Создание простого консольного приложения C# '
description: Ознакомьтесь с пошаговыми инструкциями по созданию консольного приложения на C# в Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 20732b0d7fb09de6079b0c1b7b06d2ae89802a5b
ms.sourcegitcommit: e7629e132a4d2fad6bb5869e4d68d9dbeeae9631
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2021
ms.locfileid: "113649176"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio-part-1-of-2"></a>Учебник. Создание простого консольного приложения C# в Visual Studio (часть 1 из 2)

В этом учебнике вы создадите и запустите консольное приложение C# с помощью Visual Studio, а также ознакомитесь с некоторыми возможностями интегрированной среды разработки (IDE) Visual Studio. Этот учебник представляет собой первую часть серии, состоящей из двух частей.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Создание проекта Visual Studio
> * Создание консольного приложения C#
> * Запустите отладку приложения.
> * Закрытие приложения
> * Проверка готового кода

[В части 2](tutorial-console-part-2.md) вы дополните это приложение другими проектами, узнаете о некоторых приемах отладки и укажете ссылки на сторонние пакеты.

## <a name="prerequisites"></a>Предварительные требования

Необходимо установить Visual Studio.

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2022"

Установите Visual Studio 2022 бесплатно со страницы [скачиваемых материалов предварительной версии Visual Studio 2022](https://visualstudio.microsoft.com/vs/preview/vs2022), если еще не сделали этого.

::: moniker-end

## <a name="create-a-project"></a>Создание проекта

Для начала мы создадим проект приложения C#. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

::: moniker range="vs-2017"

1. Откройте Visual Studio 2017.

2. В верхней строке меню последовательно выберите **Файл**  > **Создать**  > **Проект**.
   (Или нажмите **CTRL**+**SHIFT**+**N**).

3. В левой панели диалогового окна **Новый проект** разверните узел **C#** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)** . Присвойте файлу имя **_Calculator_**.

   ![Шаблон проекта "Консольное приложение (.NET Core)" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Добавление рабочей нагрузки (необязательно)

Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, его можно получить, добавив рабочую нагрузку **Кроссплатформенная разработка .NET Core**. Ниже описывается порядок действий.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Вариант 1: использование диалогового окна "Новый проект"

1. Выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**.

   ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

   ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Вариант 2: использование меню "Сервис"

1. Закройте диалоговое окно **Создать проект** и в верхней строке меню выберите **Сервис** > **Получить средства и компоненты**.

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Запустите Visual Studio.

1. На начальном экране выберите **Создать проект**.

   ![Просмотр окна "Создание проекта"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. В окне **Создание проекта** выберите **C#** в списке языков. Затем выберите **Windows** в списке платформ и **Консоль** в списке типов проектов. 

   Применив фильтры по языку, платформе и типу проекта, выберите шаблон **Консольное приложение** и щелкните **Далее**.

    :::image type="content" source="./media/vs-2019/csharp-create-new-project-console-net-core.png" alt-text="Выбор шаблона C# для консольного приложения (.NET Framework)":::

   > [!NOTE]
   > Если шаблон **Консольное приложение** отсутствует, его можно установить в окне **Создание проекта**. В сообщении **Не нашли то, что искали?** выберите ссылку **Установка других средств и компонентов**.
   >
   > ![Ссылка "Установка других средств и компонентов" из сообщения "Не нашли то, что искали?" в окне "Создание проекта"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > После этого в Visual Studio Installer выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core**.
   >
   > ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Затем нажмите кнопку **Изменить** в Visual Studio Installer. Вам может быть предложено сохранить результаты работы; в таком случае сделайте это. Выберите **Продолжить**, чтобы установить рабочую нагрузку. После этого вернитесь к шагу 2 в процедуре [Создание проекта](#create-a-project).

1. В поле **Имя проекта** окна **Настроить новый проект** введите *Calculator*. Затем щелкните **Далее**.

    :::image type="content" source="./media/vs-2019/csharp-name-your-calculator-project.png" alt-text="В окне &quot;Настроить новый проект&quot; назовите проект &quot;Calculator&quot;":::
   
1. В окне **Дополнительные сведения** для целевой платформы должна быть указана версия **.NET Core 3.1**. Если это не так, выберите **.NET Core 3.1**. Затем нажмите **Создать**.

    :::image type="content" source="./media/vs-2019/csharp-target-framework.png" alt-text="Проверка того, что в окне &quot;Дополнительные сведения&quot; указано .NET Core 3.1":::

   Visual Studio открывает новый проект, включающий код по умолчанию "Hello World".

::: moniker-end

## <a name="create-the-app"></a>Создание приложения

Во-первых, мы рассмотрим некоторые базовые расчеты для целых чисел в C#. Затем мы добавим код для создания простого калькулятора. После этого нам предстоит отладить приложение, чтобы найти и исправить ошибки. И, наконец, мы оптимизируем код для повышения эффективности.

### <a name="explore-integer-math"></a>Вычисления с целыми числами

Давайте начнем с базовых расчетов целых чисел в C#.

1. В редакторе кода удалите созданный по умолчанию код Hello, World!.

    ![Удаление стандартного кода Hello World из нового приложения калькулятора](./media/csharp-console-calculator-deletehelloworld.png)

   В частности, удалите строку с текстом: `Console.WriteLine("Hello World!");`.

1. Вместо нее введите следующий код:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Обратите внимание на то, что при этом функция IntelliSense в Visual Studio предлагает возможность автовыполнения записи.

    > [!NOTE]
    > Следующая анимация не предназначена для дублирования предыдущего кода. Она предназначена только для того, чтобы продемонстрировать, как работает функция автозаполнения.

    ![Анимация кода целочисленных вычислений, показывающая функцию автовыполнения IntelliSense в интегрированной среде разработки Visual Studio](./media/integer-math-intellisense.gif)

1. Нажмите зеленую кнопку **Пуск** или клавишу **F5** рядом с **калькулятором**, чтобы создать и запустить программу.

   ![Нажмите кнопку Calculator, чтобы запустить приложение с панели инструментов](./media/csharp-console-calculator-button.png)

   Откроется окно консоли с суммой 42 + 119, которая равна **161**.

    ![Окно консоли с результатами вычисления целых чисел](./media/csharp-console-integer-math.png)

1. **(Необязательно)** Можно изменить оператор, чтобы изменить результат. Например, можно изменить оператор `+` в строке кода `int c = a + b;` на `-` для вычитания, `*` для умножения или `/` для деления. Затем при запуске программы результат также изменится.

1. Закройте окно консоли.

### <a name="add-code-to-create-a-calculator"></a>Добавление кода для создания калькулятора

Давайте продолжим, добавляя более сложный набор кода калькулятора в проект.

1. Удалите весь код, который отображается в редакторе кода.

1. Введите или вставьте в редактор кода следующий код:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero.
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app.
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number.
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number.
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option.
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math.
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing.
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

1. Выберите **Calculator**, чтобы запустить программу, или нажмите клавишу **F5**.

   ![Нажмите кнопку Calculator, чтобы запустить приложение с панели инструментов](./media/csharp-console-calculator-button.png)

   Откроется окно консоли.

1. Просмотрите приложение в окне консоли и сложите числа **42** и **119**, пользуясь предложенными подсказками.

   Теперь приложение должно выглядеть как на следующем снимке экрана:

    ![Окно консоли с приложением "Калькулятор", в котором предоставляются подсказки по выбору действий](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Добавление функциональных возможностей в калькулятор

Давайте изменим этот код, чтобы добавить функциональные возможности.

### <a name="add-decimals"></a>Обработка десятичных чисел

Пока наше приложение принимает и возвращает только целые числа. Вычисления можно сделать точнее, добавив код для обработки десятичных чисел.

Как показано на следующем снимке экрана, при делении числа 42 на число 119 вы получите результат 0, что для нас недостаточно точно.

![Окно консоли с приложением калькулятора, которое возвращает результат без цифр после запятой](./media/csharp-console-calculator-nodecimal.png)

Давайте исправим код, чтобы он обрабатывал десятичные числа.

1. Нажмите клавиши **CTRL** + **H**, чтобы открыть элемент управления **Найти и заменить**.

1. Измените каждый экземпляр переменной `int` на `float`.

   Переключите **Учитывать регистр** (**ALT**+**C**) и **Слово целиком** (**ALT**+**W**) в элементе управления **Найти и заменить**.

    ![Анимация элемента управления "Поиск и замена", показывающая, как изменить переменную int на float](./media/find-replace-control-animation.gif)

1. Еще раз запустите приложение калькулятора и разделите число **42** на число **119**.

   Обратите внимание, что теперь приложение возвращает не просто ноль, а десятичное число.

    ![Окно консоли с приложением калькулятора, которое возвращает результат с десятичным числом](./media/csharp-console-calculator-decimal.png)

Но пока приложение только возвращает десятичные числа. Давайте изменим код так, чтобы приложение могло выполнять операции над десятичными числами.

1. Используйте элемент управления **Найти и заменить** (**CTRL** + **H**), чтобы изменить каждый экземпляр переменной `float` на `double` и каждый экземпляр метода `Convert.ToInt32` на `Convert.ToDouble`.

1. Запустите приложение калькулятора и разделите число **42,5** на число **119,75**.

   Обратите внимание на то, что теперь приложение принимает и возвращает значения десятичные числа.

    ![Окно консоли с приложением калькулятора, которое принимает и возвращает десятичные числа](./media/csharp-console-calculator-usedecimals.png)

    (Количество десятичных разрядов мы исправим с помощью инструкций по [пересмотру кода](#revise-the-code).)

## <a name="debug-the-app"></a>Отладка приложения

Мы уже улучшили наше простое приложение калькулятора, но пока оно не умеет обрабатывать исключения, включая ошибки во входных данных.

Например, при попытке разделить любое число на ноль или при вводе буквенного символа там, где приложение ожидает число (или наоборот), приложение может перестать работать, вернет ошибку или непредвиденный нечисловой результат.

Давайте рассмотрим несколько типичных ошибок во входных данных, найдем их с помощью отладчика, если они там есть, и исправим код, чтобы устранить их.

> [!TIP]
> Дополнительные сведения об отладчике и принципах его работы см. в разделе [Знакомство с отладчиком Visual Studio](../../debugger/debugger-feature-tour.md).

### <a name="fix-the-divide-by-zero-error"></a>Исправление ошибки деления на ноль

При попытке деления числа на ноль консольное приложение может перестать отвечать, а затем покажет, что именно не так в редакторе кода.

   ![Снимок экрана: редактор кода Visual Studio с выделенной желтым цветом строкой и отображенной ошибкой "Исключение не обработано" и причиной Attempted to divide by zero "Попытка деления на ноль".](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Иногда приложение не зависает, а отладчик не отображает ошибку деления на ноль. Вместо этого приложение может вернуть непредвиденный нечисловой результат, например символ бесконечности. Приведенное ниже исправление кода по-прежнему применимо.

Давайте изменим код, чтобы он обрабатывал такую ошибку.

1. Удалите код между `case "d":` и комментарием с текстом `// Wait for the user to respond before closing`.

1. Замените его следующим кодом.

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so.
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Когда вы добавите новый код, раздел с оператором `switch` будет выглядеть так, как показано на следующем снимке экрана:

   ![Доработанный раздел switch в редакторе кода Visual Studio](./media/csharp-console-calculator-switch-code.png)

Теперь при делении любого числа на ноль приложение предложит ввести другое число. Даже лучше: Оно будет снова и снова повторять этот запрос, пока не получит значение, отличающееся от нуля.

   ![Снимок экрана: редактор кода Visual Studio, отображающий код оператора switch с добавленной проверкой записи ненулевого делителя.](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Исправление ошибки формата

Если вы введете буквенный символ там, где приложение ожидает цифру (или наоборот), приложение консоли перестает работать. Visual Studio отображает причину проблемы в редакторе кода.

   ![Редактор кода Visual Studio с отображением ошибки формата](./media/csharp-console-calculator-format-error.png)

Чтобы устранить эту ошибку, мы выполним рефакторинг введенного ранее кода.

#### <a name="revise-the-code"></a>Пересмотр кода

Чтобы не делегировать всю обработку кода классу `program`, мы разделим приложение на два класса: `Calculator` и `Program`.

Класс `Calculator` выполняет основную часть работы для вычислений, а класс `Program` отвечает за пользовательский интерфейс и перехват ошибок.

Итак, начнем.

1. Удалите все в пространстве имен `Calculator` между открывающей и закрывающей фигурными скобками:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Теперь добавьте новый класс `Calculator` со следующим содержимым:

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Затем добавьте новый класс `Program` со следующим содержимым:

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
    ```

1. Выберите **Calculator**, чтобы запустить программу, или нажмите клавишу **F5**.

1. Разделите число **42** на число **119**, следуя подсказкам на экране. Теперь приложение должно выглядеть как на следующем снимке экрана:

    ![Окно консоли с измененным приложением калькулятора, где отображаются подсказки по выполнению действий и обработка ошибок неправильных входных данных](./media/csharp-console-calculator-refactored.png)

    Обратите внимание на то, что вы можете ввести несколько выражений, не закрывая консольное приложение. Также мы сократили количество десятичных разрядов в результате.

## <a name="close-the-app"></a>Закрытие приложения

1. Закройте приложение калькулятора, если оно еще открыто.

1. Закройте область **вывода** в Visual Studio.

   ![Закрытие области вывода в Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. В Visual Studio нажмите клавиши **CTRL**+**S**, чтобы сохранить приложение.

1. Закройте Visual Studio.

## <a name="review-code-complete"></a>Проверка: завершение кодирования

В этом руководстве мы внесли много изменений в приложение "Калькулятор". Теперь оно более эффективно использует вычислительные ресурсы и обрабатывает большинство ошибок во входных данных.

Ниже мы собрали в один блок весь код:

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>Следующие шаги

:::moniker range="vs-2017"

Другие руководства

> [!div class="nextstepaction"]
> [Руководства по C#](/dotnet/csharp/tutorials)

> [!div class="nextstepaction"]
> [Обзор интегрированной среды разработки Visual Studio](../visual-studio-ide.md)

:::moniker-end

:::moniker range=">=vs-2019"

Перейдите ко второй части этого руководства:

> [!div class="nextstepaction"]
> [Учебник, часть 2. Использование нескольких проектов и пакетов сторонних разработчиков](tutorial-console-part-2.md)
:::moniker-end

Полезные ресурсы

- [Продолжайте изучение учебников по C#](/dotnet/csharp/tutorials/)
- [Краткое руководство. Создание веб-приложения ASP.NET Core](../../ide/quickstart-aspnet-core.md)
- [Сведения об отладке кода C# в Visual Studio](tutorial-debugger.md)
- Пошаговое руководство по [созданию и запуску модульных тестов](../../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Запуск программы C#](run-program.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
- [Продолжайте обзор интегрированной среды разработки Visual Studio](/../visual-studio-ide.md)