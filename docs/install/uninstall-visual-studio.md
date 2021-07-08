---
title: Удаление Visual Studio
titleSuffix: ''
description: Сведения о поэтапном удалении среды Visual Studio.
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7d34a5be9598682982c3918aafec7725e59d6f92
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306791"
---
# <a name="uninstall-visual-studio"></a>Удаление Visual Studio

На этой странице приведены пошаговые инструкции по удалению Visual Studio, интегрированного набора средств для эффективной работы разработчиков.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Для Visual Studio для Mac см. раздел [Удаление Visual Studio для Mac](/visualstudio/mac/uninstall).

> [!TIP]
> Если у вас возникли проблемы с экземпляром Visual Studio, воспользуйтесь **средством восстановления**. Дополнительные сведения см. в статье [Восстановление Visual Studio](../install/repair-visual-studio.md). 
>
> Если вам требуется изменить расположение каких-либо файлов Visual Studio, это можно сделать, не удаляя текущий экземпляр. Дополнительные сведения см. в статье [Выбор расположения установки в Visual Studio](../install/change-installation-locations.md).
>
> Общие советы по устранению неполадок см. в статье [Устранение неполадок при установке и обновлении Visual Studio](../install/troubleshooting-installation-issues.md).

::: moniker range="vs-2017"

1. Найдите установщик Visual Studio на своем компьютере.

     Например, на компьютере с юбилейным обновлением или более поздней версией Windows 10 нажмите кнопку **Пуск** и прокрутите список до буквы **V**, где расположен пункт **Visual Studio Installer**.

     ![Visual Studio Installer](media/locate-the-visual-studio-installer.png "Поиск Microsoft Visual Studio Installer")

   > [!NOTE]
   > На некоторых компьютерах установщик Visual Studio может быть указан под буквой **"M"**  — для **Microsoft Visual Studio**.<br/><br/> Кроме того, Visual Studio Installer можно найти в следующем расположении: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. В установщике найдите установленный у вас выпуск Visual Studio. Затем выберите **Дополнительно** и **Удалить**.

     ![Удаление Visual Studio 2017](media/uninstall-visual-studio.png "Удаление Visual Studio 2017")

1. Нажмите кнопку **ОК**, чтобы подтвердить действие.

Если в будущем вы захотите снова установить Visual Studio 2017, запустите Visual Studio Installer и выберите **Установить** на экране выбора.

## <a name="uninstall-visual-studio-installer"></a>Удаление установщика Visual Studio

Чтобы полностью удалить все установки Visual Studio 2017 и Visual Studio Installer с компьютера, удалите их в окне "Программы и компоненты".

1. В Windows 10 введите **Программы и компоненты** в поле "Введите текст для поиска".
1. Найдите **Microsoft Visual Studio 2017** (или **Visual Studio 2017**).
1. Выберите **Удалить**.
1. Затем найдите **Microsoft Visual Studio Installer**.
1. Выберите **Удалить**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Найдите **Visual Studio Installer** на своем компьютере.

     В меню "Пуск" Windows можно выполнить поиск по слову "установщик".

     ![Visual Studio Installer](media/vs-2019/visual-studio-installer.png "Поиск установщика Visual Studio Installer")

     > [!NOTE]
     > Кроме того, Visual Studio Installer можно найти в следующем расположении:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Для продолжения работы может потребоваться обновление самого установщика. Если это так, следуйте инструкциям на экране.

1. В установщике найдите установленный у вас выпуск Visual Studio. Затем выберите **Дополнительно** и **Удалить**.

     ![Удаление Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "Удаление Visual Studio 2019")

1. Нажмите кнопку **ОК**, чтобы подтвердить действие.

     ![Подтверждение удаления Visual Studio](media/vs-2019/uninstall-visualstudio-confirm.png "Подтвердите, что хотите удалить Visual Studio 2019")

Если в будущем вы передумаете и захотите снова установить Visual Studio 2019 или 2022, снова запустите Visual Studio Installer, выберите вкладку **Доступно**, выберите выпуск Visual Studio, который вы хотите установить, а затем нажмите **Установка**.

## <a name="uninstall-visual-studio-installer"></a>Удаление установщика Visual Studio

Удалить все установки Visual Studio 2019, Visual Studio 2022 и Visual Studio Installer с компьютера можно в окне "Программы и компоненты".

1. В Windows 10 введите **Программы и компоненты** в поле "Введите текст для поиска".
1. Найдите **Visual Studio 2019** или **Visual Studio 2022**.
1. Выберите **Удалить**.
1. Затем найдите **Microsoft Visual Studio Installer**.
1. Выберите **Удалить**.

::: moniker-end

## <a name="remove-all-files"></a>Удаление всех файлов

Если произошла неустранимая ошибка и вы не можете удалить Visual Studio с помощью предыдущих инструкций, есть вариант, который можно использовать в качестве последнего средства. Дополнительные сведения о том, как полностью удалить все файлы установки Visual Studio и информацию о продукте, см. в [этой статье](remove-visual-studio.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Изменение Visual Studio](modify-visual-studio.md)
* [Обновление Visual Studio](update-visual-studio.md)
