---
title: Учебник. Начало работы с Visual Basic
description: Ознакомьтесь с пошаговыми инструкциями по созданию простого консольного приложения на Visual Basic в Visual Studio.
ms.custom: seodec18, get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 70782687b6220adf1c61c5b2bb6487d68fde70f4
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101682619"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Руководство. Начало работы с Visual Basic в Visual Studio

В этом руководстве по Visual Basic вы будете работать со средой Visual Studio для создания и запуска нескольких разных консольных приложений. Вы также ознакомитесь с некоторыми возможностями [интегрированной среды разработки (IDE) Visual Studio](visual-studio-ide.md).

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

::: moniker-end

## <a name="create-a-project"></a>Создание проекта

Сначала мы создадим проект приложения Visual Basic. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

::: moniker range="vs-2017"

1. Откройте Visual Studio 2017.

2. В верхней строке меню последовательно выберите **Файл** > **Создать** > **Проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)** . Назовите проект *WhatIsYourName*.

   ![Шаблон проекта "Консольное приложение (.NET Core)" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Добавление рабочей нагрузки (необязательно)

Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, его можно получить, добавив рабочую нагрузку **Кроссплатформенная разработка .NET Core**. Добавить ее можно одним из двух способов в зависимости от того, какие обновления Visual Studio 2017 установлены на вашем компьютере.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Вариант 1: использование диалогового окна "Новый проект"

1. Щелкните ссылку **Открыть установщик Visual Studio** в левой области диалогового окна **Новый проект**.

   ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../media/vs-open-visual-studio-installer-generic.png)

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

   ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Вариант 2: использование меню "Сервис"

1. Закройте диалоговое окно **Создать проект** и в верхней строке меню выберите **Сервис** > **Получить средства и компоненты**.

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> На некоторых снимках экрана в этом учебнике используется темная тема. Если вы не используете темную тему, но хотите переключиться на нее, см. страницу [Персонализация интегрированной среды разработки и редактора Visual Studio](../../ide/quickstart-personalize-the-ide.md).

1. Запустите Visual Studio 2019.

1. На начальном экране выберите **Создать проект**.

   ![Просмотр окна "Создание проекта"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. В окне **Создание проекта** выберите **Visual Basic** в списке языков. Затем выберите **Windows** в списке платформ и **Консоль** в списке типов проектов.

   Применив фильтры по языку, платформе и типу проекта, выберите шаблон **Консольное приложение** и щелкните **Далее**.

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Выбор шаблона Visual Basic для консольного приложения":::

   > [!NOTE]
   > Если шаблон **Консольное приложение** отсутствует, его можно установить в окне **Создание проекта**. В сообщении **Не нашли то, что искали?** выберите ссылку **Установка других средств и компонентов**.
   >
   > ![Ссылка "Установка других средств и компонентов" из сообщения "Не нашли то, что искали?" в окне "Создание проекта"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > После этого в Visual Studio Installer выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core**.
   >
   > ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Затем нажмите кнопку **Изменить** в Visual Studio Installer. Вам может быть предложено сохранить результаты работы; в таком случае сделайте это. Выберите **Продолжить**, чтобы установить рабочую нагрузку. После этого вернитесь к шагу 2 в процедуре [Создание проекта](#create-a-project).

1. В поле **Имя проекта** окна **Настроить новый проект** введите *WhatIsYourName*. Затем щелкните **Далее**.

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="В окне &quot;Настроить новый проект&quot; назовите проект &quot;WhatIsYourName&quot;":::

1. В окне **Дополнительные сведения** для целевой платформы должна быть указана версия **.NET Core 3.1**. Если это не так, выберите **.NET Core 3.1**. Затем нажмите **Создать**.

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="Проверка того, что в окне &quot;Дополнительные сведения&quot; указано .NET Core 3.1":::

   Новый проект открывается в Visual Studio.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Создание приложения для запроса имени

Давайте создадим приложение, которое запрашивает имя пользователя, а затем выводит его вместе с датой и временем. Вот как это сделать.

 ::: moniker range="vs-2017"

1. Откройте проект *WhatIsYourName*, если он еще не открыт.

1. Введите следующий код Visual Basic между первой открывающей скобкой после строки `Sub Main(args As String())` и строкой `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Этот код заменяет существующие операторы <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> и <xref:System.Console.ReadKey%2A>.

   ![Окно кода с кодом приложения](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Нажмите зеленую **кнопку Пуск** или клавишу **F5**, чтобы создать и запустить свое первое приложение.

1. Когда откроется окно консоли, введите свое имя. Окно консоли должно выглядеть так, как показано на следующем снимке экрана:

   ![Окно консоли с вопросом "What Is Your Name" (Как вас зовут), временем и датой, а также сообщением "Press any key to continue" (Чтобы продолжить, нажмите любую клавишу)](media/vb-console-what-name.png)

1. Для закрытия консольного окна нажмите любую клавишу.

::: moniker-end

::: moniker range="vs-2019"

1. В проекте *WhatIsYourName* введите следующий код Visual Basic между первой открывающей скобкой после строки `Sub Main(args As String())` и строкой `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Этот код заменяет существующие операторы <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> и <xref:System.Console.ReadKey%2A>.

   ![Окно кода с кодом приложения](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Нажмите зеленую **кнопку Пуск** или клавишу **F5**, чтобы создать и запустить свое первое приложение.

1. Когда откроется окно консоли, введите свое имя. Окно консоли должно выглядеть так, как показано на следующем снимке экрана:

   ![Окно консоли с вопросом "What Is Your Name" (Как вас зовут), временем и датой, а также сообщением "Press any key to continue" (Чтобы продолжить, нажмите любую клавишу)](media/vb-console-what-name.png)

1. Для закрытия консольного окна нажмите любую клавишу.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Создание приложения "Калькулятор"

::: moniker range="vs-2017"

1. Откройте Visual Studio 2017 и в верхней строке меню выберите **Файл** > **Создать** > **Проект**.

1. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)** . Назовите файл *CalculateThis*.

1. Введите следующий код между строками `Module Program` и `End Module`:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Окно кода должно выглядеть так, как показано на следующем снимке экрана:

   ![Окно кода с кодом приложения "CalculateThis"](media/vb-codewindow-calculate-this.png)

1. Щелкните **CalculateThis**, чтобы запустить программу. Окно консоли должно выглядеть так, как показано на следующем снимке экрана:

    ![Окно консоли с приложением CalculateThis, включая запросы на выполнение действий.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. На начальном экране выберите **Создать проект**. 

1. В окне **Создание проекта** выберите **Visual Basic** в списке языков. Затем выберите **Windows** в списке платформ и **Консоль** в списке типов проектов.

1. Применив фильтры по языку, платформе и типу проекта, выберите шаблон **Консольное приложение** и щелкните **Далее**.

   Затем в поле **Имя проекта** окна **Настроить новый проект** введите *CalculateThis*. Затем щелкните **Далее**.

1. В окне **Дополнительные сведения** для целевой платформы должна быть указана версия **.NET Core 3.1**. Если это не так, выберите **.NET Core 3.1**. Затем нажмите **Создать**.

1. Введите следующий код между строками `Module Program` и `End Module`:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Окно кода должно выглядеть так, как показано на следующем снимке экрана:

   ![Окно кода с кодом приложения "CalculateThis"](media/vb-codewindow-calculate-this.png)

1. Щелкните **CalculateThis**, чтобы запустить программу. Окно консоли должно выглядеть так, как показано на следующем снимке экрана:

    ![Окно консоли с приложением CalculateThis, включая запросы на выполнение действий.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Быстрые ответы на часто задаваемые вопросы

Ниже приведен краткий список вопросов и ответов, с помощью которого вы сможете ознакомиться с некоторыми основными понятиями.

### <a name="what-is-visual-basic"></a>Что такое Visual Basic?

Visual Basic — это типобезопасный язык программирования, который прост в изучении. Он является производным от языка BASIC (Beginner's All-purpose Symbolic Instruction Code — универсальный код символических инструкций для начинающих).

### <a name="what-is-visual-studio"></a>Что такое Visual Studio?

Visual Studio — это интегрированный набор средств разработки. Его можно рассматривать как программу для создания приложений.

### <a name="what-is-a-console-app"></a>Что такое консольное приложение?

Консольное приложение принимает входные данные и выводит результаты в окне командной строки (также называется консоль).

### <a name="what-is-net-core"></a>Что такое .NET Core?

.NET Core — это дальнейший этап развития платформы .NET Framework. В то время как платформа .NET Framework позволяла использовать один и тот же код в средах разных языков программирования, в .NET Core появилась возможность использовать один и тот же код на разных платформах. Более того, это платформа с открытым кодом. (Как .NET Framework, так и .NET Core включают в себя готовые библиотеки, предоставляющие определенные функциональные возможности, а также среду CLR, которая выступает в роли виртуальной машины для выполнения кода.)

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого учебника! Для получения дополнительных сведений перейдите к следующему руководству.

> [!div class="nextstepaction"]
> [Создание библиотеки .NET Standard с помощью Visual Basic и пакета SDK для .NET Core в Visual Studio 2017](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>См. также раздел

* [Пошаговые руководства по Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Справочник по языку Visual Basic](/dotnet/visual-basic/language-reference/index)
* [IntelliSense для файлов кода Visual Basic](../../ide/visual-basic-specific-intellisense.md)
