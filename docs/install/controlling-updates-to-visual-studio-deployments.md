---
title: Управление обновлением развертываний
description: Узнайте, как изменить расположение, в котором Visual Studio ищет обновления при установке из сети.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: f15281db55381dadbfd3370eb10a04feeab9c3a5
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307574"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Управление обновлением сетевых развертываний Visual Studio

Администраторы предприятий часто создают макеты и размещают их в общих сетевых папках, чтобы затем развертывать их для своих пользователей. На этой странице показано, как правильно настроить параметры сетевого макета.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Определение места, в котором Visual Studio будет искать обновления

**Сценарий 1. Клиент, изначально установленный из макета, но настроенный на получение обновлений из расположения сетевого макета или Интернета.**

По умолчанию Visual Studio продолжает искать обновления в Интернете, даже если установка была изначально развернута из общей сетевой папки. Если обновление доступно в Интернете, пользователь может установить его. Хотя кэш сетевого макета проверяется в первую очередь на наличие обновленных битов продукта, если они не будут найдены, Visual Studio будет искать и скачивать обновленные версии продуктов из Интернета.

**Сценарий 2. Изначально установленный клиент, который должен получать обновления только из сетевого макета**

Если вы хотите управлять тем, где клиент Visual Studio ищет обновления, можно настроить расположение, в котором установщик клиента будет искать обновленные биты продукта. Это полезно, если у клиентского компьютера нет доступа к Интернету и вы хотите, чтобы установка всегда выполнялась только из макета. Лучше убедиться, что этот параметр настроен правильно, прежде чем клиент выполнит первоначальную установку из макета.

1. Создайте автономный макет.

   ```shell
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Скопируйте его в общую сетевую папку, в которой будете его размещать.

   ```shell
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Измените в этом макете файл `response.json`, задав для `channelUri` значение, указывающее на управляемую администратором копию файла channelManifest.json.

   Не забудьте экранировать все символы обратной косой черты в этом значении, как показано в следующем примере:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Теперь пользователи смогут выполнять установку Visual Studio из этой общей папки.

   ```shell
   \\server\share\VS\vs_enterprise.exe
   ```

Когда администратор предприятия решит, что нужно обновить установки пользователей до новой версии Visual Studio, ему нужно [обновить расположение макета](update-a-network-installation-of-visual-studio.md), разместив в нем обновленные файлы, как показано далее.

1. Используйте команду, аналогичную следующей:

   ```shell
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Убедитесь, что файл `response.json` в обновленном макете содержит все внесенные изменения, в частности изменение channelUri:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

Все существующие копии Visual Studio, установленные из этого макета, ищут обновления в `\\server\share\VS\ChannelManifest.json`. Если файл channelManifest.json новее, чем существующий в пользовательской установке, Visual Studio уведомит пользователя о наличии доступного обновления.

В ходе любого обновления, инициированного клиентом, автоматически устанавливается обновленная версия Visual Studio непосредственно из макета.

**Сценарий 3. Изначально установленный из Интернета клиент, который должен получать обновления только из сетевого макета**

В некоторых случаях на клиентском компьютере может быть установлена среда Visual Studio из Интернета, но администратор хочет, чтобы все будущие обновления поступали из управляемого макета. Единственный поддерживаемый способ — создать сетевой макет с требуемой версией продукта, а затем на клиентском компьютере запустить начальный загрузчик _из расположения макета_ (например, `\\server\share\vs_enterprise.exe`). В идеале исходная установка клиента должна выполняться с помощью начального загрузчика из сетевого макета с правильно настроенным значением channelUri, но запуск обновленного загрузчика из расположения сетевого макета также поддерживается. Одно из этих действий реализует на клиентском компьютере подключение к определенному расположению макета. Единственная оговорка в этом сценарии заключается в том, что значение channelUri в файле `response.json` макета должно совпадать со значением channelUri, определенным на клиентском компьютере при первоначальной установке. Скорее всего, это значение было изначально установлено с учетом [канала выпусков](https://aka.ms/vs/16/release/channel).

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Управление уведомлениями в интегрированной среде разработки Visual Studio

::: moniker range="vs-2017"

Как описано выше, среда разработки Visual Studio проверяет расположение, из которого она была установлена (например, общую сетевую папку или Интернет), чтобы определить наличие доступных обновлений. Когда Visual Studio обнаруживает обновление, она уведомляет пользователя с помощью флага уведомления в правом верхнем углу окна.

   ![Флаг уведомления о наличии обновлений](media/notification-flag.png)

::: moniker-end

::: moniker range=">=vs-2019"

Как описано выше, среда разработки Visual Studio проверяет расположение, из которого она была установлена (например, общую сетевую папку или Интернет), чтобы определить наличие доступных обновлений. Когда Visual Studio обнаруживает обновление, она уведомляет пользователя с помощью значка уведомления в правом нижнем углу окна.

   ![Значок уведомления в IDE Visual Studio](media/vs-2019/notification-bar.png "Значок уведомления в IDE Visual Studio")

::: moniker-end

Если вы не хотите, чтобы пользователи получали уведомления об обновлениях, эти уведомления можно отключить. (Например, может потребоваться отключить уведомления при доставке обновлений через централизованный механизм распространения программного обеспечения.)

::: moniker range="vs-2017"

Так как Visual Studio 2017 [сохраняет параметры в частном реестре](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), вы не можете изменить реестр обычным способом. Но Visual Studio предоставляет служебную программу `vsregedit.exe`, с помощью которой вы можете изменить параметры Visual Studio. Чтобы отключить уведомления, выполните следующую команду:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Так как Visual Studio 2019 [сохраняет параметры в частном реестре](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), вы не можете изменить реестр обычным способом. Но Visual Studio предоставляет служебную программу `vsregedit.exe`, с помощью которой вы можете изменить параметры Visual Studio. Чтобы отключить уведомления, выполните следующую команду:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range=">=vs-2022"

Так как Visual Studio 2022 [сохраняет параметры в частном реестре](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), вы не можете изменить реестр обычным способом. Но Visual Studio предоставляет служебную программу `vsregedit.exe`, с помощью которой вы можете изменить параметры Visual Studio. Чтобы отключить уведомления, выполните следующую команду:

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Не забудьте заменить каталог в соответствии с установленным экземпляром, который нужно изменить.)

> [!TIP]
> Используйте [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) , чтобы найти определенный экземпляр Visual Studio на клиентской рабочей станции.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Включение обновлений администратора](enabling-administrator-updates.md)
* [Применение обновлений администратора](applying-administrator-updates.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Средства для управления экземплярами Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Жизненный цикл и обслуживание продуктов Visual Studio](/visualstudio/releases/2019/servicing/)
