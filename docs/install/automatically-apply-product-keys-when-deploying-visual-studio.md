---
title: Автоматическое применение ключей продуктов
description: Сведения о применении ключей продуктов программными средствами при развертывании Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a78da89d8e8ce4251bc9288270628bfe784eca7a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307724"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Автоматическое применение ключей продуктов при развертывании Visual Studio

Ключ продукта можно применить программным способом в составе сценария, используемого для автоматизации развертывания Visual Studio. Ключи продуктов могут быть заданы на устройстве программно во время установки Visual Studio или после ее завершения.

::: moniker range=">=vs-2022"

> [!IMPORTANT]
> Visual Studio 2022 в настоящее время находится на этапе предварительной версии. В период действия предварительной версии Visual Studio 2022 доступна в рамках оценочной лицензии, которая не требует применения ключа продукта.

::: moniker-end

::: moniker range="vs-2017"

## <a name="apply-the-license-after-installation"></a>Применение лицензии после установки

Чтобы активировать установленную версию Visual Studio с помощью ключа продукта, выполните на конечных компьютерах служебную программу `StorePID.exe` в автоматическом режиме. `StorePID.exe` — это служебная программа, которая устанавливается вместе с Visual Studio 2017 в следующем расположении по умолчанию:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE
```

 Запустите `StorePID.exe` с повышенными привилегиями, используя агент System Center или командную строку с повышенными привилегиями. Введите ключ продукта и код продукта Майкрософт (MPC).

>[!IMPORTANT]
> В ключе продукта необходимо указывать дефисы.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2019"

## <a name="apply-the-license-after-installation"></a>Применение лицензии после установки

Чтобы активировать установленную версию Visual Studio с помощью ключа продукта, выполните на конечных компьютерах служебную программу `StorePID.exe` в автоматическом режиме. `StorePID.exe` — это служебная программа, которая устанавливается вместе с Visual Studio 2019 в следующем расположении по умолчанию:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE
```

 Запустите `StorePID.exe` с повышенными привилегиями, используя агент System Center или командную строку с повышенными привилегиями. Введите ключ продукта и код продукта Майкрософт (MPC).

>[!IMPORTANT]
> В ключе продукта необходимо указывать дефисы.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2017"

В следующем примере показано использование командной строки для применения лицензии к Visual Studio 2017 Enterprise, для которой MPC имеет значение 08860, с помощью ключа продукта `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, при условии, что установка выполнена в расположение по умолчанию:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

В следующем примере показано использование командной строки для применения лицензии Visual Studio 2019 Enterprise (MPC 09260, ключ продукта `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`) при условии, что установка выполнена в расположении по умолчанию:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 В следующей таблице перечислены коды MPC для каждого выпуска Visual Studio:

| Visual Studio 2013                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Visual Studio 2013                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

::: moniker range="vs-2017"

Если `StorePID.exe` успешно применен к ключу продукта, для параметра `%ERRORLEVEL%` возвращается значение 0. При обнаружении ошибок возвращается один из следующих кодов в зависимости от состояния ошибки:

| Ошибка                     | Код |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> При запуске виртуального экземпляра Visual Studio должны быть также виртуализированы локальная папка AppData и реестр. Чтобы устранить неполадки виртуальных экземпляров, выполните `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe`.  

::: moniker-end

::: moniker range="vs-2019"

Если `StorePID.exe` успешно применен к ключу продукта, для параметра `%ERRORLEVEL%` возвращается значение 0. При обнаружении ошибок возвращается один из следующих кодов в зависимости от состояния ошибки:

| Ошибка                     | Код |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> При запуске виртуального экземпляра Visual Studio должны быть также виртуализированы локальная папка AppData и реестр. Чтобы устранить неполадки виртуальных экземпляров, выполните `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe`.  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](../install/install-visual-studio.md)
* [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)