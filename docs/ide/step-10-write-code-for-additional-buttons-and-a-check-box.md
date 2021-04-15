---
title: Написание кода для дополнительных кнопок и флажка
description: Узнайте, как создавать код для дополнительных кнопок и флажка, в учебнике по созданию средств просмотра рисунков.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 095c402b54e32dbd0839ff89def83d64d1522f4a
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296564"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Шаг 10. Написание кода для дополнительных кнопок и флажка

Теперь можно завершить другие четыре метода. Можно копировать и вставить этот код, но для получения дополнительных навыков введите код и используйте IntelliSense.

Этот код добавляет функциональность к ранее добавленным кнопкам. Без этого кода кнопки ничего не делают. Код используется в событиях <xref:System.Windows.Forms.Control.Click> кнопок (в случае флажка это событие <xref:System.Windows.Forms.CheckBox.CheckedChanged>) для выполнения различных действий при активации пользователем этих элементов управления. Например, событие `clearButton_Click` (или `ClearButton_Click`), которое активируется при нажатии кнопки **Очистить рисунок**, удаляет текущее изображение, присваивая его свойству **Image** значение **null** (или **nothing**). Каждое событие в коде сопровождается комментариями, которые поясняют, что делает код.

> [!TIP]
> Рекомендация — всегда снабжайте код комментариями. Комментарии — это сведения для человека, который читает код, необходимы для того, чтобы сделать код понятным. Содержимое в строке комментария игнорируется приложением. В C# строка комментария начинается с двух символов косой черты (//), а в Visual Basic — с одного знака одинарной кавычки (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Написание кода для дополнительных кнопок и флажка

Добавьте следующий код в файл кода **Form1** (*Form1.cs* или *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs" id="Snippet2":::

  :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb" id="Snippet2":::

> [!NOTE]
> В вашем коде буквы могут не отображаться в "верблюжьем" стиле.

## <a name="next-steps"></a>Дальнейшие действия

* Следующий раздел руководства: **[Шаг 11. Запуск приложения и изучение других функций](../ide/step-11-run-your-program-and-try-other-features.md)** .

* Предыдущий раздел: [Шаг 9. Проверка, комментирование и тестирование кода](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>См. также

* [Учебник 2. Создание ограниченной по времени математической головоломки](tutorial-2-create-a-timed-math-quiz.md)
* [Учебник 3. Создание игры "Подбери пару!"](tutorial-3-create-a-matching-game.md)
