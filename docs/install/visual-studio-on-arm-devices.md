---
title: Visual Studio на устройствах ARM
description: Рекомендации по использованию Visual Studio на устройствах с процессорами на базе ARM.
ms.date: 09/10/2020
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 31fb209a3f19c052c19e98691b8643bb098887ee
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295810"
---
# <a name="visual-studio-on-arm-powered-devices"></a>Visual Studio на устройствах ARM

> [!IMPORTANT]
> Visual Studio поддерживается только на устройствах с процессорами x86 или AMD64/x64.

Visual Studio разработана для процессоров, использующих архитектуру x86. Версии Visual Studio для процессоров на базе ARM не существует. Однако ОС Windows обеспечивает эмуляцию [x86 на ARM](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation), которую может запускать Visual Studio. Запуск Visual Studio на процессоре ARM с эмуляцией x86 значительно снижает производительность Visual Studio. Некоторые функции Visual Studio не будут работать в этом сценарии. Поэтому мы не рекомендуем запускать Visual Studio на устройствах, использующих процессоры на базе ARM. Вместо этого рекомендуется использовать удаленные целевые устройства ARM.

## <a name="remote-targeting-arm-devices"></a>Удаленные целевые устройства ARM
Для оптимальной работы мы рекомендуем использовать Visual Studio на отдельном компьютере с архитектурой x86, а также функции удаленного развертывания и отладки в Visual Studio для ориентации на устройство на основе ARM. Сведения об отладке универсальных приложений Windows, установленных на устройстве, см. в документации по [отладке установленного пакета приложения](../debugger/debug-installed-app-package.md). Сведения о развертывании нового приложения см. в статье об [удаленном запуске приложения Магазина Windows](../debugger/run-windows-store-apps-on-a-remote-machine.md). Сведения о других типах приложений см. в документации по [удаленной отладке](../debugger/remote-debugging.md).

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>Советы по запуску Visual Studio на устройствах ARM

### <a name="use-only-when-needed"></a>Используйте только при необходимости
Оптимизируйте свое время, используя Visual Studio для работы с ARM только когда это необходимо. Производительность на любом устройстве с поддержкой ARM будет низкой, и, скорее всего, она будет неприемлемой для повседневного использования.

### <a name="install-time"></a>Время установки
Учитывайте, что Visual Studio будет дольше устанавливаться и время от времени приостанавливать работу или требовать перезагрузки.
 
### <a name="remote-tools"></a>Удаленные средства
Чтобы выполнить отладку приложения, работающего на удаленном устройстве, необходимо [загрузить и установить инструменты удаленной отладки](../debugger/remote-debugging.md#download-and-install-the-remote-tools) для ARM.

### <a name="start-debugging-f5"></a>Начать отладку (F5)
Не все проекты Visual Studio настроены для локального запуска при запуске отладки (**F5**) с устройства ARM. Возможно, потребуется настроить Visual Studio для удаленной отладки, даже если приложение выполняется локально. Дополнительные сведения см. в статье [Удаленная отладка](../debugger/remote-debugging.md).

## <a name="we-need-your-help"></a>Нам нужна ваша помощь!
Если вы хотите, чтобы Visual Studio изначально запускался на устройствах ARM, мы будем рады узнать ваше мнение о необходимых сценариях и поддержке. Вы можете связаться с нами, оставив сообщение в [сообществе разработчиков](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html).
