---
title: Отладка приложений в локальном контейнере Docker | Документация Майкрософт
description: Узнайте, как вносить изменения в приложение, выполняемое в локальном контейнере Docker, обновлять контейнер с помощью функций правки и обновления, а также устанавливать точки останова.
ms.author: ghogen
author: ghogen
manager: jmartens
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 8fb821acb48dd05aa09723fe5c6c254e7d1ca648
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306388"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Отладка приложений в локальном контейнере Docker

Visual Studio обеспечивает согласованную разработку контейнеров Docker и локальную проверку приложения.
Вы можете запускать и отлаживать свои приложения в контейнерах Linux или Windows, работающих на локальном рабочем столе Windows с установленным Docker. При этом вам не нужно перезапускать контейнер каждый раз, когда вы вносите изменения в код.

В этой статье рассказывается, как запускать приложение в локальном контейнере Docker с помощью Visual Studio, вносить изменения и обновлять браузер для их отображения. В ней также показано, как устанавливать точки останова для отладки контейнерных приложений. Поддерживаемые типы проектов включают в себя консольные и веб-приложения .NET Framework и .NET Core. В этой статье используются веб-приложения ASP.NET Core и консольные приложения .NET Framework.

Если у вас уже есть проект поддерживаемого типа, Visual Studio может создать Dockerfile и настроить проект для запуска в контейнере. Ознакомьтесь со статьей [Средства для контейнеров в Visual Studio](overview.md).

## <a name="prerequisites"></a>Предварительные требования

Для отладки приложений в локальном контейнере Docker необходимо установить следующие средства:

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) с установленной рабочей нагрузкой "Веб-разработка";

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с установленной рабочей нагрузкой "Веб-разработка".

::: moniker-end

::: moniker range="vs-2022"

* [Предварительная версия Visual Studio 2022]() с установленной рабочей нагрузкой "Веб-разработка".

::: moniker-end

Для запуска контейнеров Docker локально требуется локальный клиент Docker. Можно воспользоваться приложением [Docker для Windows](https://www.docker.com/get-docker), для которой требуются Hyper-V и Windows 10.

Контейнеры Docker доступны для проектов .NET Framework и .NET Core. Рассмотрим два примера. Сначала мы рассмотрим веб-приложение .NET Core. Затем мы рассмотрим консольное приложение .NET Framework.

## <a name="create-a-web-app"></a>Создание веб-приложения

Пропустите этот раздел, если у вас есть проект и вы добавили поддержку Docker, как описано в [обзоре](overview.md).

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Изменение и обновление кода

Для быстрой итерации изменений можно запустить приложение в контейнере. Затем продолжайте вносить изменения, просматривая их так же, как в IIS Express.

1. Убедитесь, что Docker настроен для применения типа контейнера (Linux или Windows), который вы используете. На панели задач щелкните правой кнопкой мыши значок Docker и выберите пункт **Switch to Linux containers** (Переключиться на контейнеры Linux) или **Switch to Windows containers** (Переключиться на контейнеры Windows) в зависимости от ситуации.

1. (Только для .NET Core 3 и более поздних версий) Изменение кода и обновление работающего сайта, как описано в этом разделе, не включены в шаблоны по умолчанию в .NET Core 3.0 и более поздних версий. Чтобы включить их, установить пакет NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). В *Startup.cs* добавьте вызов метода расширения `IMvcBuilder.AddRazorRuntimeCompilation` в код в методе `ConfigureServices`. Этот параметр должен быть включен только в режиме отладки, поэтому код должен выглядеть следующим образом:

    ```csharp
    public IWebHostEnvironment Env { get; set; }

    public void ConfigureServices(IServiceCollection services)
    {
        IMvcBuilder builder = services.AddRazorPages();

    #if DEBUG
        if (Env.IsDevelopment())
        {
            builder.AddRazorRuntimeCompilation();
        }
    #endif

        // code omitted for brevity
    }
    ```

    Измените метод `Startup` следующим образом.

    ```csharp
    public Startup(IConfiguration configuration, IWebHostEnvironment webHostEnvironment)
    {
        Configuration = configuration;
        Env = webHostEnvironment;
    }
    ```

   Дополнительные сведения см. в статье [Компиляция файла Razor в ASP.NET Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1&preserve-view=true).

1. В качестве **конфигурации решения** выберите **Отладка**. Затем нажмите клавиши **CTRL**+**F5**, чтобы создать образ Docker и запустить его локально.

    После сборки и запуска образа контейнера в контейнере Docker среда Visual Studio запустит веб-приложение в вашем браузере по умолчанию.

1. Перейдите на страницу *Index* (Индекс). Мы будем вносить на ней изменения.
1. Вернитесь в Visual Studio и откройте файл *Index.cshtml*.
1. Добавьте приведенное ниже содержимое HTML в конец файла и сохраните изменения.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Когда сборка .NET завершится и в окне вывода будут отображаться следующие строки, вернитесь в браузер и обновите страницу:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Изменения применены!

### <a name="debug-with-breakpoints"></a>Отладка с точками останова

Изменения часто требуют дальнейшей проверки. Для этого можно использовать функции отладки Visual Studio.

1. В Visual Studio откройте файл *Index.cshtml.cs*.
2. Замените содержимое метода `OnGet` следующим кодом:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Установите точку останова слева от строки кода.
4. Чтобы начать отладку и достичь точки останова, нажмите клавишу F5.
5. Переключитесь в Visual Studio, чтобы просмотреть точку останова. Проверьте значения.

   ![Снимок экрана: часть кода для Index.cshtml.cs в Visual Studio, для которого точка останова установлена слева от строки кода, выделенной желтым цветом.](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Создание консольного приложения .NET Framework

При использовании проектов консольных приложений .NET Framework возможность добавления поддержки Docker без оркестрации недоступна. Описанную ниже процедуру можно выполнить, даже если вы используете только один проект Docker.

1. Создайте проект консольного приложения .NET Framework.
1. В обозревателе решений щелкните правой кнопкой мыши узел проекта и выберите **Добавить** > **Container Orchestration Support** (Поддержка оркестрации контейнеров).  В появившемся диалоговом окне выберите **Docker Compose**. Файл Dockerfile будет добавлен в проект, а проект Docker Compose со вспомогательными файлами будет добавлен в решение.

### <a name="debug-with-breakpoints"></a>Отладка с точками останова

1. В обозревателе решений откройте файл *Program.cs*.
2. Замените содержимое метода `Main` следующим кодом:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Установите точку останова слева от строки кода.
4. Чтобы начать отладку и достичь точки останова, нажмите клавишу F5.
5. Переключитесь в Visual Studio, чтобы просмотреть точку останова и проверить значения.

   ![Снимок экрана: окно кода для Program.cs в Visual Studio, для которого точка останова установлена слева от строки кода, выделенной желтым цветом.](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Повторное использование контейнеров

Во время цикла разработки среда Visual Studio перестраивает образы контейнеров и сам контейнер только при изменении файла Dockerfile. Если файл Dockerfile не изменяется, Visual Studio повторно использует контейнер из предыдущего запуска.

Если вы вручную изменили контейнер и хотите выполнить перезапуск с чистым образом контейнера, выберите команду **Сборка** > **Очистить**, а затем выполните сборку как обычную.

## <a name="troubleshoot"></a>Устранение неполадок

Узнайте, как [устранять неполадки при разработке Docker в Visual Studio](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения см. в статье [Как Visual Studio создает контейнерные приложения](container-build.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Дополнительные сведения об использовании Docker с Visual Studio, Windows и Azure

* Дополнительные сведения о [разработке контейнеров с помощью Visual Studio](./index.yml).
* Сведения о сборке и развертывании контейнера Docker см. в статье [Интеграция Docker для Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Указатель статей, посвященных Windows Server и Nano Server, см. на странице [Контейнеры в документации Windows](/virtualization/windowscontainers/).
* Ознакомьтесь с общими сведениями о [Службе Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) и [документацией по Службе Azure Kubernetes](/azure/aks).
