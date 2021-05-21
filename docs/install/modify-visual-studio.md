---
title: Изменение рабочих нагрузок, компонентов и языковых пакетов Visual Studio
titleSuffix: ''
description: Сведения о поэтапном изменении среды Visual Studio.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: contperf-fy21q2
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 30b28af562e5dbaa8c05624f6cc9d531cf652419
ms.sourcegitcommit: 8d3d51042261df603487169a7a008fe8f71404ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2021
ms.locfileid: "109501776"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Изменение рабочих нагрузок, компонентов и языковых пакетов Visual Studio

::: moniker range="vs-2019"

Visual Studio можно легко изменить таким образом, чтобы она включала только необходимые компоненты и в нужное время. Для этого откройте Visual Studio Installer для добавления или удаления рабочих нагрузок и компонентов.

::: moniker-end

::: moniker range="vs-2017"

Мы упростили не только персонализацию Visual Studio в соответствии с выполняемыми задачами, но и настройку самой среды Visual Studio. Для этого откройте новый установщик Visual Studio Installer и внесите нужные изменения.

::: moniker-end

## <a name="prerequisites"></a>Предварительные требования

+ Чтобы установить, обновить или изменить среду Visual Studio, необходимо войти в учетную запись с правами администратора. Дополнительные сведения см. в статье [Разрешения пользователей и Visual Studio](../ide/user-permissions-and-visual-studio.md).

+ В следующих процедурах предполагается, что у вас есть подключение к Интернету. Дополнительные сведения о том, как внести изменения в ранее созданную [автономную установку](create-an-offline-installation-of-visual-studio.md) Visual Studio, см. на страницах [Управление обновлением сетевых развертываний Visual Studio](update-a-network-installation-of-visual-studio.md) и [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md).

## <a name="launch-the-installer"></a>Запустите установщик.

Чтобы внести изменения в установку, необходимо запустить Visual Studio Installer.

::: moniker range="vs-2017"

1. Найдите установщик Visual Studio на своем компьютере.

     Например, на компьютере с Windows 10 нажмите кнопку **Пуск** и прокрутите список до буквы **V**, где расположен пункт **Visual Studio Installer**.

     ![Visual Studio Installer](media/locate-the-visual-studio-installer.png "Поиск Microsoft Visual Studio Installer")

     >[!TIP]
     >На некоторых компьютерах установщик Visual Studio может быть указан под буквой **"M"**  — для **Microsoft Visual Studio**.<br/><br/> Кроме того, Visual Studio Installer можно найти в следующем расположении: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Откройте установщик и выберите команду **Изменить**.

     ![Запуск или изменение Visual Studio](media/modify-visual-studio.png "Изменение Visual Studio 2017")

     > [!IMPORTANT]
     > При наличии ожидающих обновлений кнопка "Изменить" будет находиться в другом месте. Таким образом, вы можете изменить Visual Studio без обновления, если захотите. Нажмите кнопку **Дополнительно**, затем кнопку **Изменить**.
     >
     > ![Обновление или изменение Visual Studio](media/modify-or-update-visual-studio.png "Обновление или изменение Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Найдите **Visual Studio Installer** на своем компьютере.

     В меню "Пуск" Windows можно выполнить поиск по слову "установщик".

     ![Visual Studio Installer](media/vs-2019/visual-studio-installer.png "Поиск установщика Visual Studio Installer")

     > [!NOTE]
     > Кроме того, Visual Studio Installer можно найти в следующем расположении:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Для продолжения работы может потребоваться обновление самого установщика. Если это так, следуйте инструкциям на экране.

1. В установщике найдите установленный у вас выпуск Visual Studio и выберите **Изменить**.

     ![Выбор выпуска Visual Studio для последующего изменения](media/vs-2019/vs-installer-modify.png "Выбор выпуска Visual Studio 2019 для последующего изменения")

     > [!IMPORTANT]
     > При наличии ожидающих обновлений кнопка "Изменить" будет находиться в другом месте. Таким образом, вы можете изменить Visual Studio без обновления, если захотите. Выберите **Дополнительно**, а затем **Изменить**.
     >
     > ![Обновление или изменение Visual Studio](media/vs-2019/modify-update-visual-studio.png "Обновление или изменение Visual Studio 2019")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>Изменение рабочих нагрузок или отдельных компонентов

::: moniker range="vs-2017"

 [Рабочие нагрузки](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) содержат функции, которые требуются для используемого языка программирования или платформы. С помощью рабочих нагрузок можно изменить среду Visual Studio так, чтобы она поддерживала выполнение нужных задач в любое время.

1. В Visual Studio Installer перейдите на вкладку **Рабочие нагрузки**, а затем выберите или отмените выбор нужных рабочих нагрузок.

   Если вы не хотите использовать рабочие нагрузки для настройки установленного экземпляра Visual Studio, откройте вкладку **Отдельные компоненты**, затем выберите нужные компоненты и следуйте указаниям.

    ![Диалоговое окно установки Visual Studio 2017](media/modify-workloads.png "Выбор рабочей нагрузки в Visual Studio 2019")

1. Выберите, хотите ли вы принять параметр по умолчанию **Установить при скачивании** или параметр **Скачать все и установить**.

    ![Параметры установки Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Выбор установки при скачивании или установки после скачивания")

    Параметр "Скачать все и установить" удобен, если вы хотите сначала загрузить среду, а позже установить ее.

1. Выберите **Изменить**.

1. При необходимости перейдите на вкладку **Рабочие нагрузки**, а затем выберите или отмените выбор нужных рабочих нагрузок.


1. После установки новых рабочих нагрузок выберите команду **Запуск** в Visual Studio Installer, чтобы открыть Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Рабочие нагрузки содержат функции, которые требуются для используемого языка программирования или платформы. С помощью рабочих нагрузок можно изменить среду Visual Studio так, чтобы она поддерживала выполнение нужных задач в любое время.

 > [!TIP]
>Дополнительные сведения о наборах средств и компонентов, необходимых для разработки, см. в разделе [Рабочие нагрузки Visual Studio](https://visualstudio.microsoft.com/vs/#workloads).

1. В Visual Studio Installer перейдите на вкладку **Рабочие нагрузки**, а затем выберите или отмените выбор нужных рабочих нагрузок.

    ![Диалоговое окно установки Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Выбор рабочей нагрузки в Visual Studio 2019")

1. Выберите, хотите ли вы принять параметр по умолчанию **Установить при скачивании** или параметр **Скачать все и установить**.

    ![Параметры установки Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Выбор установки при скачивании или установки после скачивания")

    Параметр "Скачать все и установить" удобен, если вы хотите сначала загрузить среду, а позже установить ее.

1. Выберите **Изменить**.

1. После установки новых рабочих нагрузок выберите команду **Запуск** в Visual Studio Installer, чтобы открыть Visual Studio.

::: moniker-end


>[!TIP]
> Сведения о компоненте SQL Server Data Tools (SSDT) см. в разделе [Скачивание и установка SSDT для Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true).

## <a name="modify-language-packs"></a>Измените языковой пакет

По умолчанию при первом запуске установщик использует язык операционной системы. Однако вы можете изменить язык при необходимости. 

Для этого сделайте следующее:
1. Перейдите на вкладку **Языковые пакеты** в Visual Studio Installer.
2. Выберите нужный язык.
3. Следуйте инструкциям.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также раздел

* [Список идентификаторов рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
* [Обновление Visual Studio](update-visual-studio.md)
* [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Удаление Visual Studio](uninstall-visual-studio.md)
