---
title: Анализ данных по загрузке ЦП (C#, Visual Basic)
description: Измерение производительности приложения в C# и Visual Basic с помощью средства диагностики "Загрузка ЦП"
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 056996782d2b38adb96ee53250cc3ea0c0f75596
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761164"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Краткое руководство. Анализ данных по загрузке ЦП в Visual Studio (C#, Visual Basic)

Visual Studio предоставляет множество эффективных возможностей для анализа проблем с производительностью приложения. В этой статье вы ознакомитесь с некоторыми основными возможностями. Мы рассмотрим средство, позволяющее выявлять узкие места производительности, возникающие из-за высокой загрузки ЦП. Средства диагностики поддерживаются для разработки приложений .NET в Visual Studio, включая ASP.NET, и для разработки машинного кода или кода C++.

Центр диагностики предоставляет различные возможности по запуску сеансов диагностики и управлению ими. Если описываемое здесь средство **Загрузка ЦП** не предоставляет необходимые данные, можно воспользоваться [другими средствами профилирования](../profiling/profiling-feature-tour.md), предоставляющими другие виды информации, которая может оказаться полезной. Как правило, проблемы производительности приложения могут вызываться другими компонентами помимо ЦП, такими как память, отрисовка пользовательского интерфейса или время запроса сети. Профилировщик производительности предоставляет ряд других параметров для записи и анализа такого рода данных. Кроме того, используя еще одно встроенное в отладчик средство профилирования [PerfTips](../profiling/perftips.md), вы можете пошагово выполнить код и узнать, сколько времени требуется для завершения работы определенных функций или выполнения блоков кода.

Для запуска средств профилирования с отладчиком (окно **Средства диагностики**) требуется Windows 8 и более поздние версии. В Windows 7 и более поздних версиях можно использовать средство последующего анализа [Профилировщик производительности](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Создание проекта

1. Откройте Visual Studio и создайте проект.

   ::: moniker range="vs-2017"
   В верхней строке меню последовательно выберите **Файл** > **Создать** > **Проект**.

   В левой области диалогового окна **Создать проект** разверните узел **C#** или **Visual Basic** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)** . Назовите проект *MyProfilerApp*.

   Если шаблона проекта **Console App (.NET Core)** (Консольное приложение (.NET Core)) нет, выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Если окно запуска не открыто, выберите **Файл** > **Окно запуска**.

   На начальном экране выберите **Создать проект**.

   В поле поиска окна **Создание проекта** введите *консоль*. Затем выберите **C#** или **Visual Basic** в списке языков и **Windows** в списке платформ.

   Применив фильтры по языку и платформе, выберите шаблон **Консольное приложение** для .NET Core и нажмите кнопку **Далее**.

   > [!NOTE]
   > Если шаблон **Консольное приложение** отсутствует, его можно установить из окна **Создание проекта**. В сообщении **Не нашли то, что искали?** выберите ссылку **Установка других средств и компонентов**. После этого в Visual Studio Installer выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core**.

   В поле **Имя проекта** окна **Настроить новый проект** введите *MyProfilerApp*. Нажмите кнопку **Далее**.

   Выберите рекомендуемую версию целевой платформы (.NET Core 3.1) или .NET 5 и щелкните **Создать**.

   ::: moniker-end

   Новый проект открывается в Visual Studio.

2. Откройте файл *Program.cs* и замените все его содержимое следующим кодом:

    ```csharp
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading

    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000

            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")

                Dim x = GetNumber()
            End Sub

            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here
                ' and using Random to frustrate compiler optimizations
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class

        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()

                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()

                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")

            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > Убедитесь в том, что в Visual Basic задан автоматически запускаемый объект `Sub Main` (**Свойства** > **Приложение** > **Автоматически запускаемый объект**).

## <a name="step-1-collect-profiling-data"></a>Шаг 1. Сбор данных профилирования

1. Сначала установите точку останова в приложении в следующей строке кода в функции `Main`:

    `for (int i = 0; i < 200; i++)`

    Либо для Visual Basic:

    `For i As Integer = 0 To 199`

    Чтобы установить точку останова, щелкните во внешнем поле слева от строки кода.

2. Затем установите вторую точку останова в закрывающей фигурной скобке в конце функции `Main`:

     ![Установка точек останова для профилирования](../profiling/media/quickstart-cpu-usage-breakpoints.png "Установка точек останова для профилирования")

    С помощью двух точек останова можно ограничить сбор данных частями кода, которые требуется проанализировать.

3. Окно **Средства диагностики** должно отображаться, если вы не отключали эту функцию. Чтобы снова открыть окно, щелкните **Отладка** > **Окна** > **Показать средства диагностики**.

4. Щелкните **Отладка** > **Начать отладку** (**Запустить** на панели инструментов или **F5**).

     По завершении загрузки приложения отображается представление **Сводка** Средств диагностики.

5. Приостановив отладчик, включите сбор данных по загрузке ЦП, выбрав параметр **Запись профиля ЦП**, а затем откройте вкладку **Загрузка ЦП**.

     ![Средства диагностики, Включить профилирование ЦП](../profiling/media/quickstart-cpu-usage-summary.png "Средства диагностики, Включить профилирование ЦП")

     Когда сбор данных включен, на кнопке записи отображается красный кружок.

     При выборе параметра **Запись профиля ЦП** Visual Studio начнет записывать функции и сведения о времени их выполнения, а также будет выводить временной график, с помощью которого можно сосредоточить внимание на определенных частях сеанса профилирования. Эти собранные данные можно просматривать только в том случае, если приложение останавливается в точке останова.

6. Нажмите клавишу **F5**, чтобы запустить приложение до второй точки останова.

     Теперь у вас есть данные о производительности приложения именно для той области кода, которая выполняется между двумя точками останова.

     Профилировщик начинает подготавливать данные потока. Дождитесь завершения этой операции.

     Средство "Загрузка ЦП" выведет отчет на вкладке **Загрузка ЦП**.

     На этом этапе можно начать анализировать данные.

## <a name="step-2-analyze-cpu-usage-data"></a>Шаг 2. Анализ данных о загрузке ЦП

Мы рекомендуем начать анализ данных с проверки списка функций на вкладке "Загрузка ЦП" и выявления функций, выполняющих основную часть работы, а затем подробно рассмотреть каждую из этих функций.

1. В списке функций изучите функции, которые выполняют большую часть работы.

     ![Вкладка "Загрузка ЦП" в средствах диагностики](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Функции перечисляются, начиная с тех, которые выполняют большую часть работы (а не в порядке вызова). Это позволяет быстро находить функции, которые выполнялись дольше всего.

2. В списке функций дважды щелкните функцию `ServerClass::GetNumber`.

    В левой области откроется представление **Вызывающий/вызываемый**.

    ![Представление "Вызывающий/вызываемый" в средствах диагностики](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    В этом представлении выбранная функция отображается в заголовке и в поле **Текущая функция** (в этом примере `GetNumber`). Функция, вызывавшая текущую функцию, отображается в левой части окна в разделе **Вызывающая функция**, а все функции, вызываемые текущей функцией, отображаются в поле **Вызываемые функции** справа. (Можно выбрать любое поле, чтобы изменить текущую функцию.)

    В этом представлении показано общее время (мс) и доля общего времени выполнения приложения, затраченного на выполнение функции.

    В поле **Тело функции** также показан общий объем времени (и доля времени), затраченного в теле функции за исключением времени, затраченного в вызываемых и вызывающих функциях. (В этом примере в теле функции затрачено 2856 из 2863 мс, а остальное время (меньше 20 мс) затрачено во внешнем коде, вызванном этой функцией.) Фактические значения будут отличаться в зависимости от среды.

    > [!TIP]
    > Высокие значения в поле **Тело функции** могут свидетельствовать о проблемах производительности внутри самой функции.

## <a name="next-steps"></a>Следующие шаги

- [Анализируйте использование памяти](../profiling/memory-usage.md) для выявления узких мест производительности.
- [Анализируйте загрузку ЦП](../profiling/cpu-usage.md) для получения более подробных сведений о загрузке ЦП.
- Анализируйте загрузку ЦП без подключения отладчика или путем указания выполняющегося приложения. Дополнительные сведения см. в разделе [Сбор данных профилирования без отладки](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) и в статье [Выполнение средств профилирования с отладчиком и без него](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>См. также

- [Профилирование в Visual Studio](../profiling/index.yml)
- [Первое знакомство со средствами профилирования](../profiling/profiling-feature-tour.md)
