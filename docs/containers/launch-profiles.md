---
title: Управление профилями запуска для проектов Docker Compose
description: Узнайте, как использовать профили запуска Docker Compose и управлять тем, какие службы запускаются при использовании Docker Compose в Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e740ea3b7950c14bf11522c4e438a105b09eb7f6
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433705"
---
# <a name="manage-launch-profiles-for-docker-compose"></a>Управление профилями запуска для Docker Compose

При наличии приложения, состоящего из нескольких служб и использующего Docker Compose, можно настроить, какие службы будут запущены и отлажены, путем создания или изменения существующего профиля запуска в параметрах запуска Docker Compose. Профили запуска позволяют динамически запускать только службы, которые имеют отношение к текущему сценарию. Вы можете создавать и выбирать профили запуска, чтобы настроить процесс отладки и задать определенные действия запуска, такие как `Browser Launch URL`. Кроме того, можно выбрать каждую службу по отдельности или выбрать профиль Docker Compose, который также будет искать файл Compose, чтобы определить какую группу служб следует запустить.

Дополнительные сведения о профилях Docker Compose см. в разделе [Использование профилей с Compose](https://docs.docker.com/compose/profiles/).
 
## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2019](https://visualstudio.microsoft.com/vs/) версии 16.10 или более поздней.
- Решение с [Согласованием контейнеров с Docker Compose](tutorial-multicontainer.md).

## <a name="manage-launch-settings"></a>Управление параметрами запуска

Рассмотрим следующий проект Docker Compose, в котором *docker-compose.yml* имеет пять служб и три профиля Compose (web, web1 и web2).

```yml
version: '3.9'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    profiles: [web, web1]
    build:
      context: .
      dockerfile: WebApplication1/Dockerfile

  webapplication2:
    image: ${DOCKER_REGISTRY-}webapplication2
    profiles: [web, web2]
    build:
      context: .
      dockerfile: WebApplication2/Dockerfile

  webapplication3:
    image: ${DOCKER_REGISTRY-}webapplication3
    profiles: [web]
    build:
      context: .
      dockerfile: WebApplication3/Dockerfile

  external1:
    image: redis

  external2:
    image: redis

```

Диалоговое окно параметров запуска Docker Compose можно открыть несколькими способами:
- В Visual Studio выберите **Отладка** > **Управление параметрами запуска Docker Compose**.

    ![Снимок экрана: пункт меню "Отладка" > "Управление параметрами запуска Compose".](media/launch-settings/debug-dropdown-manage-compose.png)

- Щелкните правой кнопкой мыши проект `docker-compose` Visual Studio и выберите пункт **Управление параметрами запуска Docker Compose**.

    ![Снимок экрана: элемент контекстного меню](media/launch-settings/launch-settings-context-menu.png)

- Используйте быстрый запуск (**CTRL**+**Q**) и выполните поиск по **Docker Compose**, чтобы найти описанную выше команду.

В приведенном ниже примере выбирается профиль Compose `web1`, который фильтрует список **Службы** до трех из пяти включенных в этот профиль:

!["Снимок экрана: диалоговое окно параметров запуска"](media/launch-settings/launch-settings-create-profile.png)

Раздел профилей Docker Compose отображается только в том случае, если в файлах *docker-compose.yml* определены профили.

В следующем примере показано, как выбирать отдельные службы вместо фильтрации служб в профиле создания. Здесь мы покажем, как будет выглядеть диалоговое окно, если создать новый профиль запуска с именем `test2`, который запускает только две из пяти служб, `webapplication1` при отладке и `webapplication2` без отладки.  Этот профиль запуска также запускает браузер при запуске приложения и открывает его на домашней странице `webapplication1`. 

![Снимок экрана: диалоговое окно параметров запуска, где часть служб не выбрана.](media/launch-settings/launch-settings-selected.png)

Эти сведения будут сохранены в *launchSettings.json*, как показано ниже.

```json
{
    "profiles": {
      "test2": {
        "commandName": "DockerCompose",
        "composeLaunchServiceName": "webapplication1",
        "serviceActions": {
          "external1": "DoNotStart",
          "external2": "DoNotStart",
          "webapplication1": "StartDebugging",
          "webapplication2": "StartWithoutDebugging",
          "webapplication3": "DoNotStart"
        },
        "composeLaunchAction": "LaunchBrowser",
        "commandVersion": "1.0",
        "composeLaunchUrl": "{Scheme}://localhost:{ServicePort}"
      }
   }
}
```

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>Создание профиля запуска, использующего профиль Docker Compose

Кроме того, можно дополнительно настроить поведение при запуске, создав профили запуска Visual Studio, которые используют профили Compose.

Чтобы создать другой профиль, который использует профиль Compose, выберите **Использовать профили Docker Compose**, а затем `web1`. Теперь профиль запуска включает три службы: `webapplication1` (которая принадлежит к профилям Compose `web` и `web1`) `external1` и `external2`. По умолчанию службы без исходного кода, такие как `external1` и `external2`, имеют действие по умолчанию **Запуск без отладки**. Приложения .NET с исходным кодом будут по умолчанию **запускать отладку**.

> [!IMPORTANT]
> Если служба не задает профиль Compose, она будет включена во все профили Compose.

![Снимок экрана: диалоговое окно параметров запуска с еще одним созданным профилем.](media/launch-settings/launch-settings-create-profile.png)

Эти сведения будут сохранены, как показано в следующем коде. Настройка службы и ее действие по умолчанию не сохраняются, если не изменить действие по умолчанию.

```json
{
  "profiles": {
    "test1": {
      "commandName": "DockerCompose",
      "composeProfile": {
         "includes": [
            "web1"
         ]
      },
      "commandVersion": "1.0"
    }
  }
}
```

Можно также изменить действие webapplication1 на **Запуск без отладки**. Параметры в *launchSettings.json* этом примере выглядят следующим образом:

```json
{
  "profiles": {
    "test1": {
        "commandName": "DockerCompose",
        "composeProfile": {
          "includes": [
              "web1"
              ],
          "serviceActions": {
              "webapplication1": "StartWithoutDebugging"
          }
        },
    "commandVersion": "1.0"
    }
  }
}
```

## <a name="properties"></a>Свойства

Ниже приведено описание каждого свойства в *launchSettings.json*:

|Свойство| Описание|
| - | - |
|commandName| Имя команды. По умолчанию используется "DockerCompose".|
|commandVersion| Номер версии, используемый для управления схемой профиля запуска DockerCompose.|
|composeProfile| Родительское свойство, дающее определение профиля запуска. Его дочерними свойствами являются `includes` и `serviceActions`.|
|composeProfile — включает | Список имен профилей Compose, составляющих профиль запуска.|
|composeProfile — serviceActions | Список выбранных профилей Compose, служб и действия запуска каждой службы.|
|serviceActions | Выводит список выбранных служб и действие запуска.|
|composeLaunchServiceName| Если указано свойство DockerLaunchAction или DockerLaunchBrowser, DockerServiceName — это имя службы, которую следует запустить. Используйте это свойство, чтобы определить, какая служба из файла Docker Compose будет запущена.|
|composeLaunchAction| Указывает действие запуска, выполняемое при нажатии **F5** или **CTRL**+**F5**. Допустимые значения: None, LaunchBrowser и LaunchWCFTestClient.|
|composeLaunchUrl| URL-адрес, используемый при запуске браузера. Допустимые токены замены: "{ServiceIPAddress}", "{ServicePort}" и "{Scheme}". Пример: {Scheme}://{ServiceIPAddress}:{ServicePort}|

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о том, как работают средства контейнеров, см. в обзоре [Обзор создания и отладки средств контейнеров Visual Studio](container-build.md).

## <a name="see-also"></a>См. также

- [Параметры запуска инструментов Visual Studio для работы с контейнерами](container-launch-settings.md)

- [Параметры сборки Docker Compose](docker-compose-properties.md)
