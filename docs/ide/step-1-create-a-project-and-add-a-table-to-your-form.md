---
title: Шаг 1. Создание проекта и добавление таблицы в форму
description: Узнайте, как создать проект игры "Подбери пару!" и добавить таблицу в форму.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ed4c6b3c65cc7a4c68288c01964388bbf8ec54a0
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306427"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Шаг 1. Создание проекта и добавление таблицы в форму

Первым шагом создания игры "Подбери пару!" является создание проекта и добавление таблицы в форму. Таблица помогает равномерно распределить значки по сетке 4x4. Можно также задать несколько свойств, чтобы улучшить внешний вид игрового поля.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Создание проекта и добавление таблицы в форму

::: moniker range="vs-2017"

1. В строке меню щелкните **Файл** > **Создать** > **Проект**.

1. Выберите **Visual C#** или **Visual Basic** в левой области диалогового окна **Новый проект**, а затем — **Классическое приложение Windows**.

1. В списке шаблонов выберите шаблон **Приложение Windows Forms (.NET Framework)**, назовите его *MatchingGame*, а затем нажмите кнопку **ОК**.

    Появится форма с именем *Form1.cs* или *Form1.vb*, в зависимости от выбранного языка программирования.

   > [!NOTE]
   > Если вы не видите шаблон **Приложение Windows Forms (.NET Framework)**, используйте Visual Studio Installer, чтобы установить рабочую нагрузку **Разработка классических приложений .NET**.<br/><br/>![Рабочая нагрузка разработки классических приложений .NET в Visual Studio Installer](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Дополнительные сведения см. в разделе [Установка Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range=">=vs-2019"

1. На начальном экране выберите **Создать проект**.

   ![Просмотр окна "Создание проекта"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. В поле поиска окна **Создание проекта** введите *Windows Forms*. Затем в списке **Тип проекта** выберите **Рабочий стол**.

   Применив фильтр **Тип проекта**, выберите шаблон **Приложение Windows Forms (.NET Framework)** для C# или Visual Basic и нажмите кнопку **Далее**.

   ![Выбор шаблона Visual Basic или C#для приложения Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Если шаблон **Приложение Windows Forms (.NET Framework)** отсутствует, его можно установить из окна **Создание проекта**. В сообщении **Не нашли то, что искали?** выберите ссылку **Установка других средств и компонентов**.
   >
   > ![Ссылка "Установка других средств и компонентов" из сообщения "Не нашли то, что искали?" в окне "Создание проекта"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > После этого в Visual Studio Installer выберите рабочую нагрузку **Разработка классических приложений .NET**.
   >
   > ![Рабочая нагрузка .NET Core в Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Затем нажмите кнопку **Изменить** в Visual Studio Installer. Вам может быть предложено сохранить результаты работы; в таком случае сделайте это. Выберите **Продолжить**, чтобы установить рабочую нагрузку.

1. В окне **Настроить новый проект** введите *MatchingGame* в поле **Имя проекта**. Затем нажмите **Создать**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Задание свойств формы

1. В окне **Свойства** задайте следующие значения свойств формы.

   1. Измените свойство формы **Text** с **Form1** на **Matching Game**. Этот текст отображается в верхней части окна игры.

   2. Установите размер формы на 550 пикселей в ширину и 550 пикселей в высоту. Для этого установите для свойства **Size** значение **550, 550** или перетащите угол формы, чтобы требуемый размер отобразился в правом нижнем углу интегрированной среды разработки (IDE).

2. Откройте панель элементов, выбрав вкладку **Панель элементов** в левой части интегрированной среды разработки.

3. Перетащите элемент управления <xref:System.Windows.Forms.TableLayoutPanel> из категории **Контейнеры** панели элементов, а затем установите для него следующие свойства.

   1. Задайте для свойства **BackColor** значение **CornflowerBlue**. Для этого откройте диалоговое окно **BackColor**, щелкнув стрелку раскрывающегося списка рядом со свойством **BackColor** в окне **Свойства**.  Затем перейдите на вкладку **Веб** в диалоговом окне **BackColor**, чтобы просмотреть список доступных имен цветов.

      > [!NOTE]
      > Цвета упорядочены не по алфавиту, и цвет **CornflowerBlue** находится в нижней части списка.

   2. Задайте для свойства **Dock** значение **Fill**, нажав кнопку раскрывающегося списка рядом со свойством и щелкнув большую среднюю кнопку. Таблица будет растянута по всей форме.

   3. Для свойства **CellBorderStyle** установите значение **Inset**. Между ячейками поля появятся видимые границы.

   4. Нажмите треугольную кнопку в правом верхнем углу элемента управления TableLayoutPanel для отображения меню задач этой панели.

   5. В меню задач дважды щелкните **Добавить строку** для добавления двух дополнительных строк, а затем дважды щелкните **Добавить столбец** для добавления двух дополнительных столбцов.

   6. В меню задач выберите команду **Изменить строки и столбцы**, чтобы открыть окно **Стили столбцов и строк**. Выберите каждый из столбцов, нажмите кнопку **Процент** и установите ширину каждого столбца равной 25 процентам от общей ширины. Затем в раскрывающемся списке в верхней части окна выберите **Строки** и задайте высоту каждой строки равной 25 процентам. По завершении нажмите кнопку **ОК**.

      Теперь на панели макета таблицы должна быть видна сетка размером 4х4, состоящая из шестнадцати одинаковых по размеру квадратных ячеек. Эти строки и столбцы задают места, в которых позже появятся изображения значков.

4. Убедитесь, что TableLayoutPanel выбран в редакторе формы. На это будет указывать надпись **tableLayoutPanel1** в верхней части окна **Свойства**. Если этот элемент управления не выбран, выберите элемент управления TableLayoutPanel в форме или в раскрывающемся списке в верхней части окна **Свойства**.

    При выбранном элементе управления TableLayoutPanel откройте панель элементов и добавьте элемент управления <xref:System.Windows.Forms.Label> (находится в категории **Стандартные элементы управления**) в левую верхнюю ячейку TableLayoutPanel. Теперь элемент управления Label должен быть выбран в интегрированной среде разработки. Задайте для него следующие свойства.

   1. Убедитесь, что свойство **BackColor** имеет значение **CornflowerBlue**.

   2. Задайте свойству **AutoSize** значение **False**.

   3. Задайте для свойства **Dock** значение **Fill**.

   4. Задайте для свойства **TextAlign** значение **MiddleCenter**, нажав кнопку раскрывающегося списка рядом со свойством, а затем щелкнув среднюю кнопку. Это необходимо, чтобы значок отображался в середине ячейки.

   5. Выберите свойство **Font**. Должна появиться кнопка с многоточием (**…**).

   6. Нажмите кнопку с многоточием и установите для параметра **Font** значение **Webdings**, для параметра **Font Style** — значение **Bold**, а для параметра **Size** — значение **48**.

   7. Установите свойство **Text** равным букве **с**.

        Теперь в левой верхней ячейке TableLayoutPanel должен располагаться черный квадрат на синем фоне, который выравнивается по центру.

       > [!NOTE]
       > Шрифт Webdings является шрифтом значков, который поставляется с операционной системой Windows. В вашей игре "Подбери пару!" игроку необходимо найти пары одинаковых значков, поэтому используйте этот шрифт для отображения значков. Вместо ввода буквы **с** в свойство **Text** попробуйте вводить разные буквы, чтобы увидеть, какие значки отображаются. Восклицательный знак соответствует пауку, прописная буква N — глазу, а запятая — перцу чили.

5. Выберите элемент управления Label и скопируйте его в следующую ячейку TableLayoutPanel. (Нажмите сочетание клавиш **CTRL**+**C** или в строке меню выберите **Правка** > **Копировать**.) Затем вставьте его. (Нажмите сочетание клавиш **CTRL**+**V** или в строке меню выберите **Правка** > **Вставить**.) Во второй ячейке элемента управления TableLayoutPanel появится копия первого элемента управления Label. Вставьте его снова, и в третьей ячейке появится еще один элемент управления Label. Продолжайте вставлять элементы управления Label, пока все ячейки не будут заполнены.

   > [!NOTE]
   > Если выполнить команду вставки слишком много раз, интегрированная среда разработки добавит новую строку в TableLayoutPanel, чтобы появилось место для добавления нового элемента управления Label. Можно выполнить откат. Чтобы удалить новую ячейку, нажмите сочетание клавиш **CTRL**+**Z** или в меню выберите **Правка** > **Отменить**.

    Теперь ваша форма готова. Она будет выглядеть примерно так, как показано на рисунке ниже.

    ![Исходная форма игры на сопоставление](../ide/media/express_tut4step1.png)<br/>*Исходная форма игры "Подбери пару!"*

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел: [Шаг 2. Добавление случайного объекта и списка значков](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Предыдущая статья с общими сведениями: [Руководство 3. Создание игры "Подбери пару!"](../ide/tutorial-3-create-a-matching-game.md).
