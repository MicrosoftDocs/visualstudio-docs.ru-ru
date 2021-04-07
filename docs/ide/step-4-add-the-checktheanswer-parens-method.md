---
title: Шаг 4. Добавление метода CheckTheAnswer()
description: Узнайте, как написать метод CheckTheAnswer(), который проверяет правильность ответов на арифметические задачи.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 369b668dfc0339c3b78fb1c33b5df1f3eab4619d
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214256"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Шаг 4. Добавление метода CheckTheAnswer()

В четвертой части этого урока вам предстоит написать метод `CheckTheAnswer()`, который проверяет правильность ответов на арифметические задачи. Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>Проверка правильности ответов

> [!NOTE]
> Если вы разрабатываете головоломку на Visual Basic, вам необходимо будет использовать ключевое слово `Function` вместо обычного ключевого слова `Sub`, потому что этот метод возвращает значение. Это объясняется просто: процедуры не возвращают значения, в отличие от функций.

1. Добавьте метод `CheckTheAnswer()`. Этот метод должен располагаться в строке с другими созданными методами, например `StartTheQuiz()`.

     При вызове этот метод складывает значения addend1 и addend2, а затем сравнивает результат со значением в элементе управления <xref:System.Windows.Forms.NumericUpDown> с именем sum. Если значения равны, метод возвращает значение `true`. В противном случае метод возвращает значение `false`. Код должен выглядеть так, как показано ниже.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs" id="Snippet8":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Далее предстоит проверить ответ путем изменения кода в этом методе, чтобы обработчик события <xref:System.Windows.Forms.Timer.Tick> таймера вызвал новый метод `CheckTheAnswer()`.

2. Добавьте следующий код в инструкцию `if else` в методе `Timer1_Tick()`, чтобы таймер останавливался, когда пользователь получает право на ответ.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs" id="Snippet10":::

     Если ответ правильный, `CheckTheAnswer()` возвращает значение `true`. Обработчик событий останавливает таймер, выводит поздравительное сообщение, а затем снова делает кнопку **Запуск** доступной. В противном случае головоломка продолжается.

3. Сохраните программу, запустите ее, запустите головоломку и введите правильный ответ на задачу сложения.

    > [!NOTE]
    > При вводе ответа необходимо либо выделить значение по умолчанию перед началом ввода ответа, либо удалить нуль вручную. Позднее в этом уроке мы исправим это поведение.

     При вводе правильного ответа появляется окно сообщения, кнопка **Запуск** становится доступной, и таймер останавливается.

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: **[Шаг 5. Добавление обработчиков событий входа для элементов управления NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)** .

- Предыдущий раздел руководства: [Шаг 3. Добавление таймера с обратным отсчетом](../ide/step-3-add-a-countdown-timer.md).
