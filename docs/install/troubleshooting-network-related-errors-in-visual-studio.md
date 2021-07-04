---
title: Устранение неполадок сети или ошибок прокси-сервера
description: Ознакомьтесь с решениями распространенных ошибок сети или прокси-сервера, которые могут возникать при установке или использовании Visual Studio за брандмауэром или прокси-сервером.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5e7d54b4e7777b3569031e96760699e7c075245f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306830"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Исправление ошибок сети при установке или использовании Visual Studio

У нас есть решения для распространенных ошибок сети или прокси-сервера, которые могут возникать при установке или использовании Visual Studio за брандмауэром или прокси-сервером.

## <a name="error-proxy-authorization-required"></a>Ошибка: "Требуется проверка подлинности на прокси-сервере"

Эта ошибка обычно происходит, когда пользователи подключаются к Интернету через прокси-сервер, который блокирует вызовы Visual Studio к некоторым сетевым ресурсам.

### <a name="to-fix-this-proxy-error"></a>Устранение этой ошибки прокси-сервера

- Перезапустите Visual Studio. Должно появиться диалоговое окно проверки подлинности прокси. Когда в диалоговом окне появится запрос, введите свои учетные данные.

- Если перезапуск Visual Studio не решит проблему, возможно, прокси-сервер не запрашивает учетные данные для адресов http:&#47;&#47;go.microsoft.com, но делает это для адресов &#42;.visualStudio.microsoft.com. Для таких серверов попробуйте включить в список разрешенных перечисленные ниже URL-адреса, чтобы разблокировать все сценарии входа в Visual Studio:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- В противном случае из списка разрешенных можно удалить адрес http:&#47;&#47;go.microsoft.com, чтобы при перезапуске Visual Studio диалоговое окно проверки подлинности прокси-сервера открывалось для адреса http:&#47;&#47;go.microsoft.com и конечных точек сервера.

  -ИЛИ-

- Если вы хотите использовать учетные данные по умолчанию для прокси-сервера, сделайте следующее:

::: moniker range="vs-2017"

  1. Найдите файл **devenv.exe.config** (файл конфигурации devenv.exe) в папке **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** или **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. В файле конфигурации найдите блок `<system.net>` и добавьте следующий код:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      В `proxyaddress="<http://<yourproxy:port#>` необходимо вставить правильный адрес прокси-сервера в сети.

     > [!NOTE]
     > Дополнительные сведения см. на страницах [Элемент &lt;defaultProxy&gt; (сетевые параметры)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) и [Элемент &lt;proxy&gt; (сетевые параметры)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings).

::: moniker-end

::: moniker range=">=vs-2019"

  1. Найдите файл **devenv.exe.config** (файл конфигурации devenv.exe) в папке **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** или **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. В файле конфигурации найдите блок `<system.net>` и добавьте следующий код:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      В `proxyaddress="<http://<yourproxy:port#>` необходимо вставить правильный адрес прокси-сервера в сети.

     > [!NOTE]
     > Дополнительные сведения см. на страницах [Элемент &lt;defaultProxy&gt; (сетевые параметры)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) и [Элемент &lt;proxy&gt; (сетевые параметры)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings).

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>Ошибка: "Отсутствует подключение к Visual Studio" при попытке сообщить о проблеме

Эта ошибка обычно возникает, когда пользователи подключаются к Интернету через прокси-сервер, который блокирует вызовы Visual Studio к некоторым сетевым ресурсам.

### <a name="to-fix-this-proxy-error"></a>Устранение этой ошибки прокси-сервера

1. Найдите файл **feedback.exe.config** (файл конфигурации feedback.exe) в папке: **%ProgramFiles(x86)%\Microsoft Visual Studio\Installer** или **%ProgramFiles%\Microsoft Visual Studio\Installer**.

2. В файле конфигурации проверьте, присутствует ли следующий код; если код отсутствует, добавьте его перед последней строкой `</configuration>`.

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

## <a name="error-the-underlying-connection-was-closed"></a>Ошибка: "Используемое соединение было закрыто"

Если вы работаете с Visual Studio в частной сети, где есть брандмауэр, Visual Studio может быть не в состоянии подключиться к некоторым сетевым ресурсам. К таким ресурсам могут относиться Azure DevOps Services для входа и лицензирования, а также NuGet и службы Azure. Если Visual Studio не удается подключиться к одному из этих ресурсов, отображается следующее сообщение об ошибке:

  **Базовое соединение закрыто: непредвиденная ошибка при передаче**

Visual Studio использует протокол TLS 1.2 для подключения к сетевым ресурсам. Устройства для обеспечения безопасности в частных сетях блокируют определенные подключения к серверу, если Visual Studio использует TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Устранение этой ошибки подключения

Включите возможность подключения для следующих URL-адресов:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (для подключений к Azure)

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (размещение сети доставки содержимого или CDN)

- &#42;.gallerycdn.vsassets.io (размещает расширение Azure DevOps Services)

- static2.sharepointonline.com (размещение ресурсов, которые Visual Studio использует в комплекте Office UI Fabric, например, шрифтов)

- &#42;.nuget.org (для подключений к NuGet)

  > [!NOTE]
  > Частные URL-адреса серверов NuGet могут быть не включены в этот список. Используемые вами серверы NuGet можно посмотреть в файле %APPData%\Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Ошибка: "Не удалось проанализировать идентификатор из родительского процесса"

Это сообщение об ошибке может появиться при использовании на сетевом диске начального загрузчика Visual Studio и файла response.json. Источником ошибки является Контроль учетных записей пользователей (UAC) в Windows.

Причины возникновения этой ошибки: Подключенный сетевой диск или общий ресурс [UNC](/dotnet/standard/io/file-path-formats#unc-paths) связан с маркером доступа пользователя. При включении UAC создаются два [маркера доступа](/windows/win32/secauthz/access-tokens) пользователя: один *с* правами администратора и один *без* прав администратора. При создании сетевого диска или общего ресурса с ним связывается текущий маркер доступа пользователя. Поскольку начальный загрузчик следует запускать от имени администратора, он не сможет получить доступ к сетевому диску или общему ресурсу, если диск или общая папка не связаны с маркером доступа пользователя, который имеет права администратора.

### <a name="to-fix-this-error"></a>Устранение этой ошибки

Можно использовать команду `net use` или изменить параметр групповой политики UAC. Дополнительные сведения об этих обходных путях и их реализации см. в следующих статьях службы поддержки Майкрософт:

* [Mapped drives are not available from an elevated prompt when UAC is configured to "Prompt for credentials" in Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co) (Подключенные диски недоступны в приглашении с повышенными привилегиями при настройке UAC на "запрос учетных данных" в Windows)
* [Programs may be unable to access some network locations after you turn on User Account Control in Windows operating systems](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn) (Программам не удается получить доступ к некоторым сетевым расположениям после включения контроля учетных записей пользователей в операционных системах Windows)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка и использование Visual Studio в среде, защищенной брандмауэром или прокси-сервером](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Установка Visual Studio](install-visual-studio.md)
