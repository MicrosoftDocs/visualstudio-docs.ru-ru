---
title: Шаг 3. Добавление таймера с обратным отсчетом
description: Узнайте, как добавить таймер обратного отсчета для отслеживания количества секунд, оставшихся у игрока на решение задач викторины.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8cd3ca99df01262d5a27f9f6ac22cd5f2e25836c
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296487"
---
# <a name="step-3-add-a-countdown-timer"></a>Шаг 3. Добавление таймера с обратным отсчетом

В третьей части этого учебника вам предстоит добавить таймер обратного отсчета для отслеживания количества секунд, оставшихся у игрока на решение задач викторины.

> [!NOTE]
> Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-countdown-timer"></a>Добавление таймера с обратным отсчетом

1. Добавьте целочисленную переменную с именем **timeLeft** точно так же, как в предыдущей процедуре. Код должен выглядеть так, как показано ниже.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet5":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Теперь вам необходим метод-таймер, который будет подсчитывать количество секунд и по истечении указанного времени вызывать событие.

2. В окне конструктора переместите элемент управления <xref:System.Windows.Forms.Timer> из категории **Компоненты** на **панели элементов** на свою форму.

     Элемент управления появляется в серой области в нижней части окна конструктора.

3. Щелкните в форме только что добавленный значок **timer1** и установите его свойство **Interval** равным **1000**.

     Так как значение интервала указывается в миллисекундах, при значении 1000 событие <xref:System.Windows.Forms.Timer.Tick> будет запускаться каждую секунду.

4. Двойным щелчком выберите в форме элемент управления **Timer** либо выделите его и нажмите клавишу **ВВОД**.

     Появится редактор кода с отображением метода для только что добавленного обработчика событий Tick.

5. Добавьте в новый метод обработчика событий следующие операторы.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet6":::

     Основываясь на добавленных операторах, таймер каждую секунду проверяет, истекло ли время, путем проверки того, является ли целочисленная переменная **timeLeft** больше 0. Если она больше 0, время еще осталось. Таймер сначала вычитает 1 из значения переменной timeLeft, а затем обновляет свойство **Text** элемента управления **timeLabel**, чтобы показать игроку, сколько осталось секунд.

     Если времени не осталось, таймер останавливается и изменяет текст в элементе управления **timeLabel** так, чтобы он показывал текст **Time's up!** (Время вышло!). Появляется окно сообщения о том, что игра закончена, и отображается ответ — в данном случае сумма переменной addend1 и переменной addend2. Свойству **Enabled** элемента управления **startButton** устанавливается значение **true**, чтобы игрок мог заново запустить викторину.

     Только что был добавлен оператор `if else`, в котором описывается, как программа принимает решение . Оператор `if else` представлен ниже.

    > [!NOTE]
    > Следующий пример приведен исключительно для демонстрации; не добавляйте его в свой проект.

    ```vb
    If (something that your program will check) Then
        ' One or more statements that will run
        ' if what the program checked is true.
    Else
        ' One or more statements that will run
        ' if what the program checked is false.
    End If
    ```

    ```csharp
    if (something that your program will check)
    {
        // One or more statements that will run
        // if what the program checked is true.
    }
    else
    {
        // One or more statements that will run
        // if what the program checked is false.
    }
    ```

     Внимательно рассмотрите оператор, который вы добавили в блок `else`, чтобы отобразить ответ на задачу на сложение.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet24":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet24":::

     Оператор `addend1 + addend2` складывает значения двух переменных. Первая часть (`sum.Value`) использует свойство **Value** элемента управления NumericUpDown суммы для отображения правильного ответа. Это же свойство позднее используется для проверки ответов на головоломку.

     Элемент управления <xref:System.Windows.Forms.NumericUpDown> позволяет игрокам легко вводить числа; именно поэтому мы используем его для ответов на арифметические задачи. Все возможные ответы представляют собой целые числа в диапазоне от 0 до 100. Оставив для свойств **Minimum**, **Maximum** и **DecimalPlaces** значения по умолчанию, вы гарантируете, что игроки не смогут вводить десятичные знаки, отрицательные числа или слишком большие числа. (Если, например, требуется разрешить игрокам ввести 3,141, но не 3,1415, можно задать для свойства **DecimalPlaces** значение, равное 3.)

6. Добавьте три строки в конец метода `StartTheQuiz()`, чтобы код выглядел так, как показано ниже.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet7":::

     Теперь при запуске головоломки переменная **timeLeft** устанавливается равной 30, а свойство **Text** элемента управления **timeLabel** устанавливается равным 30 секундам. После этого метод <xref:System.Windows.Forms.Timer.Start> элемента управления Timer начинает обратный отсчет. (Ответ пока не проверяется — это делается позже.)

7. Сохраните программу, запустите ее и нажмите кнопку **Запуск** в форме.

     Таймер начинает обратный отсчет. Когда время истечет, игра закончится и появится ответ. На следующем рисунка показана головоломка в процессе игры.

     ![Математическая головоломка в процессе игры](../ide/media/express_addcountdown.png)<br/>
*Математическая головоломка в процессе игры*

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: **[Шаг 4. Добавление метода CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)** .

- Предыдущий раздел [Шаг 2. Создание задачи на сложение случайных чисел](../ide/step-2-create-a-random-addition-problem.md).
