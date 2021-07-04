---
title: Язык R и контейнеры Docker
description: Порядок настройки контейнеров Docker для R и подключение к ним с помощью Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3aefba3880443269dbdb1c933e2c12b2f8001469
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2021
ms.locfileid: "111551284"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Использование контейнеров Docker с инструментами R для Visual Studio

Инструменты R для Visual Studio (RTVS) версии 1.3 и более поздних версий при наличии [Docker для Windows](https://www.docker.com/docker-windows) поддерживают работу с контейнерами Docker.

## <a name="create-a-container"></a>Создание контейнера

1. Нажмите кнопку **Контейнеры** в правой части окна **Рабочие области** (**Инструменты R** > **Windows** > **Рабочие области**). Если у вас не установлено решение Docker для Windows, окно сообщит вам об этом и предоставит ссылку для загрузки. Для установки Docker может потребоваться перезагрузка компьютера.

    ![Окно "Рабочие области" в инструментах R для Visual Studio (VS2017) с командой "Контейнеры"](media/container-workspaces-window.png)

1. В окне **Контейнеры** выберите **Создать**:

    ![Команда "Создать" в окне "Контейнеры"](media/containers-window-create.png)

1. Заполните в диалоговом окне нужные сведения и выберите **Создать**. Введенные учетные данные также используются для создания учетной записи Linux, с которой вы позже будете входить в систему.

    ![Указание имени контейнера и учетных данных при создании контейнера](media/containers-window-create-fill.png)

1. Сборка образа в RTVS может занять некоторое время. Окно **Вывод** в Visual Studio отображает ход выполнения, но при длительной загрузке образов оно может практически не меняться, и вам нужно будет подождать. После сборки образа RTVS запускает контейнер, который отображается в окне **Контейнер**. Элементы управления справа останавливают, удаляют или перезапускают контейнер.

    ![Окно "Контейнеры" с созданным контейнером](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Подключение к контейнеру

1. Раздел **Локальные работающие контейнеры** окна **Рабочие области** показывает контейнеры с запущенной управляющей программой RTVS на порте 5444. (Сведения о настройке управляющей программы см. в разделе [Удаленная служба R для Linux](setting-up-remote-r-service-on-linux.md).)

    ![Окно "Рабочие области" с доступными контейнерами](media/workspaces-window-running-containers.png)

1. Чтобы подключиться к контейнеру, дважды щелкните его имя или нажмите справа от него кнопку со стрелкой вперед. После подключения вы увидите **Интерактивное окно R** (см. раздел [Работа с интерактивным окном R](interactive-repl-for-r-in-visual-studio.md)):

    ![Окно "Рабочие области" и окно REPL, открытые для контейнера](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Использование пользовательских образов

RTVS поддерживает обнаружение и управление для контейнеров, созданных с помощью пользовательских образов, например образа microsoft/rtvs, описываемого в файле Docker ниже. Используемый здесь базовый образ содержит предустановленные rtvs-daemon, R 3.4.2 и общие пакеты R. **Примечание**. Измените показанные здесь имя пользователя и пароль.

```docker
FROM mcr.microsoft.com/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Используйте для сборки образа следующую команду, изменив по своему выбору имя контейнера (аргумент `--name`):

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

Аргумент `-p 6056:5444` сопоставляет порт 6056 с внутренним портом 5444, используемым RTVS для обнаружения rtvs-daemon. Все контейнеры, предоставляющие порт контейнера 5444, перечислены в окне **Рабочие области**. Затем вы можете подключиться к контейнеру в окне **Рабочие области**, используя `<<unix>>\ruser1` в качестве имени пользователя и "foobar" в качестве пароля, если вы не указали другие учетные данные в файле Docker.
