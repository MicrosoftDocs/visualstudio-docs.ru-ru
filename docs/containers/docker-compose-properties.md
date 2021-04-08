---
title: Параметры сборки Docker Compose
author: ghogen
description: Узнайте, как изменить свойства сборки Docker Compose, чтобы настроить сборку и запуск приложения Docker Compose в Visual Studio.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 4478656af7fff4cfd3a0fdafefe623af5811154f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068301"
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
|DockerComposeBaseFilePath|DCPROJ|Указывает первую часть имен файлов docker-compose без расширения *YML*. Пример: <br>1.  DockerComposeBaseFilePath равен NULL или не определен: используется базовый путь к файлу *docker-compose*, и файлы будут называться *docker-compose.yml* и *docker-compose.override.yml*.<br>2.   DockerComposeBaseFilePath = *mydockercompose*: файлы будут называться *mydockercompose.yml* и *mydockercompose.override.yml*.<br> 3.  DockerComposeBaseFilePath = *..\mydockercompose*: файлы будут располагаться на один уровень выше. |docker-compose|
|DockerComposeBuildArguments|DCPROJ|Указывает дополнительные параметры, передаваемые в команду `docker-compose build`. Например: `--parallel --pull` |
|DockerComposeDownArguments|DCPROJ|Указывает дополнительные параметры, передаваемые в команду `docker-compose down`. Например: `--timeout 500`|-|
|DockerComposeProjectName| DCPROJ | Если указано, переопределяет имя проекта для проекта docker-compose. | dockercompose + автоматически сгенерированный хэш |
|DockerComposeProjectPath|CSPROJ или VBPROJ|Относительный путь к файлу проекта docker-compose (DCPROJ). Задайте это свойство при публикации проекта службы, чтобы можно было найти связанные параметры сборки образа, хранящиеся в файле docker-compose.yml.|-|
|DockerComposeUpArguments|DCPROJ|Указывает дополнительные параметры, передаваемые в команду `docker-compose up`. Например: `--timeout 500`|-|
|DockerDevelopmentMode|DCPROJ| Определяет, включена ли оптимизация "сборка в узле" (отладка в быстром режиме).  Допустимые значения: **Fast** и **Regular**. | Быстрый |
|DockerLaunchAction| DCPROJ | Указывает действие запуска, выполняемое при нажатии клавиши F5 или клавиш CTRL+F5.  Допустимые значения: None, LaunchBrowser и LaunchWCFTestClient.|Отсутствуют|
|DockerLaunchBrowser| DCPROJ | Указывает, следует ли запускать браузер. Игнорируется, если задано свойство DockerLaunchAction. | False |
|DockerServiceName| DCPROJ|Если указано свойство DockerLaunchAction или DockerLaunchBrowser, DockerServiceName — это имя службы, которую следует запустить.  Используйте это свойство, чтобы указать, какой из множества проектов, на которые может ссылаться файл docker-compose, будет запущен.|-|
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

## <a name="docker-compose-file-labels"></a>Метки файлов Docker Compose

Некоторые параметры можно также переопределить, поместив файл *docker-compose.vs.debug.yml* (для конфигурации **отладки**) или *docker-compose.vs.release.yml* (для конфигурации **выпуска**) в один каталог с файлом *docker-compose.yml*.  В этом файле можно задать перечисленные ниже параметры.

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
|com.microsoft.visualstudio.debuggee.killprogram|Эта команда служит для остановки отлаживаемой программы, выполняемой в контейнере (при необходимости).|
|com.microsoft.visualstudio.debuggee.program|Программа, запускаемая при начале отладки. Для приложений .NET Core этот параметр обычно имеет значение **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Каталог, используемый в качестве начального при запуске отладки. Этот параметр обычно имеет значение */app* для контейнеров Linux или *C:\app* для контейнеров Windows.|

## <a name="customize-the-app-startup-process"></a>Настройка процесса запуска приложения

Вы можете выполнить команду или пользовательский скрипт перед запуском приложения с помощью параметра `entrypoint` и сделать их зависимыми от конфигурации. Например, если требуется настроить сертификат только в режиме **Отладка**, запустив `update-ca-certificates`, но не в режиме **Выпуск**, можно добавить следующий код только в *docker-compose.vs.debug.yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

Если опустить *docker-compose.vs.release.yml* или *docker-compose.vs.debug.yml*, Visual Studio создает его на основе параметров по умолчанию.

## <a name="next-steps"></a>Следующие шаги

Общие сведения о свойствах MSBuild см. в статье [Свойства MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>См. также

[Свойства сборки с помощью инструментов для работы с контейнерами](container-msbuild-properties.md)

[Параметры запуска инструментов для работы с контейнерами](container-launch-settings.md)

[Зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
