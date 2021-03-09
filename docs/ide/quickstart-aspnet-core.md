---
title: Создание веб-приложения ASP.NET Core на C#
description: Пошаговые инструкции по созданию в Visual Studio приложения Hello World на C# и ASP.NET Core
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 68ccba785643b8f4f29143e5e72dc65cfedcd512
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684067"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Краткое руководство. Создание первого веб-приложения ASP.NET Core с помощью Visual Studio

В этом введении в использование Visual Studio (которое займет от 5 до 10 минут) с помощью шаблона проекта ASP.NET и языка программирования C# будет создано простое веб-приложение "Hello, World".

## <a name="before-you-begin"></a>Перед началом

### <a name="install-visual-studio"></a>Установка Visual Studio

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Выбор темы (необязательно)

В этом кратком руководстве содержатся снимки экрана, использующие темную тему. Если вы не используете темную тему, но хотите переключиться на нее, см. страницу [Персонализация интегрированной среды разработки и редактора Visual Studio](quickstart-personalize-the-ide.md).

## <a name="create-a-project"></a>Создание проекта

Сначала вы создадите проект веб-приложения ASP.NET Core. Для этого типа проекта уже имеются все нужные файлы шаблонов, необходимые для создания веб-приложения, что избавляет вас от лишней работы.

::: moniker range="vs-2017"

1. Откройте Visual Studio 2017.

1. В верхней строке меню последовательно выберите **Файл** > **Создать** > **Проект**.

1. В левой панели диалогового окна **Новый проект** разверните узел **Visual C#** и выберите **.NET Core**. В средней области выберите **Веб-приложение ASP.NET Core**. <br/><br/>Затем назовите файл `HelloWorld` и нажмите кнопку **ОК**.

   ![Создание проекта веб-приложения ASP.NET Core для C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Если категория шаблона проекта **.NET Core** отсутствует, выберите слева ссылку **Открыть Visual Studio Installer**. (В зависимости от параметров отображения может потребоваться выполнить прокрутку.)
   >
   > ![Открыть Visual Studio Installer в диалоговом окне "Новый проект"](../ide/media/open-visual-studio-installer.png)
   >
   > Запускается Visual Studio Installer. Выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**, а затем щелкните **Изменить**.
   >
   > ![Рабочая нагрузка ASP.NET в установщике Visual Studio](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Возможно, перед тем как продолжить установку рабочей нагрузки, придется закрыть Visual Studio.)

1. В верхнем раскрывающемся меню диалогового окна **Создать веб-приложение ASP.NET Core** выберите **ASP.NET Core 2.1**. Затем выберите **Веб-приложение** и нажмите кнопку **ОК**.

   ![Диалоговое окно "Создать веб-приложение ASP.NET Core"](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Если **ASP.NET Core 2.1** не отображается, убедитесь, что вы используете самый последний выпуск Visual Studio. Дополнительные сведения об обновлении установки см. на странице [Обновление до последнего выпуска Visual Studio](../install/update-visual-studio.md).

Через некоторое время файл проекта откроется в Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. На начальном экране выберите **Создать проект**.

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="Просмотр окна &quot;Создание проекта&quot;":::

1. В окне **Создание проекта** выберите **C#** в списке языков. Затем выберите **Windows** в списке платформ и **Веб-сайт** в списке типов проектов.

      Применив фильтры по языку, платформе и типу проекта, выберите шаблон **Веб-приложение ASP.NET Core** и щелкните **Далее**.

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Выбор шаблона C# для веб-приложения ASP.NET Core":::

   > [!NOTE]
   > Если шаблон **Консольное приложение** отсутствует, его можно установить в окне **Создание проекта**. В сообщении **Не нашли то, что искали?** выберите ссылку **Установка других средств и компонентов**.
   >
   > ![Ссылка "Установка других средств и компонентов" из сообщения "Не нашли то, что искали?" в окне "Создание проекта"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > После этого в Visual Studio Installer выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**.
   >
   > ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Затем нажмите кнопку **Изменить** в Visual Studio Installer. Сохраните результаты работы, когда появится такой запрос. Выберите **Продолжить**, чтобы установить рабочую нагрузку. После этого вернитесь к шагу 2 в процедуре [Создание проекта](#create-a-project).

1. В поле **Имя проекта** окна **Настроить новый проект** введите *HelloWorld*. Теперь щелкните **Далее**.

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png" alt-text="В окне &quot;Настроить новый проект&quot; назовите проект &quot;MyCoreApp&quot;":::

1. В окне **Дополнительные сведения** убедитесь, что в раскрывающемся меню вверху указано **.NET Core 3.1**. Обратите внимание, что вы можете включить поддержку Docker, установив флажок. Также вы можете включить поддержку проверки подлинности, нажав кнопку "Изменить способ проверки подлинности". Здесь доступны следующие варианты.
    - Нет: проверка подлинности не используется.
    - Индивидуальные учетные записи: они хранятся в локальной базе данных или базе данных Azure.
    - Платформа удостоверений Майкрософт: в этом варианте для проверки подлинности используется Active Directory, Azure AD или Microsoft 365.
    - Windows: подходит для приложений интрасети.
    
    Не устанавливайте флажок **Включить Docker** и установите флажок **Нет** в разделе "Тип проверки подлинности". Затем выберите **Создать**.

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="В окне &quot;Дополнительные сведения&quot; убедитесь, что указано .NET Core 3.1, и сохраните все значения по умолчанию":::

   В Visual Studio откроется новый проект.

::: moniker-end

## <a name="create-and-run-the-app"></a>Создание и запуск приложения

::: moniker range="vs-2017"

1. В **обозревателе решений** разверните папку **Страницы** и выберите **About.cshtml**.

   ![Снимок экрана: Обозреватель решений Visual Studio, показывающий файлы в проекте HelloWorld. Папка "Страницы" развернута и выбран параметр About.cshtml.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Этот файл соответствует странице с заголовком **О программе** веб-приложения, которое запускается в веб-браузере.

   ![Страница "О программе" в веб-приложении](../ide/media/csharp-aspnet-about-page.png)

   В редакторе на странице **О программе** появится HTML-код для области дополнительной информации.

   ![Код HTML для области дополнительной информации в редакторе Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Измените текст для чтения "дополнительная информация" на **Hello World!**.

   ![Изменение значения по умолчанию кода HTML для области дополнительной информации в редакторе Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. В **обозревателе решений** разверните **About.cshtml** и выберите **About.cshtml.cs**. (Файл также соответствует странице **О программе** в веб-браузере.)

   ![Снимок экрана: Обозреватель решений Visual Studio, показывающий файлы в проекте HelloWorld. Параметр About.cshtml развернут, и выбран About.cshtml.cs.](../ide/media/csharp-aspnet-about-page-code-file.png)

   В редакторе появится код C#, который содержит текст для области описания приложения на странице **О программе**.

   ![Код C# для области описания приложения в редакторе Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Измените текст сообщения для чтения "описание приложения" на **Мое сообщение**.

   ![Изменение текста сообщения по умолчанию для области описания приложения в редакторе Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Выберите **IIS Express** или нажмите клавиши **CTRL**+**F5**, чтобы запустить приложение и открыть его в веб-браузере.

   ![Нажмите кнопку "IIS Express" в Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Если выводится сообщение об ошибке с текстом **Не удается подключиться к веб-серверу IIS Express** или сообщение об ошибке, где упоминается SSL-сертификат, закройте Visual Studio. После этого откройте Visual Studio с помощью пункта **Запуск от имени администратора** контекстного меню. Затем снова запустите приложение.

1. В веб-браузере убедитесь, что страница **О программе** содержит введенный вами текст.

   ![Обновленная страница About (О программе) с внесенными изменениями](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Закройте веб-браузер.

### <a name="review-your-work"></a>Проверка работы

Просмотрите следующую анимацию для проверки работы, выполненной в предыдущем разделе.

  ![Просмотрите анимированный GIF-файл, демонстрирующий создание и запуск простого веб-приложения ASP.NET Core в Visual Studio на C#](../ide/media/csharp-aspnet-animated-hello-world.gif)

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали что-то новое о C#, ASP.NET Core и интегрированной среде разработки Visual Studio IDE.

::: moniker-end

::: moniker range="vs-2019"

1. В **обозревателе решений** разверните папку **Страницы** и выберите **Index.cshtml**.

   ![Выбор файла Index.cshtml из обозревателя решений](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Этот файл соответствует странице с заголовком **Home** (Домашняя) веб-приложения, которое запускается в веб-браузере.

   ![Страница "О программе" в веб-приложении](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   В редакторе отображается HTML-код для текста, содержащегося на странице **Home** (Домашняя).

   ![HTML-код из файла Index.cshtml для домашней страницы в редакторе Visual Studio](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Измените текст "Welcome" на "**Hello World!**".

   ![В редакторе Visual Studio измените сообщение "Welcome" в HTML-коде по умолчанию на сообщение "Hello World"](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Выберите **IIS Express** или нажмите клавиши **CTRL**+**F5**, чтобы запустить приложение и открыть его в веб-браузере.

   ![Нажмите кнопку "IIS Express" в Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Если выводится сообщение об ошибке с текстом **Не удается подключиться к веб-серверу IIS Express** или сообщение об ошибке, где упоминается SSL-сертификат, закройте Visual Studio. После этого откройте Visual Studio с помощью пункта **Запуск от имени администратора** контекстного меню. Затем снова запустите приложение.

1. В веб-браузере убедитесь, что страница **Home** (Домашняя) содержит введенный вами текст.

   ![Обновленная страница "Home" (Домашняя) с внесенными изменениями](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Закройте веб-браузер.

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

Для получения дополнительных сведений перейдите к следующему руководству:

> [!div class="nextstepaction"]
> [Начало работы с C# и ASP.NET в Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>См. также раздел

[Публикация веб-приложения в службе приложений Azure с помощью Visual Studio](../deployment/quickstart-deploy-to-azure.md)
