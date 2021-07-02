---
title: Учебник по Docker. Часть 8. Слои в образе
description: Изучение и управление слоями образов в Docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8f669baf6f3275f54c7e4a6ff2b31f9c260b2bb9
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222673"
---
# <a name="image-layering"></a>Слои в образе

Знаете ли вы, что можно посмотреть, из чего состоит образ? С помощью команды `docker image history` можно просмотреть команды, которые использовались для создания каждого слоя в образе.

1. Используйте команду `docker image history`, чтобы просмотреть слои в образе `getting-started`, созданном ранее в этом учебнике.

    ```bash
    docker image history getting-started
    ```

    Вы должны получить примерно следующие выходные данные (даты и идентификаторы могут отличаться).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Каждая строка представляет слой в образе. Здесь внизу показана основа, а вверху — самый новый слой. С помощью этой команды можно также быстро просмотреть размер каждого слоя, что помогает диагностировать большие образы.

1. Обратите внимание, что некоторые строки усекаются. Если добавить флаг `--no-trunc`, то вы получите полный вывод (да, для получения неусеченных выходных данных используется флаг усечения).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Кэширование слоев

Теперь, когда вы увидели слои в действии, нужно усвоить еще один важный урок, который поможет сократить время сборки для образов контейнеров.

> После изменения слоя все нижестоящие слои также необходимо создать заново.

Давайте еще раз взглянем на файл Dockerfile, который вы использовали…

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Вернувшись к выходным данным журнала образа, вы увидите, что каждая команда в Dockerfile превращается в новый слой в образе. Возможно, вы помните, что при внесении изменений в образ необходимо было переустановить зависимости Yarn. Есть ли способ обойти это? Нет смысла устанавливать одни и те же зависимости при каждой сборке, верно?

Чтобы устранить эту проблему, можно изменить структуру Dockerfile для обеспечения поддержки кэширования зависимостей. Для приложений на основе узлов эти зависимости определяются в файле `package.json`. Поэтому что если сначала скопировать только этот файл, установить зависимости и *затем* скопировать все остальное? После этого повторное создание зависимостей Yarn нужно будет выполнять только в том случае, если было внесено изменение в файл `package.json`. Разумно?

1. Сначала измените файл Dockerfile, чтобы выполнить копирование в `package.json`, установите зависимости, а затем скопируйте все остальное.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Создайте новый образ с помощью `docker build`.

    ```bash
    docker build -t getting-started .
    ```

    Должен отобразиться примерно следующий результат.

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Вы увидите, что все слои были перестроены. Прекрасно, ведь вы совсем немного изменили файл Dockerfile.

1. Теперь внесите изменения в файл `src/static/index.html` (например, измените `<title>`, скажем, на "Отличное приложение для списка дел").

1. Снова создайте образ Docker, используя `docker build`. На этот раз выходные данные должны выглядеть немного иначе.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    Во-первых, вы должны заметить, что сборка выполнялась ГОРАЗДО быстрее! И вы увидите, что у шагов 1–4 стоит `Using cache`. Ура! Вы используете кэш сборки. Отправка и извлечение этого образа и изменения в нем будут выполняться гораздо быстрее. Поздравляем!

## <a name="multi-stage-builds"></a>Многоэтапная сборка

Хотя в этом уроке мы и не будем углубляться в детали многоэтапных сборок, но они являются невероятно мощным средством для использования нескольких этапов для создания образа. У них есть несколько преимуществ.

- Отделение зависимостей времени сборки от зависимостей среды выполнения.
- Уменьшение общего размера образа за счет доставки *только* того, что нужно вашему приложению для работы.

### <a name="maventomcat-example"></a>Пример с Maven и Tomcat

При создании приложений на основе Java для компиляции исходного кода в байт-код Java требуется JDK. Но JDK не требуется в рабочей среде. Кроме того, можно использовать такие средства, как Maven или Gradle, для облегчения сборки приложения.
Они также не нужны в окончательном образе. Здесь поможет многоэтапная сборка.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

В этом примере один этап (называемый `build`) используется для выполнения фактической сборки Java с помощью Maven. Второй этап (начиная с `FROM tomcat`) копирует в файлы с этапа `build`. Окончательный образ создается только на последнем этапе (что можно переопределить с помощью флага `--target`).

### <a name="react-example"></a>Пример React

При создании приложений React требуется среда узла для компиляции кода JS (обычно JSX), таблиц стилей SASS и др. в статический HTML, JS и CSS. Если вы не выполняете отрисовку на стороне сервера, вам даже не нужна среда узла для рабочей сборки. Почему бы не отправить статические ресурсы в статическом контейнере nginx?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

Здесь мы используем образ `node:12` для выполнения сборки (максимально используя уровень кэширования) и затем копируем выходные данные в контейнер nginx. Здорово, правда?

## <a name="recap"></a>Резюме

Немного поняв, как структурированы образы, вы сможете быстрее создавать образы и вносить меньше изменений. Многоэтапные сборки также позволяют сократить общий размер образа и повысить уровень безопасности контейнера, разделив зависимости времени сборки от зависимостей среды выполнения.

## <a name="next-steps"></a>Дальнейшие действия

Продолжайте изучать учебник.

> [!div class="nextstepaction"]
> [Развертывание в облаке](deploy-to-cloud.md)