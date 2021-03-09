---
title: Создание приложения ASP.NET Core с помощью TypeScript
description: В этом руководстве создается приложение с помощью ASP.NET Core и TypeScript
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 411fbd757eb063202136eba5c1e5fbec27f56523
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683642"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Учебник. Создание приложения ASP.NET Core с помощью TypeScript в Visual Studio

В этом учебнике по ASP.NET Core разработки Visual Studio и TypeScript вы создадите простое веб-приложение, добавите код TypeScript, а затем запустите приложение.

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

::: moniker-end

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
> * Создать проект ASP.NET Core.
> * Добавить пакет NuGet для поддержки TypeScript.
> * Добавить код TypeScript.
> * Запуск приложения
> * Добавление сторонней библиотеки с помощью npm

## <a name="prerequisites"></a>Предварительные требования

* У вас должны быть установлены решение Visual Studio и рабочая нагрузка ASP.NET для разработки веб-приложений.

    ::: moniker range=">=vs-2019"
    Установите Visual Studio 2019 бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/), если еще не сделали этого.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Установите Visual Studio 2017 бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/), если еще не сделали этого.
    ::: moniker-end

    Если вам нужно установить рабочую нагрузку, но вы уже используете Visual Studio, выберите пункт **Средства** > **Получить средства и компоненты...** , после чего запустится Visual Studio Installer. Выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**, а затем щелкните **Изменить**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Создание проекта ASP.NET Core MVC

Visual Studio управляет файлами для отдельного приложения в *проекте*. Проект включает исходный код, ресурсы и файлы конфигурации.

>[!NOTE]
> Сведения о том, как начать работу с пустого проекта ASP.NET Core и добавить интерфейсную часть TypeScript, см. в статье [ASP.NET Core с TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

В этом учебнике вы начнете работу с простого проекта, содержащего код для приложения ASP.NET Core MVC.

1. Запустите Visual Studio.

1. Создайте новый проект.

    ::: moniker range=">=vs-2019"
    На начальном экране Visual Studio 2019 выберите **Создать проект**. Если окно запуска не открыто, выберите **Файл** > **Окно запуска**. Введите запрос **веб-приложение**, укажите **C#** в качестве языка, выберите **ASP.NET Core Web Application (Model-View-Controller)** (Веб-приложение ASP.NET Core (модель — представление — контроллер)) и нажмите кнопку **Далее**. На следующем экране присвойте проекту имя и нажмите кнопку **Далее**.

    Выберите рекомендуемую версию целевой платформы (.NET Core 3.1) или .NET 5 и щелкните **Создать**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    В верхней строке меню последовательно выберите **Файл**  > **Создать**  > **Проект**. В левой панели диалогового окна **Новый проект** разверните узел **Visual C#** и выберите **.NET Core**. В средней области выберите **ASP.NET Core Web Application — C#** (Веб-приложение ASP.NET Core — C#) и нажмите кнопку **ОК**.

    В открывшемся диалоговом окне выберите **Веб-приложение (модель-представление-контроллер)** , а затем нажмите кнопку **Создать** (или **ОК**).

    ![Выбор шаблона MVC](../javascript/media/aspnet-core-ts-mvc-template.png)
    ::: moniker-end
    Если шаблон проекта **Веб-приложение ASP.NET Core** отсутствует, его можно получить, добавив рабочую нагрузку **ASP.NET и разработка веб-приложений**. Подробные инструкции см. в разделе [с предварительными требованиями](#prerequisites).

    Visual Studio создаст решение и откроет проект в правой области.

## <a name="add-some-code"></a>Добавление кода

1. Выбор в обозревателе решений Щелкните правой кнопкой узел проекта и выберите **Управление пакетами NuGet**. На вкладке **Обзор** найдите **Microsoft.TypeScript.MSBuild**, а затем нажмите кнопку **Установить** справа, чтобы установить пакет.

   ![Добавление пакета NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio добавляет пакет NuGet в раздел **Зависимости** узла в обозревателе решений.

1. Щелкните правой кнопкой мыши узел проекта и выберите **Добавить > Новый элемент**. Выберите **Файл конфигурации TypeScript JSON**, а затем нажмите кнопку **Добавить**.

   Visual Studio добавит файл *tsconfig.json* в корневую папку проекта. Этот файл можно использовать для [настройки параметров](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) компилятора TypeScript.

1. Откройте *tsconfig.json* и замените код по умолчанию следующим кодом.

   ```json
   {
     "compileOnSave": true,
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   Параметр *outDir* указывает выходную папку для обычных файлов JavaScript, которые преобразуются компилятором TypeScript.

   Эта конфигурация содержит основные сведения об использовании TypeScript. В других сценариях, например при использовании [gulp или веб-пакета](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), вместо пути *wwwroot/js* может потребоваться другое промежуточное расположение для преобразованных файлов JavaScript в зависимости от средств и настроек конфигурации.

1. В обозревателе решений щелкните правой кнопкой мыши узел проекта и выберите **Добавить > Новая папка**. Для новой папки используйте имя *scripts*.

1. Щелкните правой кнопкой мыши папку *scripts* и выберите **Добавить > Новый элемент**. Выберите **Файл TypeScript**, введите *app.ts* в качестве имени файла, а затем нажмите кнопку **Добавить**.

   Visual Studio добавляет файл *app.ts* в папку *scripts*.

1. Откройте файл *app.ts* и добавьте следующий код TypeScript.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio обеспечивает поддержку IntelliSense для кода TypeScript.

    Чтобы проверить это, удалите `.lastName` из функции `greeter`, а затем повторно введите ".", и вы увидите IntelliSense.

    ![Просмотр IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Выберите `lastName`, чтобы добавить последнее имя обратно в код.

1. Откройте папку *Views/Home*, а затем файл *Index.cshtml*.

1. Добавьте следующий HTML-код в конец файла.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Откройте папку *Views/Shared*, а затем файл *_Layout.cshtml*.

1. Добавьте следующую ссылку на скрипт перед вызовом `@RenderSection("Scripts", required: false)`:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Построение приложения

1. Выберите **Сборка > Собрать решение**.

   Хотя приложение автоматически собирается при запуске, рассмотрим, что происходит во время процесса сборки.

1. Откройте папку *wwwroot/js* и найдите два новых файла: *app.js* и файл сопоставителя с исходным кодом *app.js.map*. Эти файлы создаются компилятором TypeScript.

   Файлы сопоставителя с исходным кодом необходимы для отладки.

## <a name="run-the-application"></a>Запуск приложения

1. Чтобы запустить приложение, нажмите клавишу **F5** (**Отладка** > **Начать отладку**).

    Приложение откроется в браузере.

    В окне браузера вы увидите заголовок **Добро пожаловать** и кнопку **Щелкните здесь**.

    ![ASP.NET Core с TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Нажмите кнопку, чтобы отобразить сообщение, указанное в файле TypeScript.

## <a name="debug-the-application"></a>Отладка приложения

1. Установите точку останова в функции `greeter` в `app.ts`, щелкнув левое поле в редакторе кода.

    ![Установка точки останова](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Нажмите клавишу **F5** для запуска приложения.

   Возможно, потребуется ответить на сообщение, чтобы включить отладку скрипта.

   Приложение останавливается в точке останова. Теперь вы можете проверять переменные и использовать функции отладчика.

## <a name="add-typescript-support-for-a-third-party-library"></a>Добавление поддержки TypeScript для сторонней библиотеки

1. Следуйте инструкциям в разделе по [управлению пакетом npm](../javascript/npm-package-management.md#aspnet-core-projects), чтобы добавить файл `package.json` в проект. В результате в проект будет добавлена поддержка npm.

   >[!NOTE]
   > Для установки клиентских файлов JavaScript и CSS в проектах ASP.NET Core вместо npm можно также использовать [диспетчер библиотек](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) или yarn.

1. В этом примере в проект добавляется файл определения TypeScript для jQuery. Включите в файл *package.json* следующий код.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   В результате будет добавлена поддержка TypeScript для jQuery. Сама библиотека jQuery уже включена в шаблон проекта MVC (находится в папке wwwroot/lib в обозревателе решений). Если вы используете другой шаблон, может потребоваться также включить пакет jquery npm.

1. Если пакет в обозревателе решений не установлен, щелкните правой кнопкой мыши узел npm и выберите пункт **Восстановить пакеты**.

   >[!NOTE]
   > В некоторых сценариях в обозревателе решений может быть указано, что пакет npm не синхронизирован с файлом *package.json* из-за известной проблемы, описанной [здесь](https://github.com/aspnet/Tooling/issues/479). Например, при установке пакет может отображаться как неустановленный. В большинстве случаев обозреватель решений можно обновить, удалив файл *package.json*, перезапустив Visual Studio и повторно добавив файл *package.json*, как описано выше в этой статье.

1. В обозревателе решений щелкните папку скриптов правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.

1. Выберите **Файл TypeScript**, введите *library.ts* и щелкните **Добавить**.

1. Добавьте в файл *library.ts* следующий код.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Для простоты этот код отображает сообщение с помощью jQuery и оповещения.

   Добавив определения типов TypeScript для jQuery, вы получаете поддержку IntelliSense для объектов jQuery при вводе "." после объекта jQuery, как показано ниже.

   ![IntelliSense для jQuery](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. В файле _Layout.cshtml обновите ссылки на скрипты так, чтобы они включали `library.js`.

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Добавьте следующий HTML-код в конец файла Index.cshtml.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Чтобы запустить приложение, нажмите клавишу **F5** (**Отладка** > **Начать отладку**).

    Приложение откроется в браузере.

    Нажмите кнопку **ОК** в оповещении, чтобы увидеть обновленную страницу со строкой **Версия jQuery: 3.3.1!** .

    ![Пример jQuery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Следующие шаги

Возможно, вы захотите узнать больше об использовании TypeScript с ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core с TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
