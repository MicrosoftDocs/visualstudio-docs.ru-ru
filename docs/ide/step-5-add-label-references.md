---
title: Шаг 5. Добавление ссылок на элементы управления Label
description: Узнайте, как добавить в форму ссылки на элементы управления Label.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 316db91ac00ca9e18b9c0875340d2358b8955bed
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214230"
---
# <a name="step-5-add-label-references"></a>Шаг 5. Добавление ссылок на элементы управления Label
Программе нужно отслеживать, какие элементы управления Label выбирает игрок. В настоящий момент программа отображает все метки, выбранные игроком. Однако мы изменим это. После выбора первой метки программа должна показывать ее значок. После выбора второй метки программа должна показать оба значка на короткое время, а затем снова скрыть их. Теперь программа будет отслеживать, какой элемент управления Label выбран первым, а какой — вторым, с помощью *ссылочных переменных*.

## <a name="to-add-label-references"></a>Добавление ссылок на метки

1. Добавьте ссылки на метки в свою форму, используя следующий код.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet5":::

     > [!IMPORTANT]
     > Используйте элемент управления языка программирования в правом верхнем углу этой страницы, чтобы просмотреть фрагмент кода на C# или Visual Basic.<br><br>![Элемент управления языка программирования для Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Ссылочные переменные похожи на операторы, которые вы использовали для добавления объектов (таких как объекты <xref:System.Windows.Forms.Timer>, <xref:System.Collections.Generic.List%601> и <xref:System.Random>) в форму. Но эти операторы не приводят к появлению в форме двух дополнительных элементов управления Label, так как в них не используется ключевое слово `new`. Без ключевого слова `new` объект не создается. Именно поэтому `firstClicked` и `secondClicked` называются ссылочными переменными — они просто отслеживают (или ссылаются на) объекты Label.

     Когда переменная не отслеживает объект, ей задается специальное зарезервированное значение — `null` в C# и `Nothing` в Visual Basic. Поэтому при запуске программы переменным `firstClicked`и `secondClicked` задается значение `null` или `Nothing`. Это означает, что переменные ничего не отслеживают.

2. Измените свой обработчик событий <xref:System.Windows.Forms.Control.Click> для использования новой ссылочной переменной `firstClicked`. Удалите последний оператор (`label_Click()`) в методе обработчика событий `clickedLabel.ForeColor = Color.Black;` и замените его последующим оператором `if`. (Не забудьте включить комментарий и весь оператор `if`).

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet6":::

3. Сохраните и выполните программу. Выберите одну из меток и появится ее значок.

4. Выберите следующую метку и обратите внимание, что ничего не происходит. Программа уже отслеживает первую метку, которую выбрал игрок, поэтому `firstClicked` не равно `null` в C# или `Nothing` в Visual Basic. Когда оператор `if` проверяет, имеет ли переменная `firstClicked` значение `null` или `Nothing`, он обнаруживает, что это не так, и не выполняет операторы в блоке `if`. Поэтому только первый выбранный значок становится черным, а другие значки остаются невидимыми, как показано на следующем рисунке.

     ![Игра "Подбери пару!", отображающая один значок](../ide/media/express_tut4step5.png)<br/>
***Игра "Подбери пару!"** ,_ _отображающая один значок*

     Это поведение будет исправлено в следующем шаге руководства путем добавления элемента управления **Таймер**.

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: **[Шаг 6. Добавление таймера](../ide/step-6-add-a-timer.md)** .

- Предыдущий раздел: [Шаг 4. Добавление к каждой метке обработчика событий Click](../ide/step-4-add-a-click-event-handler-to-each-label.md).
