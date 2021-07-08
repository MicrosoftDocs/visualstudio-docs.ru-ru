---
title: Средства для обнаружения экземпляров Visual Studio и управления ими
titleSuffix: ''
description: Сведения о средствах, с помощью которых можно обнаруживать экземпляры Visual Studio, установленные на клиентских компьютерах, и управлять ими.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 914449fe1db792614af1f9ed22464cb9fdb91481
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306895"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Средства для обнаружения экземпляров Visual Studio и управления ими

Существует ряд средств, с помощью которых можно обнаруживать и администрировать экземпляры Visual Studio, установленные на клиентских компьютерах.

## <a name="detecting-existing-visual-studio-instances"></a>Обнаружение существующих экземпляров Visual Studio

Следующие средства и служебные программы помогут вам обнаруживать и администрировать экземпляры Visual Studio, установленные на клиентских компьютерах:

* [**vswhere**](https://github.com/microsoft/vswhere) — исполняемый файл, входящий в состав Visual Studio и доступный для отдельного распространения, который поможет вам найти расположение всех экземпляров Visual Studio на конкретном компьютере.
* [**VSSetup.PowerShell**](https://github.com/microsoft/vssetup.powershell) — скрипты PowerShell, которые позволяют определить установленные экземпляры Visual Studio с помощью API конфигурации установки.
* [**VS-Setup-Samples**](https://github.com/microsoft/vs-setup-samples) — примеры на языках C# и C++, демонстрирующие применение API конфигурации установки для запрашивания существующей установки.
* [**Инструментарий управления Windows (WMI)**](/windows/win32/wmisdk/wmi-start-page) — сведения об экземпляре Visual Studio можно запросить с помощью класса MSFT_VSInstance в Visual Studio.
* [**API конфигурации установки**](<xref:Microsoft.VisualStudio.Setup.Configuration>) — реализует интерфейсы для разработчиков, которые хотят создавать собственные служебные программы для опроса экземпляров Visual Studio.
* [**Инвентаризация программного обеспечения Microsoft Endpoint Configuration Manager**](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) — может использоваться для сбора сведений об экземплярах Visual Studio на клиентских устройствах.

## <a name="using-vswhereexe"></a>С помощью vswhere.exe

`vswhere.exe` по умолчанию входит в состав Visual Studio 2017 и более поздних версий, а также предлагается для скачивания на [странице выпусков vswhere](https://github.com/Microsoft/vswhere/releases). Используйте `vswhere -?`, чтобы получить информацию об этом средстве. Например, эта команда выводит в формате JSON полный список выпусков Visual Studio, включая предыдущие и предварительные версии продукта:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Использование инструментария управления Windows (WMI)

Если на компьютере установлен компонент Visual Studio Client Detector Utility, можно запросить сведения об экземпляре Visual Studio с помощью инструментария WMI. Visual Studio Client Detector Utility устанавливается по умолчанию при установке всех обновлений Visual Studio 2017, Visual Studio 2019 и Visual Studio 2022, выпущенных начиная с 12 мая 2020 г. Этот компонент также доступен в [каталоге Центра обновления Майкрософт](https://catalog.update.microsoft.com/), если вы хотите установить его отдельно.  Чтобы узнать, как использовать этот компонент для получения сведений об экземпляре Visual Studio, откройте PowerShell с правами администратора на клиентском компьютере и введите следующую команду:

```shell
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Использование Microsoft Endpoint Configuration Manager

Возможности [инвентаризации программного обеспечения Microsoft Endpoint Configuration Manager](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) можно использовать для запрашивания и сбора сведений об экземплярах Visual Studio на клиентских устройствах. Например, следующий запрос вернет отображаемое имя, версию и имя устройства, на котором установлен экземпляр Visual Studio, для всех установленных экземпляров Visual Studio 2017 и 2019:

```WQL
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
```

::: moniker range="vs-2017"

> [!TIP]
> Дополнительные сведения об установке Visual Studio 2017 см. в [архивах по установке Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Редактирование реестра для экземпляра Visual Studio

Параметры реестра для Visual Studio сохраняются в частном расположении, что позволяет устанавливать параллельно несколько экземпляров одной версии Visual Studio на одном компьютере.

Поскольку эти записи не хранятся в глобальном реестре, для изменения этих параметров с помощью редактора реестра используется отдельная процедура.

1. Если открыт любой экземпляр Visual Studio, закройте его.

1. Запустите среду `regedit.exe`.

1. Выберите узел `HKEY_LOCAL_MACHINE`.

1. В главном меню редактора реестра выберите пункты **Файл** > **Загрузить куст...** и файл частного реестра из папки **AppData\Local**. Пример:

   ```shell
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` обозначает экземпляр Visual Studio, который вы хотите просмотреть.

Вам будет предложено предоставить имя используемого изолированного куста. После этого вы сможете просматривать параметры реестра, хранящиеся в созданном изолированном кусте.

> [!IMPORTANT]
> Прежде чем возвращаться к работе в Visual Studio, необходимо выгрузить созданный вами изолированный куст. Для этого выберите **Файл** > **Выгрузить куст** в главном меню редактора реестра. (Если этого не сделать, файл останется заблокированным и Visual Studio не сможет запуститься.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Руководство администратора Visual Studio](../install/visual-studio-administrator-guide.md)
