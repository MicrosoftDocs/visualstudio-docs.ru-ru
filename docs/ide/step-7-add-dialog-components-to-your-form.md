---
title: Шаг 7. Добавление компонентов диалогового окна в форму
description: Узнайте, как добавить в форму компонент диалогового окна <xref:System.Windows.Forms.OpenFileDialog> и компонент диалогового окна <xref:System.Windows.Forms.ColorDialog>.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 66a6663cfbbcc212f05f75a8bc87bf30a3e4f880
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107297071"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Шаг 7. Добавление компонентов диалогового окна в форму

Чтобы приложение могло открывать графические файлы и изменять цвет фона, в этом шаге следует добавить в форму компоненты <xref:System.Windows.Forms.OpenFileDialog> и <xref:System.Windows.Forms.ColorDialog>.

В некотором смысле компонент похож на элемент управления. Для добавления компонента в форму используется **панель элементов**, его свойства настраиваются в окне **Свойства**. Но в отличие от элемента управления, добавление в форму компонента не добавляет в форму элемент, который может видеть пользователь. Вместо этого, компонент предоставляет определенное поведение, которое можно включать в коде. Это компонент, который открывает диалоговое окно **Открыть файл**.

## <a name="to-add-dialog-components-to-your-form"></a>Добавление компонентов диалогового окна в форму

1. Выберите **конструктор Windows Forms** (**Form1.cs [Design]**) и откройте группу **Диалоговые окна** на **панели элементов**.

    > [!NOTE]
    > Группа **Диалоговые окна** на **панели элементов** содержит компоненты, которые открывают множество полезных диалоговых окон. Эти диалоговые окна можно использовать для открытия и сохранения файлов, просмотра папок, выбора шрифтов и цветов. В этом проекте используется два компонента диалоговых окон — OpenFileDialog и ColorDialog.

1. Чтобы добавить в форму компонент с именем **openFileDialog1**, дважды щелкните элемент **OpenFileDialog**. Чтобы добавить в форму компонент с именем **colorDialog1**, дважды щелкните на **панели элементов** элемент **ColorDialog**. (такой компонент используется в следующем шаге руководства). В нижней части **конструктора Windows Forms** должно быть поле (под формой **программы просмотра изображений**), которое содержит значок для каждого из двух добавленных компонентов диалоговых окон, как показано на рисунке ниже.

     ![Компоненты диалоговых окон](../ide/media/express_dialogsadded.png)<br>***Компоненты** _ _диалоговых окон*

1. Выберите значок **openFileDialog1** в области в нижней части **конструктора Windows Forms**. Установите значения двух свойств.

    - Задайте для свойства **Filter** следующее значение (можно копировать и вставить):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Установите для свойства **Title** значение **Выбор файла изображения**.

         Параметры свойства **Filter** определяют типы файлов, которые отображаются в диалоговом окне **Выбор файла изображения**.

    > [!TIP]
    > Чтобы посмотреть пример диалогового окна **Открыть файл** в другом приложении, откройте программу **Блокнот** или **Paint** и выберите **Файл** > **Открыть**. Обратите внимание на раскрывающийся список рядом с именем файла, в котором можно выбрать тип файла. <br/><br/>Вы только что настроили свойство **Filter** компонента **OpenFileDialog** в приложении. Обратите внимание и на то, как выделены полужирным шрифтом свойства **Title** и **Filter** в окне **Свойства**. Таким образом интегрированная среда разработки показывает свойства, у которых были изменены их значения по умолчанию.

## <a name="next-steps"></a>Дальнейшие действия

* Следующий раздел руководства: **[Шаг 8. Написание кода для обработчика событий кнопки "Показать рисунок"](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)** .

* Предыдущий раздел: [Шаг 6. Присвоение имен элементам управления "Кнопка"](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>См. также

* [Учебник 2. Создание ограниченной по времени математической головоломки](tutorial-2-create-a-timed-math-quiz.md)
* [Учебник 3. Создание игры "Подбери пару!"](tutorial-3-create-a-matching-game.md)
