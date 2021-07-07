---
title: Учебник. Создание консольного приложения C# в Visual Studio
titleSuffix: ''
description: Ознакомьтесь с пошаговыми инструкциями по созданию простого консольного приложения "Hello World" на C# в Visual Studio.
ms.custom: vs-acquisition
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: bf7a52b6dbf36c25590292c3272f1e63d07156b9
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387623"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Краткое руководство. Создание консольного приложения на C# в Visual Studio

Изучение этого ознакомительного руководства по возможностям интегрированной среды разработки Visual Studio (IDE) займет 5–10 минут. В его рамках вы создадите простое приложение на C#, выполняющееся в консоли.

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2022"

Установите Visual Studio 2022 бесплатно со страницы [скачиваемых материалов предварительной версии Visual Studio 2022](https://visualstudio.microsoft.com/vs/preview/vs2022), если еще не сделали этого.

::: moniker-end

## <a name="create-a-project"></a>Создание проекта

Сначала вы создадите проект приложения на C#. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

::: moniker range="vs-2017"

1. Откройте Visual Studio 2017.

2. В верхней строке меню последовательно выберите **Файл** > **Создать** > **Проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **C#** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)** . Назовите проект *HelloWorld*.

   ![Шаблон проекта "Консольное приложение (.NET Core)" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Если шаблона проекта **Console App (.NET Core)** (Консольное приложение (.NET Core)) нет, выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**.

   ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

     ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Запустите Visual Studio.

1. На начальном экране выберите **Создать проект**.

   ![Окно "Создание проекта"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. В поле поиска окна **Создание проекта** введите *консоль*. Затем выберите **C#** в списке языков и **Windows** в списке платформ. 

   Применив фильтры языка и платформы, выберите шаблон **Консольное приложение (.NET Core)** и нажмите кнопку **Далее**.

   ![Выбор шаблона C# для консольного приложения (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Если шаблон **Консольное приложение (.NET Core)** отсутствует, его можно установить из окна **Создание проекта**. В сообщении **Не нашли то, что искали?** выберите ссылку **Установка других средств и компонентов**.
   >
   > ![Ссылка "Установка других средств и компонентов" из сообщения "Не нашли то, что искали?" в окне "Создание проекта"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > После этого в Visual Studio Installer выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core**.
   >
   > ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Затем нажмите кнопку **Изменить** в Visual Studio Installer. Вам может быть предложено сохранить результаты работы; в таком случае сделайте это. Выберите **Продолжить**, чтобы установить рабочую нагрузку. После этого вернитесь к шагу 2 в процедуре [Создание проекта](#create-a-project).

1. В поле **Имя проекта** окна **Настроить новый проект** введите *HelloWorld*. Затем нажмите **Создать**.

   ![В окне "Настроить новый проект" назовите проект "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Новый проект открывается в Visual Studio.
   
::: moniker-end

## <a name="create-the-application"></a>Создание приложения

::: moniker range="vs-2017"

Когда вы выберете шаблон проекта на C# и зададите имя проекта, Visual Studio создаст простое приложение "Hello World".

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio включает код по умолчанию "Hello World" в проект.

::: moniker-end

(Для этого Visual Studio вызывает метод <xref:System.Console.WriteLine%2A> для отображения строкового литерала "Hello World!" в окне консоли.)

   ![Просмотр кода "Hello World" по умолчанию на основе шаблона](../ide/media/csharp-console-helloworld-template.png)

Если нажать клавишу **F5**, программа запустится в режиме отладки. Но окно консоли отображается на короткое время, перед тем как закрыться.

(Это происходит потому, что метод `Main` завершается после выполнения его единственного оператора, после чего завершается работа приложения.)

### <a name="add-some-code"></a>Добавление кода

Добавим код для приостановки работы приложения, чтобы окно консоли не закрывалось, пока вы не нажмете клавишу **ВВОД**.

1. Добавьте следующий код сразу после вызова метода <xref:System.Console.WriteLine%2A>:

   ```csharp
   Console.ReadLine();
   ```

1. Убедитесь, что он выглядит в редакторе кода следующим образом:

   ![Добавление кода для приостановки приложения "Hello World"](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Выполнение приложения

1. Нажмите кнопку **HelloWorld** на панели инструментов, чтобы запустить приложение в режиме отладки. (Или нажмите клавишу **F5**.)

   ![Кнопка HelloWorld для запуска программы с панели инструментов](../ide/media/csharp-console-hello-world-button.png)

1. Просмотрите результат в окне консоли.

   ![Текст "Hello World!" в окне консоли](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Закрытие приложения

1. Нажмите клавишу **ВВОД**, чтобы закрыть окно консоли.

1. Закройте область **вывода** в Visual Studio.

   ![Закрытие области вывода в Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Закройте Visual Studio.

## <a name="next-steps"></a>Дальнейшие действия

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали кое-что новое о C# и интегрированной среде разработки Visual Studio. Дополнительные сведения см. по представленной ниже ссылке.

> [!div class="nextstepaction"]
> [Начало работы с консольным приложением на C# в Visual Studio](../get-started/csharp/tutorial-console.md)
