---
title: Руководство администратора Visual Studio
titleSuffix: ''
description: Дополнительные сведения о способах развертывания Visual Studio в корпоративной среде.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0b86d8bc6d3533d2ed50eb4e87330a81f1028f13
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547418"
---
# <a name="visual-studio-administrator-guide"></a>Руководство администратора Visual Studio

В корпоративных средах системные администраторы часто развертывают установки для пользователей из общей сетевой папки или с помощью программного обеспечения для управления системами. Мы создали механизм установки Visual Studio, который поддерживает корпоративные сценарии развертывания. Это позволяет системным администраторам создать сетевое расположение и настроить параметры по умолчанию для развертывания ключей продукта во время установки и для управления обновлениями продуктов после успешного развертывания.

В этом руководстве администратора представлено руководство на основе сценария для корпоративного развертывания в сетевых окружениях.

## <a name="before-you-begin"></a>Подготовка к работе

Перед развертыванием Visual Studio в вашей организации нужно принять определенные решения и выполнить задачи:

::: moniker range="vs-2019"

* Убедитесь, что каждый конечный компьютер отвечает [минимальным требованиям к установке](/visualstudio/releases/2019/system-requirements/).

::: moniker-end

::: moniker range="vs-2017"

* Убедитесь, что каждый конечный компьютер отвечает [минимальным требованиям к установке](/visualstudio/productinfo/vs2017-system-requirements-vs/).

::: moniker-end

* Определите потребности обслуживания.

  Если организации требуется подольше оставаться на определенном наборе функций, но также нужно получать регулярные обновления обслуживания, следует использовать план обслуживания. Дополнительные сведения см. в разделе ***Варианты поддержки для клиентов Enterprise и Professional*** статьи [Жизненный цикл и обслуживание продукта Visual Studio](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers), а также в статье [Обновление Visual Studio во время обслуживания](update-servicing-baseline.md).

* Выберите модель обновления.

  Из какого расположения отдельные клиентские компьютеры должны получать обновления продуктов? В частности, решите, откуда клиент должен получать обновления: из Интернета или корпоративной локальной общей папки. Если вы решили использовать локальный общий ресурс, решите, могут ли отдельные пользователи обновлять свои собственные клиенты, или необходимо, чтобы администратор программным способом обновлял клиенты. Лучше, чтобы эти решения были приняты до того, как исходная установка будет выполнена на клиентском компьютере. Дополнительные сведения см. в статье [Создание сетевой установки Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md).

  Вы можете обновить макет сетевой установки Visual Studio, включив последнее обновление продукта, чтобы использовать его в качестве точки установки обновлений Visual Studio и обеспечить поддержку уже развернутых установок на клиентских рабочих станциях. Дополнительные сведения см. в статье [Обновление сетевой установки Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Организации, в которых используются средства корпоративного развертывания, могут воспользоваться тем, что обновления Visual Studio доступны в каталоге Центра обновления Майкрософт и Windows Server Update Services. Дополнительные сведения см. в статьях [Включение обновлений администратора](../install/enabling-administrator-updates.md) и [Применение обновлений администратора](../install/applying-administrator-updates.md).

  Для компьютеров, не подключенных к Интернету, создание минимального макета — самый простой и быстрый способ обновления автономных экземпляров Visual Studio. Дополнительные сведения см. в статье [Обновление Visual Studio с использованием минимального автономного макета](update-minimal-layout.md).

::: moniker range="vs-2019"

* Решите, какой набор [рабочих нагрузок и компонентов](workload-and-component-ids.md?view=vs-2019&preserve-view=true) отвечает потребностям вашей компании.

* Решите, следует ли использовать [файл ответов](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) (это упрощает управление сведениями в файле скрипта).

::: moniker-end

::: moniker range="vs-2017"

* Решите, какой набор [рабочих нагрузок и компонентов](workload-and-component-ids.md?view=vs-2017&preserve-view=true) отвечает потребностям вашей компании.

* Решите, следует ли использовать [файл ответов](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) (это упрощает управление сведениями в файле скрипта).

::: moniker-end

* Решите, нужно ли включение групповой политики и хотите ли вы отключить в Visual Studio отправку отзывов пользователей с отдельных компьютеров.

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Шаг 1.Скачивание файлов продукта Visual Studio

* [Выберите набор рабочих нагрузок и компонентов](workload-and-component-ids.md?view=vs-2019&preserve-view=true), которые требуется установить.

* [Создайте общую сетевую папку для файлов продукта Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Шаг 2. Создание скрипта установки

* Создайте скрипт установки, который использует [параметры командной строки](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) для управления установкой.

  >[!NOTE]
  > Его можно упростить с помощью [файла ответов](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true). Обязательно создайте файл ответов с параметрами установки по умолчанию.

* Также вы можете [применить ключ корпоративной лицензии](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true) в рамках скрипта установки, чтобы освободить пользователей от дополнительных действия для активации программного обеспечения.

* При необходимости обновите структуру сети для [управления временем и источником обновлений для конечных пользователей](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true).

* При необходимости можно задать политики реестра, влияющие на развертывание Visual Studio, например, место, где установлены некоторые пакеты, используемые совместно с другими версиями или экземплярами, [где кэшируются пакеты](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) или [кэшируются ли пакеты вообще](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true).

* При необходимости задайте групповую политику. Также можно настроить в Visual Studio [отключение отправки отзывов пользователей с отдельных компьютеров](../ide/visual-studio-experience-improvement-program.md).

## <a name="step-3---deploy-updates"></a>Шаг 3. Развертывание обновлений

Примените любую удобную технологию развертывания, чтобы выполнить скрипт на целевых рабочих станциях разработчиков.

* Регулярно [дополняйте расположение сетевой установки последними обновлениями](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true) для Visual Studio, повторно выполняя команду из шага 1 для добавления новых компонентов.

  Visual Studio можно обновить с помощью скрипта обновления. Чтобы сделать это, используйте параметр командной строки [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true).

  Обновления Visual Studio можно развернуть из Windows Server Update Services или каталога Центра обновления Майкрософт с помощью таких средств, как System Center Configuration Manager.  Дополнительные сведения см. в статье [Применение обновлений администратора](applying-administrator-updates.md). 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Шаг 4. (Необязательно.) Использование средств Visual Studio для проверки установки

Мы предлагаем несколько средств, предназначенных для [обнаружения установленных экземпляров Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true) на клиентских компьютерах и управления ими.

## <a name="advanced-configuration"></a>Расширенная конфигурация

По умолчанию установка Visual Studio позволяет включать в поиск Bing пользовательские типы из списка ошибок F1 и ссылок на код. Можно настроить Visual Studio таким образом, чтобы запретить включение пользовательских типов в механизм поиска. Для этого необходимо изменить значение следующего раздела реестра для политики:

**"PutCustomTypeInBingSearch" DWORD 0**

Этот раздел находится в каталоге *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\* частного куста реестра. Инструкции по открытию куста реестра см. в разделе [Редактирование реестра для экземпляра Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Шаг 1.Скачивание файлов продукта Visual Studio

* [Выберите набор рабочих нагрузок и компонентов](workload-and-component-ids.md?view=vs-2017&preserve-view=true), которые требуется установить.

* [Создайте общую сетевую папку для файлов продукта Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Шаг 2. Создание скрипта установки

* Создайте скрипт установки, который использует [параметры командной строки](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) для управления установкой.

  >[!NOTE]
  > Его можно упростить с помощью [файла ответов](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true). Обязательно создайте файл ответов с параметрами установки по умолчанию.

* Также вы можете [применить ключ корпоративной лицензии](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true) в рамках скрипта установки, чтобы освободить пользователей от дополнительных действия для активации программного обеспечения.

* При необходимости обновите структуру сети для [управления временем и источником обновлений для конечных пользователей](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true).

* При необходимости можно задать политики реестра, влияющие на развертывание Visual Studio, например, место, где установлены некоторые пакеты, используемые совместно с другими версиями или экземплярами, [где кэшируются пакеты](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) или [кэшируются ли пакеты вообще](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true).

* При необходимости задайте групповую политику. Также можно настроить в Visual Studio [отключение отправки отзывов пользователей с отдельных компьютеров](../ide/visual-studio-experience-improvement-program.md).

## <a name="step-3---deploy-updates"></a>Шаг 3. Развертывание обновлений

Примените любую удобную технологию развертывания, чтобы выполнить скрипт на целевых рабочих станциях разработчиков.

* Регулярно [дополняйте расположение сетевой установки последними обновлениями](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) для Visual Studio, повторно выполняя команду из шага 1 для добавления новых компонентов.

  Visual Studio можно обновить с помощью скрипта обновления. Чтобы сделать это, используйте параметр командной строки [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true).

  Обновления Visual Studio можно развернуть из Windows Server Update Services или каталога Центра обновления Майкрософт с помощью таких средств, как System Center Configuration Manager. Дополнительные сведения см. в статье [Применение обновлений администратора](applying-administrator-updates.md).

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Шаг 4. (Необязательно.) Использование средств Visual Studio для проверки установки

Мы предлагаем несколько средств, предназначенных для [обнаружения установленных экземпляров Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) на клиентских компьютерах и управления ими.

## <a name="advanced-configuration"></a>Расширенная конфигурация

По умолчанию установка Visual Studio позволяет включать в поиск Bing пользовательские типы из списка ошибок F1 и ссылок на код. Можно настроить Visual Studio таким образом, чтобы запретить включение пользовательских типов в механизм поиска. Для этого необходимо изменить значение следующего раздела реестра для политики:

**"PutCustomTypeInBingSearch" DWORD 0**

Реестр расположен в каталоге `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` частного куста реестра. Инструкции по открытию куста реестра см. в разделе [Редактирование реестра для экземпляра Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Включение обновлений администратора](enabling-administrator-updates.md)
* [Применение обновлений администратора](applying-administrator-updates.md)
* [Примеры параметров командной строки](command-line-parameter-examples.md)
* [Установка сертификатов, необходимых для установки Visual Studio в автономном режиме](install-certificates-for-visual-studio-offline.md)
* [Импорт или экспорт конфигураций установки](import-export-installation-configurations.md)
* [Архивы установки Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Жизненный цикл и обслуживание продуктов Visual Studio](/visualstudio/releases/2019/servicing/)
* [Параметры синхронной автозагрузки](../extensibility/synchronously-autoloaded-extensions.md)
