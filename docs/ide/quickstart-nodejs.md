---
title: Создание первого приложения Node.js
ms.custom:
- vs-acquisition
- SEO-VS-2020
description: В этом кратком руководстве вы создадите приложение Node.js в Visual Studio.
ms.date: 03/25/2021
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0c44bfcfe1e7f07f83ca2b7dbb8b0604f5efe5f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386167"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Краткое руководство. Создание первого приложения Node.js в Visual Studio

В рамках этого краткого (на 5–10 минут) знакомства с возможностями интегрированной среды разработки (IDE) Visual Studio вы создадите простое веб-приложение Node.js.

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, установите Visual Studio и настройте среду Node.js.

### <a name="install-visual-studio"></a>Установка Visual Studio

::: moniker range=">=vs-2019"
Установите Visual Studio 2019 бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.
::: moniker-end
::: moniker range="vs-2017"
Установите Visual Studio 2017 бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>Настройка среды Node.js

Visual Studio может помочь в настройке среды, включая установку средств, общих с разработкой Node.js.

1. В Visual Studio выберите **Средства** > **Получить средства и компоненты**.

1. в Visual Studio Installer выберите рабочую нагрузку **Разработка Node.js** и щелкните **Изменить**, чтобы скачать и установить рабочую нагрузку.

    ![Рабочая нагрузка Node.js в Visual Studio Installer](../ide/media/quickstart-nodejs-workload.png)

1. Установите версию LTS [среды выполнения Node.js](https://nodejs.org/en/download/). Мы рекомендуем использовать версию LTS для обеспечения лучшей совместимости с внешними платформами и библиотеками.

    Несмотря на то, что Node.js создана для 32-разрядных и 64-разрядных архитектур, установщик Node.js поддерживает только одну установленную версию в каждый конкретный момент.

1. Если Visual Studio не обнаруживает установленную среду выполнения (обычно это не так), настройте проект так, чтобы он ссылался на установленную среду выполнения.

   1. После [создания проекта](#create-your-app-project) щелкните правой кнопкой мыши узел проекта.

   1. Выберите **Свойства** и задайте **путь к Node.exe**. В каждом из проектов Node.js можно использовать глобальную установку Node.js или указать путь к локальному интерпретатору.

## <a name="create-your-app-project"></a>Создание проекта приложения

1. Если вы еще не сделали это, установите версию LTS [среды выполнения Node.js](https://nodejs.org/en/download/). Дополнительные сведения см. в разделе [Необходимые условия](#prerequisites).

1. Запустите Visual Studio.

1. Создайте новый проект.

    ::: moniker range=">=vs-2019"

    1. Нажмите клавишу **ESC**, чтобы закрыть окно запуска.

    1. Нажмите клавиши **CTRL + Q**, чтобы открыть поле поиска и введите **Node.js**.

    1. Выберите **Пустое веб-приложение Node.js (JavaScript)** . В диалоговом окне выберите **Создать**.

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. В верхней строке меню последовательно выберите **Файл** > **Создать** > **Проект**.

    1. В левой области диалогового окна **Новый проект** разверните узел **JavaScript** и выберите **Node.js**.

    1. В средней области выберите **Пустое веб-приложение Node.js** и нажмите кнопку **ОК**.

    ::: moniker-end
    
    Если шаблон проекта **Пустое веб-приложение Node.js** отсутствует, необходимо добавить рабочую нагрузку **Разработка Node.js**. Подробные инструкции см. в разделе [с предварительными требованиями](#prerequisites).

    Visual Studio создаст и откроет проект. Файл *server.js* проекта откроется в редакторе слева.

## <a name="explore-the-ide"></a>Изучение интегрированной среды разработки

1. Посмотрите на **Обозреватель решений** в правой области.

   ![Обозреватель решений](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Ваш проект выделен жирным шрифтом, с именем, указанным при настройке проекта. На диске этот проект представлен файлом *NJSPROJ* в папке проекта.

   - На верхнем уровне находится решение, имя которого по умолчанию совпадает с именем проекта. Решение, представленное на диске файлом *SLN*, является контейнером для одного или нескольких связанных проектов.

   - В узле **npm** представлены установленные пакеты npm. Вы можете щелкнуть узел npm правой кнопкой мыши, чтобы найти и установить пакеты npm с помощью диалогового окна.

1. Чтобы установить пакеты npm или команды Node.js из командной строки, щелкните узел проекта правой кнопкой мыши и выберите пункт **Открыть командную строку здесь**.

   ![Командная строка dot j s](../ide/media/quickstart-nodejs-command-prompt.png)

1. Если вы хотите протестировать навигацию к исходному коду, выберите **http.createServer** в открытом файле *server.js* и нажмите клавишу **F12** или выберите команду **Перейти к определению** в контекстном (открываемом по щелчку правой кнопки мыши) меню. Эта команда выполняет переход к определению функции `createServer` в *http.d.ts*.

   ![Контекстное меню "Перейти к определению"](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Вернитесь к *server.js* и найдите следующую строку кода: `res.end('Hello World\n');`. Измените этот код следующим образом:

    `res.end('Hello World\n' + res.connection.`

    При вводе **connection.** технология IntelliSense предлагает варианты автозавершения.

   ![Автозавершение IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Выберите **localPort** и тип **);** для завершения инструкции:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>Запуск приложения

1. Чтобы запустить приложение, нажмите клавиши **CTRL+F5** (или последовательно выберите **Отладка** > **Запуск без отладки**). 
 
   Приложение откроется в браузере.

1. Убедитесь, что в браузере отображаются сообщение "Hello World" и номер локального порта.

Поздравляем! Вы создали простое приложение Node.js с помощью Visual Studio. Дальше можно двигаться, обратившись к разделу **Учебники**.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Развертывание приложения в службе приложений Linux](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Руководство по Node.js и выпуску Express](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Руководство по Node.js и React](../javascript/tutorial-nodejs-with-react-and-jsx.md)
