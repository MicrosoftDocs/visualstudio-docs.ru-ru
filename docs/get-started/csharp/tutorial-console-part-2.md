---
title: Учебник 2. Расширение консольного приложения C#
description: Ознакомьтесь с пошаговыми инструкциями по разработке консольного приложения на C# в Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 04/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f7d1ae7d0d5f045c0772243c7fc4011a9f31088e
ms.sourcegitcommit: e7629e132a4d2fad6bb5869e4d68d9dbeeae9631
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2021
ms.locfileid: "113649160"
---
# <a name="tutorial-extend-c-console-app-and-debug-in-visual-studio-part-2-of-2"></a>Учебник. Расширение консольного приложения C# и отладка в Visual Studio (часть 2 из 2)

В части 2 этой серии учебников вы узнаете чуть больше о функциях сборки и отладки в Visual Studio, необходимых для повседневных задач разработки, например об управлении несколькими проектами, отладке и ссылках на сторонние пакеты. Вы запустите консольное приложение C#, созданное в части 1 этого учебника (tutorial-console.md), и изучите некоторые функции интегрированной среды разработки (IDE) Visual Studio. Этот учебник представляет собой вторую часть серии, состоящей из двух частей.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Добавление еще одного проекта к первому
> * Ссылка на библиотеки и добавление пакетов
> * Отладка
> * Проверка готового кода


## <a name="prerequisites"></a>Предварительные требования

Необходимо:
+ Использовать [консольное приложение калькулятора из части 1 этой серии учебников](tutorial-console.md). 
+ Использовать приложение калькулятора на C# из [репозитория vs-tutorial-samples](https://github.com/MicrosoftDocs/vs-tutorial-samples), которое можно [открыть в репозитории](../tutorial-open-project-from-repo.md), чтобы начать работу.

## <a name="add-another-project"></a>Добавление еще одного проекта

Реальный код связан со множеством проектов, объединенных в решение. Давайте добавим еще один проект в приложение калькулятора. Это будет библиотека классов, предоставляющая некоторые функции калькулятора.

1. В Visual Studio можно использовать команду меню верхнего уровня **Файл** > **Добавить** > **Новый проект**, чтобы добавить новый проект, но можно также щелкнуть правой кнопкой мыши имя существующего проекта ("узел проекта") и открыть контекстное меню проекта. Это контекстное меню предлагает различные варианты добавления функциональных возможностей в проекты. Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и последовательно выберите **Добавить** > **Новый проект**.

1. Выберите шаблон проекта C# **Библиотека классов (.NET Standard)** .

   ![Снимок экрана: выбор шаблона проекта "Библиотека классов"](media/vs-2019/calculator2-add-project-dark.png)

1. Введите имя проекта **CalculatorLibrary** и щелкните **Создать**. Снова при появлении запроса выберите .NET 3.1. Visual Studio создаст новый проект и добавит его в решение.

   ![Снимок экрана: обозреватель решений с добавленным проектом библиотеки классов CalculatorLibrary](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Вместо *Class1.cs* переименуйте файл в **CalculatorLibrary.cs**. Можно щелкнуть имя в **обозреватель решений**, чтобы указать другое имя, или щелкнуть правой кнопкой мыши и выбрать **Переименовать** или нажать клавишу **F2**.

   Возможно, вам будет предложено переименовать все ссылки на `Class1` в файле. Вы можете выбрать любой ответ, так как вы замените код на следующем шаге.

1. Теперь необходимо добавить ссылку на проект, чтобы первый проект мог использовать API, предоставляемые новой библиотекой классов.  Правой кнопкой мыши щелкните узел **Зависимости** в первом проекте и выберите **Добавить ссылку на проект**.

   ![Снимок экрана: пункт меню "Добавить ссылку на проект"](media/vs-2019/calculator2-add-project-reference-dark.png)

   Откроется диалоговое окно **Диспетчер ссылок**. Это диалоговое окно позволяет добавлять ссылки на другие проекты, а также сборки и библиотеки DLL COM, необходимые вашим проектам.

   ![Снимок экрана: диалоговое окно "Диспетчер ссылок"](media/vs-2019/calculator2-ref-manager-dark.png)

1. В диалоговом окне **Диспетчер ссылок** установите флажок для проекта **CalculatorLibrary** и выберите **ОК**.  Ссылка на проект отображается в узле **Проекты** в **обозревателе решений**.

   ![Снимок экрана: обозреватель решений со ссылкой на проект](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. В файле *Program.cs* выберите класс `Calculator` и весь его код и нажмите **CTRL+X**, чтобы вырезать его из Program.cs. Затем в **CalculatorLibrary**, в файле *CalculatorLibrary.cs*, вставьте код в пространство имен `CalculatorLibrary`. Затем объявите класс калькулятора как `public`, чтобы предоставить его за пределами библиотеки. Теперь код в *CalculatorLibrary.cs* должен выглядеть следующим образом:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. Первый проект содержит ссылку, но вы увидите ошибку, так как вызов Calculator.DoOperation не разрешается. Это связано с тем, что CalculatorLibrary находится в другом пространстве имен, поэтому добавьте пространство имен `CalculatorLibrary` для полной ссылки.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Попробуйте добавить директиву using в начало файла:

   ```csharp
   using CalculatorLibrary;
   ```

   Это изменение позволяет удалить пространство имен CalculatorLibrary из места вызова, но это приводит к неоднозначности. Является ли `Calculator` классом в CalculatorLibrary или Calculator является пространством имен?  Чтобы устранить неоднозначность, переименуйте пространство имен `CalculatorProgram`.

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Ссылки на библиотеки .NET: запись в журнал

1. Предположим, что теперь нужно добавить журнал всех операций и записать его в текстовый файл. Класс .NET `Trace` предоставляет эти функции. (Он также удобен для базовых методов отладки печати.) Класс Trace находится в пространстве имен System.Diagnostics. Нам понадобятся классы System.IO, такие как `StreamWriter`, поэтому начните с добавления директив using вверху файла *CalculatorLibrary.cs*:

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Просмотрев, как используется класс Trace, придерживайтесь ссылки на класс, связанный с файловым потоком. Это означает, что калькулятор будет работать лучше в качестве объекта, поэтому давайте добавим конструктор в начало класса Calculator в *CalculatorLibrary.cs*.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. Нам следует поменять статический метод `DoOperation` на метод-член, для чего удалим ключевое слово `static`.  Давайте также добавим выходные данные в каждый расчет для журнала, чтобы DoOperation выглядел следующим образом:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Теперь в файле *Program.cs* статический вызов помечен красной волнистой линией. Чтобы исправить это, создайте переменную `calculator`, добавив непосредственно перед циклом `while (!endApp)` следующую строку:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Также измените место вызова для `DoOperation` следующим образом, чтобы ссылаться на объект с именем `calculator` в нижнем регистре. Таким образом, это будет не вызов статического метода, а вызов члена:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Запустите программу еще раз, а затем щелкните правой кнопкой мыши узел проекта, выберите **Открыть папку в проводнике файлов**, перейдите к выходной папке, например *bin/Debug/netcoreapp3.1*, и откройте файл *calculator.log*.

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

Сейчас файл *CalculatorLibrary.cs* должен быть подобен следующему:

```csharp
using System;
using System.IO;
using System.Diagnostics;


namespace CalculatorLibrary
{
    public class Calculator
    {

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                    break;
                case "s":
                    result = num1 - num2;
                    Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                    break;
                case "m":
                    result = num1 * num2;
                    Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }
}
```

А файл *Program.cs* — иметь примерно следующий вид:

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Добавление пакета NuGet: запись в JSON-файл

1. Теперь предположим, что мы хотим вывести операции в формате JSON — популярном и переносимом формате для хранения данных объекта. Чтобы реализовать эту функциональность, необходимо сослаться на пакет NuGet Newtonsoft.Json. Пакеты NuGet являются основным средством распространения библиотек классов .NET. В **Обозревателе решений** щелкните правой кнопкой мыши узел **Зависимости** для проекта CalculatorLibrary и выберите **Управление пакетами NuGet**.

   ![Снимок экрана: "Управление пакетами NuGet" в контекстном меню.](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Откроется диспетчер пакетов NuGet.

   ![Снимок экрана: диспетчер пакетов NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Найдите пакет Newtonsoft.Json и нажмите **Установить**.

   ![Снимок экрана: сведения о пакете NuGet Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Пакет будет загружен и добавлен в проект, а в узле "Ссылки" в **обозревателе решений** появится новая запись.

1. Добавьте директиву using для System.IO и пакета Newtonsoft.Json в начало файла *CalculatorLibrary.cs*.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Теперь замените конструктор для калькулятора на следующий код и создайте объект члена JsonWriter:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. Измените метод `DoOperation`, чтобы добавить код модуля записи JSON:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Необходимо добавить метод для завершения синтаксиса JSON после ввода пользователем всех данных для операции.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. В *Program.cs* добавьте вызов Finish в конце.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Выполните сборку приложения и запустите его. Попробуйте выполнить несколько операций и закройте приложение, используя команду "n".  Теперь откройте файл calculatorlog.json, который будет содержать примерно следующее.

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Отладка. Установка точки останова и попадание в нее

Отладчик Visual Studio — мощное средство для пошагового выполнения кода в поисках точки, в которой вы допустили ошибку при написании программы. Таким образом, вы получите возможность проанализировать код и внести в него необходимые исправления. Visual Studio позволяет вносить временные изменения, чтобы можно было продолжить выполнение программы.

1. В *Program.cs* щелкните поле слева от указанного ниже кода (или откройте контекстное меню и выберите пункт **Точка останова** > **Вставить точку останова**, либо нажмите клавишу **F9**):

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Красный кружок, который отображается, указывает на точку останова. Для приостановки приложения и проверки кода можно использовать точки останова. Вы можете установить точку останова в любой исполняемой строке кода.

   ![Снимок экрана: установка точки останова](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Выполните сборку и запустите приложение.

1. В выполняющемся приложении введите некоторые значения для вычисления:

   - Для первого числа введите **8**.
   - Для второго числа введите **0**.
   - В качестве оператора введите **d**.

   Приложение приостанавливается в созданной точке останова, которая обозначается желтым указателем слева и выделенным кодом. Выделенный код еще не выполнен.

   ![Снимок экрана: попадание в точку останова](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Теперь, когда приложение приостановлено, вы можете проверить состояние приложения.

## <a name="debug-view-variables"></a>Отладка. Просмотр переменных

1. В выделенном коде наведите указатель мыши на переменные, такие как `cleanNum1` и `op`. Вы увидите текущие значения этих переменных (`8` и `d` соответственно), которые отображаются в подсказках по данным.

   ![Снимок экрана: просмотр подсказок по данным](media/vs-2019/calculator-2-debug-view-datatip.png)

   При отладке очень важно выполнить проверку переменных на содержание соответствующих значений для устранения проблем.

2. В нижней области просмотрите окно **Локальные**. (Если оно закрыто, выберите **Отладка** > **Окна** > **Локальные**, чтобы открыть его.)

   В окне "Локальные" отображаются все переменные, находящиеся в области, а также их значения и типы.

   ![Снимок экрана: окно "Локальные"](media/vs-2019/calculator-2-debug-locals-window.png)

3. Взгляните на окно **Видимые**.

   Окно "Видимые" аналогично окну **Локальные**, но отображает переменную непосредственно перед текущей строкой кода и после строки, в которой приостановлено приложение.

   Далее можно поочередно выполнить код в отладчике по одной инструкции за раз. Это называется *пошаговым выполнением*.

## <a name="debug-step-through-code"></a>Отладка. Пошаговое прохождение кода

1. Нажмите клавишу **F11** (или выберите **Отладка** > **Выполнять по шагам**).

   С помощью команды "Выполнять по шагам" приложение выполняет текущий оператор и переходит к следующему исполняемому оператору (как правило, это следующая строка кода). Желтый указатель слева всегда указывает на текущий оператор.

   ![Снимок экрана: команда "Выполнять по шагам"](media/vs-2019/calculator-2-debug-step-into.png)

   Вы только что выполнили по шагам метод `DoOperation` в классе `Calculator`.

1. Чтобы получить иерархический обзор выполнения программы, просмотрите окно **Стек вызовов**. (Если оно закрыто, выберите **Отладка** > **Окна** > **Стек вызовов**.)

   ![Снимок экрана: стек вызовов](media/vs-2019/calculator-2-debug-call-stack.png)

   В этом представлении отображается текущий метод `Calculator.DoOperation`, обозначенный желтым указателем, а во второй строке показана функция, которая его вызвала из метода `Main` в *Program.cs*. В окне **Стек вызовов** показан порядок вызова методов и функций. Кроме того, оно предоставляет доступ ко многим функциям отладчика, таким как **Перейти к исходному коду**, из контекстного меню.

1. Нажмите клавишу **F10** (или выберите **Отладка** > **Шаг с обходом**) несколько раз, пока приложение не остановится в операторе `switch`.

   ```csharp
   switch (op)
   {
   ```

   Команда "Шаг с обходом" аналогична команде "Выполнять по шагам", за исключением того, что если текущий оператор вызывает функцию, то отладчик выполняет код в вызываемой функции и не приостанавливает выполнение до возврата функции. Команда "Шаг с обходом" — это более быстрый способ навигации по коду, если вас не интересует определенная функция.

1. Нажмите клавишу **F10** еще раз, чтобы приложение приостанавливалось на следующей строке кода.

   ```csharp
   if (num2 != 0)
   {
   ```

   Этот код проверяет деление на нуль. Если приложение продолжает работать, оно вызовет общее исключение (ошибку). Предположим, вы считаете, что это ошибка, и хотите выполнить другое действие, например просмотреть фактическое возвращаемое значение в консоли. Один из вариантов — использовать функцию отладчика "Изменить и продолжить", чтобы внести изменения в код и продолжить отладку. Тем не менее мы покажем другой метод для временного изменения потока выполнения.

## <a name="debug-test-a-temporary-change"></a>Отладка. Тестирование временного изменения

1. Выберите желтый указатель, который в данный момент приостановлен на операторе `if (num2 != 0)`, и перетащите его в следующий оператор.

   ```csharp
   result = num1 / num2;
   ```

   При этом приложение полностью пропускает оператор `if`, чтобы вы могли увидеть, что происходит при делении на ноль.

1. Нажмите клавишу **F10**, чтобы выполнить строку кода.

1. Наведите указатель мыши на переменную `result`, вы увидите, что она сохраняет значение `Infinity`.

   В C# `Infinity` является результатом деления на ноль.

1. Нажмите клавишу **F5** (или выберите **Отладка** > **Продолжить отладку**).

   Символ бесконечности отображается в консоли как результат математической операции.

1. Закройте приложение должным образом с помощью команды n.

## <a name="code-complete"></a>Полный код

Ниже приведен полный код для файла *CalculatorLibrary.cs* после выполнения всех шагов:

```csharp
using System;
using System.IO;
using System.Diagnostics;
using Newtonsoft.Json;

namespace CalculatorLibrary
{
    public class Calculator
    {

        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }

        public void Finish()
        {
            writer.WriteEndArray();
            writer.WriteEndObject();
            writer.Close();
        }
    }
}
```

А вот код для файла *Program.cs*: 

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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
            calculator.Finish();
            return;
        }
    }
}
```

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого учебника! Для получения дополнительных сведений изучите следующие ресурсы.

- [Продолжайте изучение учебников по C#](/dotnet/csharp/tutorials/)
- [Краткое руководство. Создание веб-приложения ASP.NET Core](../../ide/quickstart-aspnet-core.md)
- [Сведения об отладке кода C# в Visual Studio](tutorial-debugger.md)
- Пошаговое руководство по [созданию и запуску модульных тестов](../../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Запуск программы C#](run-program.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
- [Продолжайте обзор интегрированной среды разработки Visual Studio](/../visual-studio-ide.md)
