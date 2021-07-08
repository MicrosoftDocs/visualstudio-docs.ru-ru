---
title: Параметры сборки Docker Compose
author: ghogen
description: Узнайте, как изменить свойства сборки Docker Compose, чтобы настроить сборку и запуск приложения Docker Compose в Visual Studio.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: b3744640aada798179c86cc60d2c8ce7b02ccfaa
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973483"
---
# <a name="docker-compose-build-properties"></a>Свойства сборки Docker Compose

Помимо свойств для отдельных проектов Docker (см. статью [Свойства сборки с помощью инструментов для работы с контейнерами](container-msbuild-properties.md)), вы можете настроить способ сборки проектов Docker Compose в Visual Studio, задав свойства Docker Compose, используемые MSBuild для сборки решения. Кроме того, вы можете управлять запуском приложений Docker Compose с помощью отладчика Visual Studio. Для этого необходимо задать метки файлов в файлах конфигурации Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Задание свойств MSBuild

Чтобы задать значение свойства, измените файл проекта. Для свойств Docker Compose этот файл проекта имеет расширение DCPROJ, если иное не указано в таблице в следующем разделе. Например, предположим, что при начале отладки должен запускаться браузер. Вы можете задать свойство `DockerLaunchAction` в файле проекта DCPROJ указанным ниже образом.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Вы можете добавить значение свойства в существующий элемент `PropertyGroup` или, если его нет, создать новый элемент `PropertyGroup`.

## <a name="docker-compose-msbuild-properties"></a>Свойства MSBuild для Docker Compose

В таблице ниже приводятся свойства MSBuild, доступные для проектов Docker Compose.

| Имя свойства | Местоположение | Описание | Значение по умолчанию  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|DCPROJ|Указывает дополнительные файлы Compose в списке, разделенном точкой с запятой, которые будут отправлены в docker-compose.exe для всех команд. Относительные пути от файла проекта docker-compose (DCPROJ) разрешены.|-|
|DockerComposeBaseFilePath|DCPROJ|Указывает первую часть имен файлов docker-compose без расширения *YML*. Пример: <br>1. DockerComposeBaseFilePath = null/undefined: используйте базовый путь к файлу *docker-compose*, и файлы будут называться *docker-compose.yml* и *docker-compose.override.yml*.<br>2. DockerComposeBaseFilePath = *mydockercompose*: файлы будут называться *mydockercompose.yml* и *mydockercompose.override.yml*.<br> 3. DockerComposeBaseFilePath = *..\mydockercompose*: файлы будут располагаться на уровень выше. |docker-compose|
|DockerComposeBuildArguments|DCPROJ|Указывает дополнительные параметры, передаваемые в команду `docker-compose build`. Например, `--parallel --pull`. |
|DockerComposeDownArguments|DCPROJ|Указывает дополнительные параметры, передаваемые в команду `docker-compose down`. Например, `--timeout 500`.|-|  
|DockerComposeProjectName| DCPROJ | Если указано, переопределяет имя проекта для проекта docker-compose. | dockercompose + автоматически сгенерированный хэш |
|DockerComposeProjectPath|CSPROJ или VBPROJ|Относительный путь к файлу проекта docker-compose (DCPROJ). Задайте это свойство при публикации проекта службы, чтобы можно было найти связанные параметры сборки образа, хранящиеся в файле docker-compose.yml.|-|
|DockerComposeProjectsToIgnore|DCPROJ| Определяет проекты, игнорируемые средствами docker-compose во время отладки. Это свойство можно использовать для любого проекта. Пути к файлам можно указать одним из двух способов: <br> 1. Относительно DCPROJ. Например, `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. Абсолютные пути.<br> **Примечание.** Пути должны быть разделены с помощью символа `;`.|-|
|DockerComposeUpArguments|DCPROJ|Указывает дополнительные параметры, передаваемые в команду `docker-compose up`. Например, `--timeout 500`.|-|
|DockerDevelopmentMode| DCPROJ | Определяет, создан ли пользовательский проект в контейнере. Допустимые значения **Fast** или **Regular** определяют, [какие этапы создаются](https://aka.ms/containerfastmode) в Dockerfile. По умолчанию в качестве конфигурации отладки используется режим Fast, в противном случае — режим Regular. | Быстрый |
|DockerLaunchAction| DCPROJ | Указывает действие запуска, выполняемое при нажатии клавиши F5 или клавиш CTRL+F5.  Допустимые значения: None, LaunchBrowser и LaunchWCFTestClient. | Отсутствуют |
|DockerLaunchBrowser| DCPROJ | Указывает, следует ли запускать браузер. Игнорируется, если задано свойство DockerLaunchAction. | False |
|DockerServiceName| DCPROJ| Если указать DockerLaunchAction или DockerLaunchBrowser, тогда DockerServiceName определяет запускаемую службу, на которую есть ссылка в файле docker-compose.|-|
|DockerServiceUrl| DCPROJ | URL-адрес, используемый при запуске браузера.  Допустимые токены замены: "{ServiceIPAddress}", "{ServicePort}" и "{Scheme}".  Пример: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| DCPROJ | Целевая ОС, используемая при сборке образа Docker.|-|

## <a name="example"></a>Пример

Если изменить расположение файлов Docker Compose, задав для `DockerComposeBaseFilePath` относительный путь, необходимо также убедиться, что контекст сборки изменен и ссылается на папку решения. Например, если файл Docker Compose находится в папке *DockerComposeFiles*, он должен задавать ".." или "../.." для контекста сборки в зависимости от его расположения относительно папки решения.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

Файл *mydockercompose.yml* должен выглядеть так, как показано ниже. Для контекста сборки задан относительный путь к папке решения (в данном случае `..`).

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> Свойства DockerComposeBuildArguments, DockerComposeDownArguments и DockerComposeUpArguments появились в Visual Studio 2019 версии 16.3.

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Переопределение конфигурации Docker Compose в Visual Studio

Некоторые параметры можно переопределить, поместив файл *docker-compose.vs.debug.yml* (для режима **Fast**) или *docker-compose.vs.release.yml* (для режима **Regular**) в один каталог с файлом *docker-compose.yml*. 

>[!TIP] 
>Чтобы узнать значения по умолчанию для любого из этих параметров, см. файл *docker-compose.vs.debug.g.yml* или *docker-compose.vs.release.g.yml*.

### <a name="docker-compose-file-labels"></a>Метки файлов Docker Compose

 В файле *docker-compose.vs.debug.yml* или *docker-compose.vs.release.yml* можно определить метки override-specific:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Заключайте значения в двойные кавычки, как в предыдущем примере, и используйте обратную косую черту как escape-символ для обратных косых черт в путях.

|Имени метки|Описание|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Аргументы, передаваемые в программу при запуске отладки. Для приложений .NET Core эти аргументы обычно представляют собой дополнительные пути поиска пакетов NuGet, за которыми следует путь к выходной сборке проекта.|
|com.microsoft.visualstudio.debuggee.program|Программа, запускаемая при начале отладки. Для приложений .NET Core этот параметр обычно имеет значение **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Каталог, используемый в качестве начального при запуске отладки. Этот параметр обычно имеет значение */app* для контейнеров Linux или *C:\app* для контейнеров Windows.|
|com.microsoft.visualstudio.debuggee.killprogram|Эта команда служит для остановки отлаживаемой программы, выполняемой в контейнере (при необходимости).|

### <a name="customize-the-docker-build-process"></a>Настройка процесса сборки Docker

Вы можете объявить создаваемый этап в Dockerfile, используя параметр `target` в свойстве `build`. Это переопределение можно использовать только в файле *docker-compose.vs.debug.yml* или *docker-compose.vs.release.yml*. 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Настройка процесса запуска приложения

Вы можете выполнить команду или пользовательский скрипт перед запуском приложения с помощью параметра `entrypoint`, создав зависимость от `DockerDevelopmentMode`. Например, если вам нужно настроить сертификат только в режиме **Fast**, запустив `update-ca-certificates`, но не в режиме **Regular**, можно добавить следующий код **только** в файл *docker-compose.vs.debug.yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Следующие шаги

Общие сведения о свойствах MSBuild см. в статье [Свойства MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>См. также

[Свойства сборки с помощью инструментов для работы с контейнерами](container-msbuild-properties.md)

[Параметры запуска инструментов для работы с контейнерами](container-launch-settings.md)

[Управление профилями запуска для Docker Compose в Visual Studio](launch-profiles.md)

[Зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
