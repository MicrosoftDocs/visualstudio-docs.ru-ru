---
title: Шаг 3. Назначение каждому элементу управления Label случайного значка
description: Узнайте, как присвоить каждому элементу управления Label случайный значок, чтобы значки не отображались в одной ячейке каждой игры.
ms.custom: SEO-VS-2020
ms.date: 03/21/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3254a986fb21c5a562d0d9a3c7f098d2b560dbfd
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214295"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Шаг 3. Назначение каждому элементу управления Label случайного значка

Если значки оказываются в одной и той же ячейке каждую игру, игра становится слишком простой. Чтобы избежать этого, назначайте значки элементам управления Label случайным образом, используя для этого метод `AssignIconsToSquares()`.

## <a name="to-assign-a-random-icon-to-each-label"></a>Назначение каждой метке случайного значка

1. Перед добавлением следующего кода разберитесь в принципе его работы. В C# есть новое ключевое слово `foreach`, а в Visual Basic — `For Each`. (Одна из строк закомментирована по причине, описанной в конце этой процедуры.)

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet2":::

      > [!IMPORTANT]
      > Используйте элемент управления языка программирования в правом верхнем углу этой страницы, чтобы просмотреть фрагмент кода на C# или Visual Basic.<br><br>![Элемент управления языка программирования для Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

2. Добавьте метод `AssignIconsToSquares()`, как показано в предыдущем шаге. Вы можете поместить его сразу же после кода, добавленного в разделе [Шаг 2. Добавление случайного объекта и списка значков](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Как было сказано выше, в методе `AssignIconsToSquares()` имеется определенное нововведение: цикл `foreach` в C# и `For Each` в Visual Basic. Цикл `For Each` можно использовать в любое время для выполнения одного и того же действия несколько раз. В этом случае требуется выполнять одни и те же операторы для каждого элемента управления Label в <xref:System.Windows.Forms.TableLayoutPanel>, как показано в следующем коде. Первая строка создает переменную с именем `control`, которая хранит каждый элемент управления по одному, пока у этого элемента управления есть инструкции в цикле, выполняемом для него.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet14":::

    > [!NOTE]
    > Используются имена iconLabel и control, поскольку они являются описательными. Можно заменить эти имена на любые другие и это не повлияет на работу кода (при условии, что имена будут изменены имена в каждом операторе внутри цикла).

     Метод `AssignIconsToSquares()` перебирает все элементы управления Label в TableLayoutPanel и выполняет одни и те же операторы для каждого из них. Эти операторы запрашивают случайные значки из списка, добавленного в разделе [Шаг 2. Добавление случайного объекта и списка значков](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). Помните, что каждый из этих значков является буквой в шрифте Webdings, поэтому в этом методе они выражены как текст. Вы включили в список по два значка. Это позволяет назначить пару значков случайным элементам управления Label.

     Внимательнее рассмотрите код, выполняемый внутри цикла `foreach` или `For Each`. Этот код воспроизведен здесь.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet16":::

     Первая строка преобразует переменную **control** в метку с именем **iconLabel**. Следующая строка представляет собой оператор `if`, проверяющий и обеспечивающий успешное выполнение преобразования. Если преобразование выполняется, выполняются операторы в операторе `if`. (Как можно вспомнить из предыдущих занятий, оператор `if` используется для проверки заданного условия). Первая строка в операторе `if` создает переменную с именем **randomNumber**, содержащую случайное число, соответствующее одному из элементов списка значков. Для этого используется метод <xref:System.Random.Next> объекта <xref:System.Random>, созданного ранее. Метод `Next` возвращает случайное число. Эта строка также использует свойство <xref:System.Collections.Generic.List%601.Count> списка **значков** для определения диапазона, из которого выбирается случайное число. В следующей строке один из элементов списка значков присваивается свойству <xref:System.Windows.Forms.Label.Text> этой метки. Пояснения относительно строки с комментариям приводятся далее в этом разделе. Наконец, последняя строка в операторе `if` удаляет из списка значок, добавленный в форму.

     Помните, если вы не уверены, что делает какая-либо часть кода, можно навести указатель мыши на элемент кода и посмотреть отображаемую подсказку. Можно также выполнять каждую строку кода пошагово после запуска программы, воспользовавшись отладчиком Visual Studio. Дополнительные сведения см. в руководствах по [началу работы с отладчиком в Visual Studio](https://msdn.microsoft.com/vstudio/ee672313.aspx) и [навигации по коду с помощью отладчика](../debugger/navigating-through-code-with-the-debugger.md).

3. Чтобы быстро заполнить игровое поле значками, необходимо вызвать метод `AssignIconsToSquares()` сразу после запуска программы. Если вы используете C#, добавьте оператор после вызова метода `InitializeComponent()` в **Form1** _constructor_. Так форма будет вызывать новый метод для настройки перед отображением. Конструкторы вызываются при создании нового объекта, такого как класс или структура. Дополнительные сведения см. в разделах [Конструкторы (руководство по программированию на C#)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) и [Использование конструкторов и деструкторов в Visual Basic](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)).

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet13":::

     В Visual Basic добавьте вызов метода `AssignIconsToSquares()` в метод `Form1_Load`, чтобы код выглядел следующим образом.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Сохраните и выполните программу. Должна отобразиться форма со случайными значками, которые назначены каждой метке. 

5. Закройте программу, а затем снова запустите ее. Обратите внимание, что теперь каждой метке назначены другие значки, как показано на следующем рисунке. 

     ![Игра "Подбери пару!" со случайными значками](../ide/media/express_tut4step3.png)<br/>
*Игра "Подбери пару!" со случайными значками*

     Значки видимы, поскольку они не были скрыты. Чтобы скрыть их от игрока, можно задать для свойства **ForeColor** каждого элемента управления Label тот же цвет, что и у свойства **BackColor**.

6. Чтобы скрыть значки, остановите программу и удалите метки комментариев с соответствующей строки кода в цикле `For Each`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet15":::

7. На панели меню нажмите кнопку **Сохранить все**, чтобы сохранить программу, а затем запустите программу. Похоже, что значки исчезли. Отображается только голубой фон. Однако значки назначены случайным образом и по-прежнему существуют. Поскольку значки имеют тот же цвет, что и фон, они невидимы, т. е. скрыты от игрока. Наконец, игра станет неинтересной, если игрок будет сразу видеть все значки!

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: **[Шаг 4. Добавление обработчика событий Click к каждому элементу управления Label](../ide/step-4-add-a-click-event-handler-to-each-label.md)** .

- Предыдущий раздел руководства: [Шаг 2. Добавление случайного объекта и списка значков](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
