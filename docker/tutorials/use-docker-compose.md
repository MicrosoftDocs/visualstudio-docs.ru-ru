---
title: Учебник по Docker. Часть 7. Использование Docker Compose
description: Описывается установка и использование Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 3bcf3a69dcf8053851e3d8519a25f61fe23ae7e3
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082569"
---
# <a name="use-docker-compose"></a>Использование Docker Compose

[Docker Compose](https://docs.docker.com/compose/) — это средство, разработанное для помощи в определении и совместном использовании многоконтейнерных приложений. С помощью средства Compose можно создать файл YAML для определения служб и с помощью одной команды запускать и останавливать все, что нужно.

*Большим* преимуществом использования Compose является то, что можно определить стек приложения в файле, сохранить его в корне репозитория проекта (теперь поддерживается управление версиями) и легко предоставить другому пользователю возможность участвовать в проекте. Другому пользователю достаточно будет только клонировать репозиторий и начать создание приложения. Фактически в GitHub и GitLab можно увидеть достаточно много проектов, использующих эту возможность.

С чего же начать работу?

## <a name="install-docker-compose"></a>Установка Docker Compose

Если вы установили Docker Desktop для Windows или Mac, то у вас уже есть Docker Compose. В экземплярах "Play-with-Docker" уже установлен Docker Compose. Если вы используете компьютер Linux, необходимо установить Docker Compose с помощью [приведенных здесь инструкций](https://docs.docker.com/compose/install/).

После установки вы сможете запустить следующую команду и просмотреть сведения о версии.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Создание файла Compose

1. В корне проекта приложения создайте файл с именем `docker-compose.yml`.

1. Написание файла Compose начнем с определения версии схемы. В большинстве случаев лучше использовать последнюю поддерживаемую версию. Текущие версии схемы и матрицу совместимости см. в [справочнике по файлу Compose](https://docs.docker.com/compose/compose-file/).

    ```yaml
    version: "3.7"
    ```

1. Затем определим список служб (или контейнеров), которые требуется использовать как часть приложения.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Теперь приступим к переносу службы в файл Compose.

## <a name="define-the-app-service"></a>Определение службы приложений

Напомним, что эту команду вы использовали для определения контейнера приложения (замените в Windows PowerShell символы ` \ ` на символы `` ` ``).

```bash
docker run -dp 3000:3000 \
  -w /app -v ${PWD}:/app \
  --network todo-app \
  -e MYSQL_HOST=mysql \
  -e MYSQL_USER=root \
  -e MYSQL_PASSWORD=secret \
  -e MYSQL_DB=todos \
  node:12-alpine \
  sh -c "yarn install && yarn run dev"
```

1. Сначала определите запись службы и образ для контейнера. Для службы можно выбрать любое имя. Имя будет автоматически преобразовано в сетевой псевдоним, что будет полезно при определении службы MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. Как правило, команда будет похожа на определение `image`, хотя для упорядочивания нет требований. Итак, добавьте это в файл.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Перенесите часть команды `-p 3000:3000`, определив параметры `ports` службы. Здесь мы будем использовать [короткий синтаксис](https://docs.docker.com/compose/compose-file/#short-syntax-1), но также доступен более подробный [длинный синтаксис](https://docs.docker.com/compose/compose-file/#long-syntax-1).

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Затем перенесите рабочий каталог (`-w /app`) и сопоставление томов (`-v ${PWD}:/app`) с помощью определений `working_dir` и `volumes`. Для томов также существует [короткий](https://docs.docker.com/compose/compose-file/#short-syntax-3) и [длинный](https://docs.docker.com/compose/compose-file/#long-syntax-3) синтаксис.

   Одним из преимуществ определений томов Docker Compose является использование относительных путей из текущего каталога.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Наконец, перенесите определения переменных среды с помощью ключа `environment`.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>Определение службы MySQL

Теперь пора определить службу MySQL. Для этого контейнера использовалась следующая команда (замените в Windows PowerShell символы ` \ ` на символы `` ` ``).

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Сначала определите новую службу и назовите ее `mysql`, чтобы она автоматически получила сетевой псевдоним. Укажите также используемый образ.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Затем определите сопоставление томов. При запуске контейнера с помощью команды `docker run` именованный том создавался автоматически. Однако это не происходит при запуске через Compose. Необходимо определить том в разделе верхнего уровня `volumes:`, а затем указать точку подключения в конфигурации службы. Если указать только имя тома, будут использоваться параметры по умолчанию. Но есть и [много других доступных параметров](https://github.com/compose-spec/compose-spec/blob/master/spec.md#volumes-top-level-element).

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Наконец, осталось указать переменные среды.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

На этом этапе полный файл `docker-compose.yml` должен выглядеть следующим образом.

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Запуск стека приложений

Теперь, когда у вас есть файл `docker-compose.yml`, его можно запустить.

1. Сначала убедитесь, что никакие другие копии приложения и базы данных не запущены (`docker ps` и `docker rm -f <ids>`).

1. Запустите стек приложений с помощью команды `docker-compose up`. Добавьте флаг `-d`, чтобы выполнить все в фоновом режиме. Либо можно щелкнуть правой кнопкой мыши файл Compose и выбрать параметр **Compose Up** (запустить Compose) на боковой панели VS Code. 

    ```bash
    docker-compose up -d
    ```

    После запуска должны отобразиться примерно следующие выходные данные.

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Вы увидите, что том был создан, так же как и сеть. По умолчанию Docker Compose автоматически создает сеть специально для стека приложений (поэтому мы не определили его в файле Compose).

1. Просмотрите журналы с помощью команды `docker-compose logs -f`. Отобразятся журналы каждой из служб, которые чередуются в одном потоке. Это чрезвычайно полезно, когда необходимо отслеживать проблемы, связанные с временем. Флаг `-f` дает команду "следовать за журналом", поэтому выходные данные будут выдаваться в режиме реального времени по мере их создания.

    Если вы еще этого не сделали, вы увидите следующий результат.

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Имя службы отображается в начале строки (часто в цвете), чтобы облегчить различение сообщений. Если вы хотите просмотреть журналы для определенной службы, можно добавить имя службы в конец команды logs (например, `docker-compose logs -f app`).

    > [!TIP]
    > **Ожидание базы данных перед запуском приложения**. При запуске приложения оно фактически ожидает, пока MySQL будет готов к работе, прежде чем попытаться подключиться к нему. В Docker отсутствует встроенная поддержка, позволяющая ожидать, пока другой контейнер будет полностью готов, запущен и подготовится к запуску другого контейнера. Для проектов на основе узлов можно использовать зависимость [wait-port](https://github.com/dwmkerr/wait-port). Аналогичные проекты существуют для других языков и платформ.

1. На этом этапе вы сможете открыть приложение и увидеть, что оно запускается. И постойте! Вы сделали это с помощью одной команды!

## <a name="see-the-app-stack-in-the-docker-extension"></a>Просмотр стека приложений в расширении Docker

Если взглянуть на расширение Docker, там можно изменить параметры группировки с помощью меню "шестеренки" и пункта "Group By" (группировать). В нашем случае необходимо просмотреть контейнеры, сгруппированные по имени проекта Compose.

![Расширение VS с Compose](media/vs-app-project-collapsed.png)

Если развернуть сеть, вы увидите два контейнера, которые вы определили в файле Compose.

![Расширение VS с развернутым Compose](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Завершение работы

Когда необходимо завершить работу, просто выполните команду `docker-compose down` или щелкните правой кнопкой мыши приложение в списке контейнеров в расширении Docker VS Code и выберите **Compose Down** (завершить Compose). Контейнеры будут остановлены, а сеть удалена.

> [!WARNING]
> **Удаление томов**. По умолчанию именованные тома в файле Compose не удаляются при выполнении команды `docker-compose down`. Если вы хотите удалить тома, необходимо добавить флаг `--volumes`.

После завершения работы можно переключиться на другой проект, запустить `docker-compose up` и подготовиться к работе с этим проектом. На самом деле нет ничего проще!

## <a name="recap"></a>Резюме

В этом разделе вы узнали о средстве Docker Compose и о том, как оно помогает значительно упростить определение и совместное использование приложений с несколькими службами. Вы создали файл Compose, переведя команды в соответствующий формат.

Сейчас начинается завершающий этап обучения. Однако есть несколько рекомендаций по созданию образов, которые необходимо осветить, поскольку есть большая проблема с Dockerfile, который вы использовали. Так что давайте взглянем на это.

## <a name="next-steps"></a>Дальнейшие действия

Продолжайте изучать учебник.

> [!div class="nextstepaction"]
> [Рекомендации по созданию образов](image-building-best-practices.md)
