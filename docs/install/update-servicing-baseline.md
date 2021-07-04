---
title: Обновление Visual Studio во время обслуживания
description: Узнайте, как обновить Visual Studio, оставаясь на базовой версии.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: '>=vs-2019'
ms.openlocfilehash: 03a192657a46c2db15cb2d1121735905f06da478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306674"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Обновление Visual Studio во время обслуживания

Мы часто обновляем Visual Studio во время жизненного цикла продукта. Существует два типа обновлений:

* **Дополнительные обновления выпуска**&mdash;например, 16.0–16.1,&mdash; включающие новые функции и компоненты.  
* **Служебные обновления** — например, 16.0.4–16.0.5, — включающие только целевые исправления для критических проблем.

Администраторы предприятий могут не выполнять промежуточные обновления своих клиентов. Служебные обновления продолжают выходить в течение года после выпуска очередной базовой версии.

Служебные обновления позволяют разработчикам и администраторам лучше адаптироваться к новым функциям, исправлениям ошибок и компонентам, добавляемым при промежуточных обновлениях. 16.0.x — это первая базовая версия. Дополнительные сведения см. в разделе [Варианты поддержки для клиентов уровня Enterprise и Professional](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Как установить базовую версию

Чтобы приступить к использованию базовой версии, скачайте начальный загрузчик Visual Studio Installer определенной версии Visual Studio на сайте [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). В загрузчиках приводятся ссылки на конфигурации, рабочие нагрузки и компоненты для определенной версии Visual Studio.

> [!NOTE]
> Обратите внимание, что доступны как загрузчики определенной версии, так и стандартные загрузчики. Стандартные загрузчики настроены на использование последней доступной версии Visual Studio. В имени файла стандартного загрузчика, доступного для скачивания на My.VisualStudio.com, есть номер (например, vs_enterprise__123456789-123456789.exe).

Во время установки администраторам необходимо настроить свои клиенты так, чтобы не выполнялось обновление клиентов до последней версии. Для этого можно использовать следующие способы.
- [Изменить параметр `channelUri` в файле конфигурации ответов](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network), чтобы использовать манифест канала из макета или локальной папки.
- [Изменить channelUri при установке с помощью командной строки](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet), чтобы использовать несуществующий файл.
- [Настроить политики в системе клиента на отключение обновлений](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating), чтобы предотвратить самостоятельное обновление клиентов.

### <a name="install-a-servicing-baseline-on-a-network"></a>Сетевая установка базовой версии

Администраторам, использующим макет сетевой установки, нужно изменить значение `channelUri` в файле *response.json* макета, чтобы использовать файл *channelmanifest.json*, который находится в той же папке. Инструкции см. в статье [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md). Если изменить значение `channelUri`, клиенты будут искать обновления в расположении макета.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Установка базовой версии по Интернету

При установке по Интернету добавьте `--channelUri` с несуществующим манифестом канала с помощью командной строки при запуске установки. Это приведет к отключению в Visual Studio обновления до последней доступной версии. Ниже приведен пример:

```shell
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Отключение обновления клиентов с помощью параметров политики

Другой вариант управления обновлениями клиента заключается в [отключении уведомлений об обновлениях](controlling-updates-to-visual-studio-deployments.md). Используйте этот вариант, если значение channelUri не было изменено при установке. Это не позволит клиенту получать ссылки на последнюю доступную версию. При этом все равно требуется начальный загрузчик определенной версии для обновления клиента до определенной версии.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Как оставаться на базовой версии

При выходе обновления для базовой версии на сайте [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) публикуются файлы загрузчика определенной версии для служебного обновления.

При развертывании с помощью макета сетевой установки администратору потребуется обновить [расположение макета](update-a-network-installation-of-visual-studio.md). Клиенты, установленные из расположения, получат уведомления об обновлении. Если требуется развернуть обновление в клиентах, следуйте [этим инструкциям](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines). При изменении файла response.json для обновления не добавляйте дополнительные рабочие нагрузки, компоненты или языки. Управление этими параметрами должно выполняться как "модифицирующее" развертывание после обновления продукта.

При установке по Интернету запустите в клиенте новый начальный загрузчик определенной версии с параметром `--channelUri`, указывающим на манифест несуществующего канала. Если обновление развертывается в тихом или пассивном режиме, используйте две отдельные команды:

1. Обновите установщик Visual Studio.

    ```shell
    vs_enterprise.exe --quiet --update
    ```

::: moniker range="vs-2019"
 
2. Обновите само приложение Visual Studio.
    ```shell
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

::: moniker-end

::: moniker range=">=vs-2022"

2. Обновите само приложение Visual Studio.
    ```shell
    vs_enterprise.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Средства для обнаружения экземпляров Visual Studio и управления ими](tools-for-managing-visual-studio-instances.md)
* [Как определить параметры в файле ответов](automated-installation-with-response-file.md)
* [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Жизненный цикл и обслуживание продуктов Visual Studio](/visualstudio/releases/2019/servicing/)
