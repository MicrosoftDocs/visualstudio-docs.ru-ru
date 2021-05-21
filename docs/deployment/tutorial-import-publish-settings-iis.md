---
title: Публикация в IIS посредством импорта параметров публикации
description: Создание и импорт профиля публикации для развертывания приложения из Visual Studio в IIS
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aeaaff68ab0abe85838456e8c8b69e2520295689
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729277"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Публикация приложения в IIS посредством импорта параметров публикации в Visual Studio

Вы можете использовать средство **публикации** для импорта параметров публикации, а затем развернуть приложение. В этой статье мы используем параметры публикации для IIS, однако аналогичные действия можно использовать, чтобы импортировать параметры публикации для [Службы приложений Azure](../deployment/tutorial-import-publish-settings-azure.md). В некоторых случаях использование профиля параметров публикации может оказаться быстрее, чем ручная настройка развертывания в IIS для каждой установки Visual Studio.

Эти шаги применимы к приложениям ASP.NET, ASP.NET Core и .NET Core в Visual Studio.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Настройка IIS таким образом, чтобы вы могли создать файл параметров публикации.
> * Создание файла параметров публикации.
> * Импорт файла параметров публикации в Visual Studio.
> * Развертывание приложения в IIS.

Файл параметров публикации ( *\*.publishsettings*) отличается от профиля публикации ( *\*.pubxml*), созданного в Visual Studio. Файл параметров публикации создается IIS или Службой приложений Azure либо может быть создан вручную, после чего его можно импортировать в Visual Studio.

> [!NOTE]
> Если вам нужно только скопировать профиль публикации Visual Studio (файл \*.pubxml) из одной установки Visual Studio в другую, можно найти профиль публикации *\<profilename\>.pubxml* в папке *\\<имя_проекта\>\Properties\PublishProfiles* для управляемых типов проектов. Для веб-сайтов см. в папке *\App_Data*. Профили публикации являются XML-файлами MSBuild.

## <a name="prerequisites"></a>Предварительные требования

::: moniker range=">=vs-2019"

* У вас должны быть установлены решение Visual Studio 2019 и рабочая нагрузка **ASP.NET и разработка веб-приложений**.

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/), если еще не сделали этого.
::: moniker-end

::: moniker range="vs-2017"

* У вас должна быть установлена среда Visual Studio 2017 и рабочая нагрузка **ASP.NET и разработка веб-приложений**.

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/), если еще не сделали этого.
::: moniker-end

* На сервере должна быть запущена ОС Windows Server 2012, Windows Server 2016 или Windows Server 2019, а [роль веб-сервера IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) должна быть правильно установлена (это необходимо для создания файла параметров публикации [ *\*.publishsettings*]). Также требуется установить на сервере ASP.NET 4.5 или ASP.NET Core. Для настройки ASP.NET 4.5 см. раздел [IIS 8.0 — использование ASP.NET 3.5 и ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Для настройки ASP.NET Core см. раздел [Размещение ASP.NET Core в Windows со службами IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Для ASP.NET Core убедитесь, что в пуле приложений настроен параметр использования **Без управляемого кода**, как описывается в статье.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Создание проекта ASP.NET в Visual Studio

1. На компьютере, где выполняется Visual Studio, создайте новый проект.

    Выберите подходящий шаблон. В данном примере выберите **Веб-приложение ASP.NET(.NET Framework)** или (только для C#) **Веб-приложение ASP.NET Core**, а затем нажмите кнопку **ОК**.

    Если вы не видите указанные шаблоны проекта, нажмите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Создание проекта**. Запускается Visual Studio Installer. Установите рабочую нагрузку **ASP.NET и веб-разработка**.

    Выбранный шаблон проекта (ASP.NET или ASP.NET Core) должен соответствовать версии ASP.NET, установленной на веб-сервере.

1. Выберите **MVC** (.NET Framework) или **Веб-приложение (модель-представление-контроллер)** (для .NET Core) и убедитесь, что выбран параметр **Без проверки подлинности**, а затем нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp**, и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **Сборка** > **Собрать решение** (или нажмите сочетание клавиш **CTRL** + **SHIFT** + **B**), чтобы выполнить сборку проекта.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Установка и настройка веб-развертывания в Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Создание файла параметров публикации в IIS в Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Импорт параметров публикации в Visual Studio и развертывание

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

После успешного развертывания приложение должно запускаться автоматически. Если оно не запускается из Visual Studio, запустите его в IIS. Для ASP.NET Core необходимо убедиться, что в поле "Пул приложений" для **DefaultAppPool** задано значение **Без управляемого кода**.

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы создали файл параметров публикации, импортировали его в Visual Studio и развернули приложение ASP.NET в IIS. Рекомендуем вам ознакомиться с общими сведениями о других параметрах публикации в Visual Studio.

> [!div class="nextstepaction"]
> [Первое знакомство с развертыванием](../deployment/deploying-applications-services-and-components.md)
