---
title: Создание автономной установки
description: Узнайте, как установить Visual Studio в автономном режиме в случае ненадежного подключения к Интернету или низкой пропускной способности.
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c37ccb9c6dce1f6b20b8ade317e8135462c65011
ms.sourcegitcommit: 367a2d9df789aa617abaa09b0cd0a18db7357d0c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107800871"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Создание автономной установки Visual Studio

::: moniker range="vs-2017"

Visual Studio 2017 поддерживает различные конфигурации сети и компьютера. Хотя мы рекомендуем использовать [веб-установщик Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads)&mdash; — небольшой файл, в который входят все последние исправления и функции&mdash;, мы понимаем, что это не всегда возможно.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 поддерживает различные конфигурации сети и компьютера. Хотя мы рекомендуем использовать [веб-установщик Visual Studio](https://visualstudio.microsoft.com/downloads)&mdash; — небольшой файл, в который входят все последние исправления и функции&mdash;, мы понимаем, что это не всегда возможно.

::: moniker-end

Например, у вас может быть ненадежное подключение к Интернету или низкая пропускная способность. В этом случае у вас есть несколько вариантов: вы можете воспользоваться новым компонентом Download all, then install (Скачать все и установить), чтобы загрузить необходимые для установки файлы, или создать локальный кэш файлов с помощью командной строки.

> [!NOTE]
> Если вы являетесь администратором предприятия и вам нужно развернуть Visual Studio в сети клиентских рабочих станций, которые отделены от Интернета брандмауэром, см. руководства по [созданию сетевой установки Visual Studio](../install/create-a-network-installation-of-visual-studio.md) и [установке сертификатов, требуемых для автономной установки Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Использование компонента Download all, then install (Скачать все и установить)

::: moniker range="vs-2017"

[**Новые возможности в версии 15.8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): скачав веб-установщик, выберите в Visual Studio Installer вариант **Скачать все и установить**. После этого продолжите установку.

   ![Параметр Download all, then install (Скачать все и установить)](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

загрузив веб-установщик, выберите в установщике Visual Studio Installer новый компонент **Download all, then install** (Скачать все и установить). После этого продолжите установку.

   ![Параметр Download all, then install (Скачать все и установить)](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Параметр Download all, then install (Скачать все и установить) позволяет скачать Visual Studio в виде отдельного установщика для компьютера, на который он скачивается. Это позволяет безопасно отключится от Интернета перед установкой Visual Studio.

> [!IMPORTANT]
> Не используйте этот параметр, чтобы создать автономный кэш для передачи на другой компьютер. Он не предназначен для этого. <br><br>Если вы хотите создать автономный кэш на локальном компьютере, который затем можно использовать для установки Visual Studio, см. раздел [Использование командной строки для создания локального кэша](#use-the-command-line-to-create-a-local-cache) ниже.  На странице [Создание сетевой установки Visual Studio](../install/create-a-network-installation-of-visual-studio.md) также содержатся сведения о том, как создать кэш в сети.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Использование командной строки для создания локального кэша
::: moniker range="vs-2017"

Скачав небольшой загрузчик, откройте командную строку, чтобы создать локальный кэш. После этого установите Visual Studio из локального кэша. (При этом ISO-файлы, доступные для предыдущих версий, будут заменены.) 

::: moniker-end

::: moniker range="vs-2019"

Скачав небольшой файл начального загрузчика, откройте командную строку, чтобы создать локальный кэш. После этого установите Visual Studio из локального кэша.

::: moniker-end

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Шаг 1. Скачивание начального загрузчика Visual Studio

Для выполнения этого этапа необходимо подключение к Интернету.

::: moniker range="vs-2017"

Чтобы получить последнюю версию начального загрузчика для Visual Studio 2017 версии 15.9, перейдите на страницу с [предыдущими версиями Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) и скачайте один из следующих файлов начального загрузчика: 

| Выпуск | имя_файла |
|-------------|-----------------------|
|Visual Studio Professional 2017, версия 15.9 | vs_professional.exe |
|Visual Studio Enterprise 2017, версия 15.9 | vs_enterprise.exe |
|Visual Studio Build Tools 2017, версия 15.9  | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Начните со скачивания начального загрузчика Visual Studio 2019 с [веб-страницы загрузки Visual Studio](https://visualstudio.microsoft.com/downloads) или страницы с [выпусками Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) для выбранной версии и выпуска Visual Studio. Файл установки или &mdash;начальный загрузчик&mdash; должны иметь одно из перечисленных ниже имен или похожее:

| Выпуск                    | Файл                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio 2019 Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Если вы ранее скачали файл начального загрузчика и хотите проверить его версию, сделайте следующее. В Windows откройте проводник, щелкните правой кнопкой мыши файл начального загрузчика, выберите **Свойства**, перейдите на вкладку **Подробно**, а затем найдите номер в строке **Версия продукта**. Чтобы сопоставить этот номер с выпуском Visual Studio, перейдите на страницу [Номера сборки и даты выпуска Visual Studio](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Если вы ранее скачали файл начального загрузчика и хотите проверить его версию, вот как это сделать. В Windows откройте проводник, щелкните правой кнопкой мыши файл начального загрузчика, выберите **Свойства**, перейдите на вкладку **Подробно**, а затем найдите номер в строке **Версия продукта**. Чтобы сопоставить этот номер с выпуском Visual Studio, перейдите на страницу [Выпуски Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history).

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>Шаг 2. Создание локального кэша установки

Для выполнения этого этапа необходимо подключение к Интернету.

Откройте командную строку и используйте параметры начального загрузчика, как указано в статье [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md), чтобы создать локальный кэш установки. Распространенные примеры использования начального загрузчика Enterprise показаны ниже и на странице с [примерами параметров командной строки](command-line-parameter-examples.md). Вы можете установить язык, отличающийся от английского, изменив `en-US` на языковой стандарт из [списка языковых стандартов](#list-of-language-locales). Для дальнейшей настройки кэша можно использовать [список компонентов и рабочих нагрузок](workload-and-component-ids.md).

> [!TIP]
> Чтобы предотвратить ошибку, убедитесь, что путь к полной установке содержит менее 80 символов.

- Для разработки веб-приложений .NET или классических приложений .NET выполните следующую команду:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Для разработки классических приложений .NET и решений Office выполните следующую команду:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Для разработки классических приложений C++ выполните следующую команду:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Чтобы создать локальный макет с поддержкой только английского языка и полным набором компонентов (это будет довольно долго &mdash; компонентов у нас _очень много_), выполните следующую команду:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Для установки полного макета Visual Studio потребуется как минимум 35 ГБ дискового пространства. Дополнительные сведения см. в статье [Требования к системе](/visualstudio/productinfo/vs2017-system-requirements-vs/). 

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Для установки полного макета Visual Studio потребуется как минимум 35 ГБ дискового пространства. Дополнительные сведения см. в статье [Требования к системе](/visualstudio/releases/2019/system-requirements/).

::: moniker-end


### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Шаг 3. Установка Visual Studio из локального кэша
При установке Visual Studio из локального кэша установщик Visual Studio использует локальные кэшированные версии файлов. Но если во время установки вы выберете компоненты, которые отсутствуют в кэше, установщик Visual Studio попытается скачать их из Интернета. Чтобы установить только те файлы, которые вы уже скачали, все [параметры командной строки](use-command-line-parameters-to-install-visual-studio.md) должны совпадать с теми, которые вы использовали для создания кэша макета. 

Предположим, что вы создали кэш локальной установки с помощью следующей команды:

```cmd
vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

В этом случае используйте для запуска установки следующую команду.

```cmd
c:\vslayout\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!IMPORTANT]
> Если вы используете Visual Studio Community, необходимо активировать его, войдя в продукт в течение 30 дней после установки. Для активации требуется подключение к Интернету.

> [!NOTE]
> Если возникнет ошибка с сообщением о недопустимой сигнатуре, [установите обновленные сертификаты](install-certificates-for-visual-studio-offline.md). Откройте папку "Сертификаты" в автономном кэше. Дважды щелкните каждый файл сертификата и выполните инструкции в мастере диспетчера сертификатов. Если он предложит ввести пароль, оставьте это поле пустым.

::: moniker range="vs-2019"
> [!TIP]
> Если при установке в автономном режиме появляется сообщение об ошибке "Невозможно найти продукт, соответствующий следующим параметрам", убедитесь, что вы используете параметр — `--noweb` с версией 16.3.5 или более поздней.

::: moniker-end

### <a name="list-of-language-locales"></a>Список языковых стандартов

| **Язык-языковой стандарт** | **Язык** |
| ----------------------- | --------------- |
| cs-CZ | Чешский |
| de-DE | Немецкий |
| en-US | Английский |
| es-ES | Испанский |
| fr-FR | Французский |
| it-IT | Итальянский |
| ja-JP | Японский |
| ko-KR | Корейский |
| pl-PL | Польский |
| pt-BR | Португальский (Бразилия) |
| ru-RU | Русский |
| tr-TR | Турецкий |
| zh-CN | Китайский (упрощенное письмо) |
| zh-TW | Китайский (традиционное письмо) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также раздел

- [Создание сетевой установки Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Установка сертификатов, необходимых для установки Visual Studio в автономном режиме](../install/install-certificates-for-visual-studio-offline.md)
- [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
