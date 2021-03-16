---
title: Настройка Python в службе приложений Azure (Windows)
description: Установка интерпретатора и библиотек Python в Службе приложений Azure и настройка веб-приложений, чтобы в них содержалась правильная ссылка на интерпретатор.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f7c874a5cd2742f795c6d8b04db88b98b19a556d
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470018"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Работа с Python в "Службе приложений Azure" (Windows)

> [!Important]
> Корпорация Майкрософт объявила нерекомендуемыми расширения Python для службы приложений в Windows, как описано в этой статье, и рекомендует прямое развертывание в [службе приложений в Linux](publishing-python-web-applications-to-azure-from-visual-studio.md).

[Служба приложений Azure](https://azure.microsoft.com/services/app-service/) — это предложение вида "платформа как услуга" для веб-приложений, представлены ли они сайтами, к которым обращаются через браузер, REST API, используемыми вашими собственными клиентами, либо обработкой с активацией по событиям. Служба приложений полностью поддерживает использование Python для реализации приложений.

Настраиваемая поддержка Python в службе приложений Azure представлена набором *расширений сайтов*, каждое из которых содержит определенную версию среды выполнения Python. В этом окружении можно устанавливать любые требуемые пакеты, как описано в этой статье. Благодаря настройке среды в самой службе приложений вам не нужно обеспечивать наличие пакетов в проектах веб-приложений или добавлять их в коде приложения.

> [!Tip]
> Хотя в службе приложений по умолчанию установлены среды Python 2.7 и Python 3.4 в корневых папках на сервере, настраивать или устанавливать пакеты в этих средах нельзя. Кроме того, не следует полагаться на их наличие. Вместо этого используйте расширение сайта, которым вы управляете, как описано в этой статье.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Выбор версии Python с помощью портала Azure

1. Создайте службу приложений для веб-приложения на портале Azure.
1. Прокрутите содержимое страницы службы приложений до раздела **Средства разработки**, выберите **Расширения**, а затем нажмите **+ Добавить**.
1. Прокрутите список до расширения, содержащего нужную версию Python.

    ![Портал Azure с расширениями Python](media/python-on-azure-extensions.png)

    > [!Tip]
    > Если вам нужна более старая версия Python, которой нет в списке расширений сайта, ее можно установить посредством Azure Resource Manager, как описано в следующем разделе.

1. Выберите расширение, примите юридические условия и нажмите кнопку **ОК**.
1. По завершении установки на портале появится уведомление.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Выбор версии Python с помощью Azure Resource Manager

Если вы развертываете службу приложений с помощью шаблона Azure Resource Manager, добавьте расширение сайта в качестве ресурса. В частности, расширение отображается в виде вложенного ресурса (объект `resources` в `resources`) с типом `siteextensions`.

Например, после добавления ссылки на `python361x64` (Python 3.6.1 x64) шаблон может выглядеть следующим образом (некоторые свойства опущены):

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Указание интерпретатора Python в файле web.config

После установки расширения сайта (с помощью портала или шаблона Azure Resource Manager) необходимо указать интерпретатор Python в файле *web.config* приложения. Файл *web.config* предоставляет веб-серверу служб IIS (версии 7 или более поздней), на котором выполняется служба приложений, информацию о том, как он должен обрабатывать запросы Python по протоколу FastCGI или HttpPlatform (рекомендуется).

Сначала определите полный путь к файлу *python.exe* расширения сайта, а затем создайте и измените соответствующий файл *web.config*.

### <a name="find-the-path-to-pythonexe"></a>Определение пути к файлу python.exe

Расширение сайта Python устанавливается на сервере в каталоге *d:\home* в папке, соответствующей версии и архитектуре Python (кроме нескольких старых версий). Например, 64-разрядная версия Python 3.6.1 устанавливается в папке *d:\home\python361x64*. Полный путь к интерпретатору Python в этом случае будет иметь вид *d:\home\python361x64\python.exe*.

Чтобы увидеть путь в вашей службе приложений, на ее странице щелкните **Расширения**, а затем выберите расширение в списке.

![Список расширений в службе приложений Azure](media/python-on-azure-extension-list.png)

В результате этого действия открывается страница с описанием расширения, включая путь:

![Сведения о расширении в службе приложений Azure](media/python-on-azure-extension-detail.png)

Если у вас возникают трудности с просмотром пути к расширению, вы можете определить его вручную с помощью консоли.

1. На странице службы приложений выберите **Средства разработки** > **Консоль**.
1. Введите команду `ls ../home` или `dir ..\home`, чтобы увидеть папки расширений верхнего уровня, например *Python361x64*.
1. Чтобы проверить, содержит ли папка файл *python.exe* и (или) другие файлы интерпретатора, введите команду вида `ls ../home/python361x64` или `dir ..\home\python361x64`.

### <a name="configure-the-httpplatform-handler"></a>Настройка обработчика HttpPlatform

Модуль HttpPlatform передает подключения через сокет напрямую в автономный процесс Python. Такая сквозная передача позволяет запускать нужный веб-сервер, но требует выполнения скрипта запуска на локальном веб-сервере. Укажите скрипт в элементе `<httpPlatform>` файла *web.config*, где атрибут `processPath` указывает на интерпретатор Python для расширения сайта, а атрибут `arguments` указывает скрипт и содержит все аргументы для него:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

Показанная здесь переменная среды `HTTP_PLATFORM_PORT` содержит порт, который должен прослушивать локальный сервер для соединений от localhost. Этот пример также показывает, как при необходимости создать другую переменную среды, в данном случае это `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Настройка обработчика FastCGI

FastCGI — это интерфейс, работающий на уровне запроса. Службы IIS принимают входящие подключения и перенаправляют каждый запрос в приложение WSGI, работающее в одном или нескольких сохраняемых процессах Python. [Пакет wfastcgi](https://pypi.io/project/wfastcgi) предварительно установлен и настроен для каждого расширения сайта Python, поэтому вы можете легко включить его, добавив в файл *web.config* приблизительно следующий код для веб-приложения на основе платформы Bottle. Обратите внимание, что полные пути к *python.exe* и *wfastcgi.py* находятся в ключе `PythonHandler`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Определенные здесь параметры `<appSettings>` доступны для вашего приложения в качестве переменных среды:

- Значение `PYTHONPATH` можно свободно расширить, однако оно должно включать корень приложения.
- `WSGI_HANDLER` должен указывать на приложение WSGI, импортируемое из приложения.
- `WSGI_LOG` является необязательным, но рекомендуется для отладки приложения.

Дополнительные сведения о содержимом файла *web.config* для веб-приложений Bottle, Flask и Django см. в руководстве по [публикации в Azure](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="install-packages"></a>Установка пакетов

Интерпретатор Python, установленный посредством расширения сайта, — это всего лишь один из элементов среды Python. Вам, скорее всего, потребуется также установить в среде различные пакеты.

Чтобы установить пакеты в серверной среде напрямую, используйте один из указанных ниже способов.

| Методы | Использование |
| --- | --- |
| [Консоль Kudu для Службы приложений Azure](#azure-app-service-kudu-console) | Установка пакетов в интерактивном режиме. Пакеты должны содержать чистый код Python или публиковаться в формате wheel. |
| [REST API Kudu](#kudu-rest-api) | Можно использовать для автоматизации установки пакетов.  Пакеты должны содержать чистый код Python или публиковаться в формате wheel. |
| Объединение с приложением | Установка пакетов непосредственно в проекте и последующее их развертывание в службе приложений так, как если бы они были частью приложения. В зависимости от числа имеющихся зависимостей и частоты их обновления этот метод может оказаться самым простым для получения рабочего развертывания. Учтите, что библиотеки должны соответствовать версии Python на сервере. В противном случае после развертывания возникнут непонятные ошибки. Так как версии Python в расширениях сайтов службы приложений полностью аналогичны тем, которые опубликованы на сайте python.org, вы легко можете получить совместимую версию для локальной разработки. |
| Виртуальные среды | Не поддерживается. Вместо этого используйте объединение в пакет и задайте значение переменной среды `PYTHONPATH` так, чтобы она указывала на расположение пакетов. |

### <a name="azure-app-service-kudu-console"></a>Консоль Kudu для Службы приложений Azure

[Консоль Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) предоставляет вам прямой доступ к серверу службы приложений и его файловой системе из командной строки с повышенными привилегиями. С одной стороны, она является полезным средством отладки, а с другой — обеспечивает выполнение в интерфейсе командной строки таких операций, как установка пакетов.

1. Откройте Kudu со страницы службы приложений на портале Azure, выбрав пункты **Средства разработки** > **Дополнительные инструменты**, а затем нажав кнопку **Перейти**. В результате этого действия будет выполнен переход по URL-адресу, который совпадает с базовым URL-адресом службы приложений, но с добавлением `.scm`. Например, если базовый URL-адрес имеет вид `https://vspython-test.azurewebsites.net/`, то для Kudu используется `https://vspython-test.scm.azurewebsites.net/` (можно добавить в закладки):

    ![Консоль Kudu для службы приложений Azure](media/python-on-azure-console01.png)

1. Выберите **Консоль отладки** > **CMD**, чтобы открыть консоль, где можно перейти к установке Python и узнать, какие библиотеки уже доступны.

1. Установка отдельного пакета:

    a. Перейдите в папку установки Python, в которую вы хотите установить пакет, например *d:\home\python361x64*.

    b. Используйте команду `python.exe -m pip install <package_name>` для установки пакета.

    ![Пример установки Bottle через консоль Kudu для службы приложений Azure](media/python-on-azure-console02.png)

1. Если вы уже развернули на сервере файл *requirements.txt* для приложения, установите указанные в нем требуемые компоненты, как описано ниже.

    a. Перейдите в папку установки Python, в которую вы хотите установить пакет, например *d:\home\python361x64*.

    b. Выполните команду `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Мы рекомендуем использовать файл *requirements.txt*, так как он позволяет легко воспроизвести точный набор пакетов как в локальной среде, так и на сервере. Просто не забудьте открыть консоль после развертывания изменений в *requirements.txt* и выполнить эту команду еще раз.

> [!Note]
> В службе приложений нет компилятора C, поэтому нужно установить "колесо" (wheel) для всех пакетов с собственными модулями расширения. Многие популярные пакеты имеют свои собственные колеса. В противном случае используйте `pip wheel <package_name>` на локальном компьютере разработки, после чего отправьте колесо на сайт. Пример см. в руководстве по [управлению требованиями к пакетам с помощью файла requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>REST API Kudu

Вместо использования консоли Kudu на портале Azure можно выполнять команды удаленно через REST API Kudu, публикуя их по адресу `https://yoursite.scm.azurewebsites.net/api/command`. Например, чтобы установить пакет `bottle`, опубликуйте следующую JSON по адресу `/api/command`:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Сведения о командах и проверке подлинности см. в [документации по Kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

Просмотреть учетные данные можно также с помощью команды `az webapp deployment list-publishing-profiles`, которая выполняется в интерфейсе командной строки Azure (см. описание команды [az webapp deployment](/cli/azure/webapp/deployment?view=azure-cli-latest&preserve-view=true#az-webapp-deployment-list-publishing-profiles)). Вспомогательную библиотеку для отправки команд Kudu можно найти на сайте [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).
