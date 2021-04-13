---
title: Установка сертификатов для установки в автономном режиме
description: Узнайте, как установить сертификаты для автономной установки Visual Studio.
ms.date: 03/29/2021
ms.custom: seodec18, SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0d8441b0a4b8acba3f24f60d5ea8dc7030b79253
ms.sourcegitcommit: 22789927ec8e877b7d2b67a555d6df97d84103e0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "105981294"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Установка сертификатов, необходимых для установки Visual Studio в автономном режиме

Visual Studio рассчитана в основном на установку на компьютер, подключенный к Интернету, так как многие ее компоненты регулярно обновляются. Но вы можете, выполнив несколько дополнительных действий, создать развертывание Visual Studio и в среде без подключения к Интернету.

Программа установки Visual Studio устанавливает только то содержимое, которое считается доверенным. Перед установкой она проверяет наличие сигнатур Authenticode для скачиваемого содержимого и наличие доверия для всего содержимого. Это позволяет обезопасить среду от атак, направленных на расположение загрузки. Таким образом, программа установки Visual Studio требует наличия актуальных стандартных корневых и промежуточных сертификатов Майкрософт на компьютере пользователя. Если компьютер обновлялся с помощью Центра обновления Windows, сертификаты для подписи обычно актуальны. Если компьютер подключен к Интернету, во время установки Visual Studio сертификаты могут быть обновлены для проверки подписей файлов. Если компьютер не подключен к сети, сертификаты следует обновить иным способом.

## <a name="how-to-refresh-certificates-when-offline"></a>Обновление сертификатов в автономном режиме

В автономной среде установить и обновить сертификаты можно тремя способами.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Вариант 1. Установка сертификатов из папки макета вручную

::: moniker range="vs-2017"

При создании [схемы сети](../install/create-a-network-installation-of-visual-studio.md) или [локального автономного кэша](../install/create-an-offline-installation-of-visual-studio.md) необходимые сертификаты скачиваются в папку Certificates. Затем их можно установить вручную, дважды щелкнув каждый файл сертификата и выполнив инструкции в мастере управления сертификатами. Если он предложит ввести пароль, оставьте это поле пустым.

**Обновление**. Для Visual Studio 2017 версии 15.8 (предварительная версия 2) или более поздней версии вы можете вручную установить сертификаты, щелкнув правой кнопкой мыши каждый файл сертификата, выбрав действие "Установить сертификат" и выполнив инструкции в диалоговых окнах мастера "Диспетчер сертификатов".

::: moniker-end

::: moniker range="vs-2019"

При создании [схемы сети](../install/create-a-network-installation-of-visual-studio.md) или [локального автономного кэша](../install/create-an-offline-installation-of-visual-studio.md) необходимые сертификаты скачиваются в папку Certificates. Вы можете вручную установить сертификаты, щелкнув правой кнопкой мыши каждый файл сертификата, выбрав действие "Установить сертификат" и выполнив инструкции в диалоговых окнах мастера "Диспетчер сертификатов". Если он предложит ввести пароль, оставьте это поле пустым.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Вариант 2. Распространение доверенных корневых сертификатов в среде предприятия

Что касается предприятий с автономными компьютерами, на которых нет последних корневых сертификатов, администратор может использовать инструкции в статье [Настройка доверенных корневых сертификатов и запрещенных сертификатов](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) для их обновления.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Вариант 3. Установка сертификатов в рамках развертывания Visual Studio с помощью скрипта

При настройке развертывания Visual Studio в автономной среде на клиентских рабочих станциях с помощью сценариев необходимо выполнить следующие действия.

1. Скопируйте [средство диспетчера сертификатов](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) в схему сети или расположение экземпляра локального кэша. Программа Certmgr.exe не является компонентом Windows, но доступна как часть пакета [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. С помощью следующих команд создайте пакетный файл сценария:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root
   ```
   
   Или создайте пакетный файл, который использует certutil.exe, входящий в состав Windows, со следующими командами:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Разверните пакетный файл на клиенте. Эту команду необходимо выполнить из процесса с повышенными правами.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Какие файлы сертификатов содержатся в папке Certificates?

* **manifestRootCertificate.cer** содержит:
  * Корневой сертификат: **Microsoft Root Certificate Authority 2011**
* **manifestCounterSignRootCertificate.cer** и **vs_installer_opc.RootCertificate.cer** содержат:
  * Корневой сертификат: **Microsoft Root Certificate Authority 2010**
 
Для Visual Studio Installer требуется наличие в системе только корневых сертификатов. Все эти сертификаты требуются в системах Windows 7 с пакетом обновления 1 (SP1), в которых не установлены последние обновления Центра обновления Windows.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Почему сертификаты из папки Certificates не устанавливаются автоматически?

В среде с подключением к Интернету в процессе проверки подписи используются Windows API для загрузки и добавления сертификатов. Этот процесс включает проверку того, что сертификат является доверенным и допустимым в соответствии с настройками администрирования. В большинстве случаев процесс проверки невозможно выполнить в автономных средах. Установив сертификаты вручную, вы предоставите администраторам предприятия возможность убедиться в том, что сертификаты являются надежными и соответствуют требованиям политики безопасности организации.

## <a name="checking-if-certificates-are-already-installed"></a>Проверка наличия необходимых сертификатов

Чтобы проверить установку системы, можно выполнить следующие действия.

1. Запустите **mmc.exe**.<br/>
  а. В меню **Файл** выберите **Добавить или удалить оснастку**.<br/>
  b. Дважды щелкните **Сертификаты**, выберите **Учетная запись компьютера** и нажмите кнопку **Далее**.<br/>
  c. Выберите **Локальный компьютер**, нажмите кнопку **Готово**, а затем — **ОК**.<br/>
  d. Разверните узел **Сертификаты (локальный компьютер)** .<br/>
  д) Разверните узел **Доверенные корневые центры сертификации** и выберите **Сертификаты**.<br/>
    * Убедитесь, что в этом списке содержатся необходимые корневые сертификаты.<br/>

   е) Разверните узел **Промежуточные центры сертификации** и выберите **Сертификаты**.<br/>
    * Убедитесь, что в этом списке содержатся необходимые промежуточные сертификаты.<br/>

2. В меню **Файл** выберите **Добавить или удалить оснастку**.<br/>
  а. Дважды щелкните **Сертификаты**, выберите **моей учетной записи пользователя**, нажмите кнопки **Готово** и **ОК**.<br/>
  b. Разверните узел **Сертификаты — текущий пользователь**.<br/>
  c. Разверните узел **Промежуточные центры сертификации** и выберите **Сертификаты**.<br/>
    * Убедитесь, что в этом списке содержатся необходимые промежуточные сертификаты.<br/>

Если имена сертификатов не содержатся в столбцах **Кому выдан**, их необходимо установить.  Если промежуточный сертификат находился только в хранилище промежуточных сертификатов **текущего пользователя**, значит он доступен только для пользователя, выполнившего вход в систему. Его может потребоваться установить для других пользователей.

## <a name="install-visual-studio"></a>Установка Visual Studio

После установки сертификатов на клиентском компьютере вы можете [установить Visual Studio из локального кэша](../install/create-an-offline-installation-of-visual-studio.md#step-3---install-visual-studio-from-the-local-cache) или [развернуть Visual Studio из общей папки схемы сети](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) на клиентском компьютере.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также раздел

* [Создание сетевой установки Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

