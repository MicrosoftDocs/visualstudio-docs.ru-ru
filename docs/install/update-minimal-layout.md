---
title: Обновление Visual Studio с использованием минимального автономного макета
description: Узнайте, как обновлять Visual Studio с использованием минимального автономного макета.
ms.date: 05/18/2021
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1c3a6254c3205038be3d56c64de091e659d2bbd5
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306739"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Обновление Visual Studio с использованием минимального автономного макета

Для компьютеров, не подключенных к Интернету, создание минимального макета — самый простой и быстрый способ обновления автономных экземпляров Visual Studio.

Средство минимальных макетов создает макет, специально предназначенный для нужд вашей команды. Администраторы предприятия могут с помощью этого средства создавать макеты обновления для большинства версий Visual Studio 2017 и 2019. В отличие от полного макета Visual Studio минимальный макет содержит только обновленные пакеты, поэтому он всегда меньше и быстрее создается и развертывается. Макет обновления можно еще более уменьшить, указав только нужные языки, рабочие нагрузки и компоненты.

## <a name="how-to-generate-a-minimal-layout"></a>Создание минимального макета

> [!IMPORTANT]
> В этих инструкциях предполагается, что вы уже создавали и использовали макеты. Дополнительные сведения об этом см. на странице [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md).
>
> Дополнительные сведения о жизненном цикле Visual Studio см. на странице [Жизненный цикл и обслуживание продуктов Visual Studio](/visualstudio/releases/2019/servicing).
>

Это средство создает макеты обновления для Visual Studio 2017 (15.9) и более поздних версий. Макет можно развернуть на сетевых или автономных компьютерах для обновления экземпляров Visual Studio. Во время [создания обычного макета](update-a-network-installation-of-visual-studio.md) скачиваются все пакеты для конкретного выпуска. Создание обычного макета требуется для восстановления, удаления и других стандартных операций с экземплярами Visual Studio. Для минимального макета скачиваются только обновленные пакеты, поэтому он меньше и его проще копировать на автономные компьютеры.

### <a name="installing-the-minimal-layout-tool"></a>Установка средства минимальных макетов

 1. Сначала скачайте средство минимальных макетов с [этой страницы](https://aka.ms/vs/installer/minimallayout). При появлении запроса нажмите кнопку **Сохранить**, а затем кнопку **Выполнить**.

     ![Сохранение средства минимальных макетов](media/save-minimal-layout.png)

 2. Затем примите запрос системы контроля учетных записей, нажав кнопку **Да**.

     ![Принятие запроса контроля учетных записей](media/accept-user-account-control.png)

 3. Средство минимальных макетов будет установлено в папке `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout`.

### <a name="how-to-use-the-minimal-layout-tool"></a>Использование средства минимальных макетов

`MinimalLayout.exe` использует перечисленные ниже команды и параметры для создания макета. Для запуска средства требуется по крайней мере одна команда. Средство запускается так:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Команды

* **Предварительная версия.** Используйте эту команду для предварительного просмотра количества скачиваемых пакетов и общего пространства, которое необходимо для создания данного макета.
* **Создание**: Используйте эту команду, чтобы создать минимальный макет для обновления Visual Studio.
* **Regenerate**. Используйте эту команду, чтобы повторно создать макет с помощью существующего файла ответов с минимальным макетом. Для каждого минимального макета создается файл ответов `MinimalLayout.json`, который содержит входные параметры исходного минимального макета. С помощью команды **Regenerate** и файла ответов `MinimalLayout.json` можно повторно создать минимальный макет. Это полезно в том случае, если необходимо создать минимальный макет для нового обновления Visual Studio на основе файла ответов предыдущего минимального макета.

   Для этой команды требуется путь к файлу `MinimalLayout.json` уже созданного макета.

   ```shell
   MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
   ```

* **Verify**. Используйте эту команду, чтобы определить, повреждена ли папка макета.
* **Fix**. Используйте эту команду, чтобы исправить поврежденную папку макета, в том числе заменить в ней все отсутствующие пакеты.

#### <a name="options"></a>Параметры

::: moniker range=">=vs-2019"

| Параметры                                             | Описание                                                                                                                                                                                                                                                                                                                                                                                                                                 | Обязательный/необязательный               | Пример                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt;каталог&gt;                        | Указывает каталог, в котором нужно создать минимальный автономный макет.                                                                                                                                                                                                                                                                                                                                                                          | Обязательное значение                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion &lt;версия&gt;                       | Минимальный автономный макет будет создан для версий начиная с этой.                                                                                                                                                                                                                                                                                                                                                                    | Обязательное значение                        | --baseVersion 16.4.0                                                                                                                                             |
| --targetVersion &lt;версия&gt;                     | Минимальный автономный макет будет создан для версий вплоть до указанной.                                                                                                                                                                                                                                                                                                                                                              | Обязательное значение                        | --targetVersion 16.4.4                                                                                                                                           |
| --languages                                         | Указывает языки, которые нужно включить в минимальный автономный макет. Можно указать несколько значений через пробелы.                                                                                                                                                                                                                                                                                                                    | Обязательное значение                        | --languages en-US fr-FR                                                                                                                                          |
| --productId &lt;один или несколько идентификаторов продуктов&gt;        | Идентификатор(ы) продуктов, из которых будет сформирована минимальная автономная структура, разделенная запятыми. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul> | Обязательное значение                        | --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional                                                               |
| --filePath                                          | Путь к файлу MinimalLayout.json уже созданного макета. Этот параметр используется только с командой Regenerate.                                                                                                                                                                                                                                                                                                          | Требуется для команды Regenerate | --filePath C:\VSLayout\minimalLayout.json <br><br> **Обратите внимание, что команда Regenerate принимает только параметр --filePath.**                                      |
| --add &lt;один или несколько идентификаторов рабочих нагрузок или компонентов&gt; | Указывает один или несколько идентификаторов рабочих нагрузок или компонентов, которые нужно добавить. Дополнительные компоненты можно добавлять глобально с помощью параметра --includeRecommended и (или) <br> –-includeOptional. Можно указать несколько идентификаторов рабочих нагрузок или компонентов через пробелы.                                                                                                                                                                                                   | Необязательный                        | --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio                                        |
| --includeRecommended                                | включает в установку рекомендуемые компоненты для всех устанавливаемых рабочих нагрузок, но не дополнительные компоненты.                                                                                                                                                                                                                                                                                                                                  | Необязательный                        | Для определенной рабочей нагрузки: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Для применения ко всем рабочим нагрузкам: --includeRecommended |
| --includeOptional                                   | Включает в установку дополнительные компоненты для всех устанавливаемых рабочих нагрузок, включая рекомендуемые компоненты.                                                                                                                                                                                                                                                                                                                                | Необязательный                        | Для определенной рабочей нагрузки: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Для применения ко всем рабочим нагрузкам: --includeOptional         |

::: moniker-end

::: moniker range="vs-2017"

| Параметры                                             | Описание                                                                                                                                                                                                                                                                                                                                                                                                                                 | Обязательный/необязательный               | Пример                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt;каталог&gt;                        | Указывает каталог, в котором нужно создать минимальный автономный макет.                                                                                                                                                                                                                                                                                                                                                                          | Обязательное значение                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion &lt;версия&gt;                       | Минимальный автономный макет будет создан для версий начиная с этой.                                                                                                                                                                                                                                                                                                                                                                    | Обязательное значение                        | --baseVersion 15.0.0                                                                                                                                             |
| --targetVersion &lt;версия&gt;                     | Минимальный автономный макет будет создан для версий вплоть до указанной.                                                                                                                                                                                                                                                                                                                                                              | Обязательное значение                        | --targetVersion 15.9.31                                                                                                                                          |
| --languages                                         | Указывает языки, которые нужно включить в минимальный автономный макет. Можно указать несколько значений через пробелы.                                                                                                                                                                                                                                                                                                                    | Обязательное значение                        | --languages en-US fr-FR                                                                                                                                          |
| --productId &lt;один или несколько идентификаторов продуктов&gt;        | Идентификатор(ы) продуктов, из которых будет сформирована минимальная автономная структура, разделенная запятыми. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul> | Обязательное значение                        | --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional                                                               |
| --filePath                                          | Путь к файлу MinimalLayout.json уже созданного макета. Этот параметр используется только с командой Regenerate.                                                                                                                                                                                                                                                                                                          | Требуется для команды Regenerate | --filePath C:\VSLayout\minimalLayout.json <br><br> **Обратите внимание, что команда Regenerate принимает только параметр --filePath.**                                      |
| --add &lt;один или несколько идентификаторов рабочих нагрузок или компонентов&gt; | Указывает один или несколько идентификаторов рабочих нагрузок или компонентов, которые нужно добавить. Дополнительные компоненты можно добавлять глобально с помощью параметра --includeRecommended и (или) <br> –-includeOptional. Можно указать несколько идентификаторов рабочих нагрузок или компонентов через пробелы.                                                                                                                                                                                                   | Необязательный                        | --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio                                        |
| --includeRecommended                                | включает в установку рекомендуемые компоненты для всех устанавливаемых рабочих нагрузок, но не дополнительные компоненты.                                                                                                                                                                                                                                                                                                                                  | Необязательный                        | Для определенной рабочей нагрузки: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Для применения ко всем рабочим нагрузкам: --includeRecommended |
| --includeOptional                                   | Включает в установку дополнительные компоненты для всех устанавливаемых рабочих нагрузок, включая рекомендуемые компоненты.                                                                                                                                                                                                                                                                                                                                | Необязательный                        | Для определенной рабочей нагрузки: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Для применения ко всем рабочим нагрузкам: --includeOptional         |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Создание минимального макета

> [!IMPORTANT]
> В этих инструкциях предполагается, что макет сетевой установки уже создан. Дополнительные сведения см. на странице [Создание сетевой установки Visual Studio](create-a-network-installation-of-visual-studio.md).

Создайте минимальный макет для указанного диапазона версий с помощью команды **generate**. Необходимо также знать идентификатор продукта, языки и требуемые рабочие нагрузки. Этот минимальный макет обновит все экземпляры Visual Studio начиная с базовой версии до целевой версии включительно.

Перед созданием макета можно определить общий размер скачиваемых данных и число включаемых пакетов с помощью команды **preview**. Эта команда принимает те же параметры, что и команда **generate**, а сведения выводятся в консоли.

Рассмотрим несколько примеров предварительного просмотра, создания и повторного создания минимального макета.

::: moniker range=">=vs-2019"

* Ниже приведен пример предварительного просмотра макета для версий Visual Studio Enterprise с 16.4.0 по 16.4.4 только для английского языка.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Ниже показано, как создать этот же макет с одной рабочей нагрузкой.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* Теперь повторно создадим минимальный автономный макет с помощью существующего файла ответов.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

Еще несколько примеров с использованием команды **generate**:

* Ниже показано добавление дополнительной рабочей нагрузки и включение только рекомендуемых пакетов.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Можно также создать минимальный автономный макет, поддерживающий несколько продуктов.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Наконец, так можно включить несколько языков в минимальный макет.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

::: moniker range="vs-2017"

* Ниже приведен пример предварительного просмотра макета для версий Visual Studio Enterprise с 15.0.0 по 15.9.31 только для английского языка.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Ниже показано, как создать этот же макет с одной рабочей нагрузкой.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* Теперь повторно создадим минимальный автономный макет с помощью существующего файла ответов.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

Еще несколько примеров с использованием команды **generate**:

* Ниже показано добавление дополнительной рабочей нагрузки и включение только рекомендуемых пакетов.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Можно также создать минимальный автономный макет, поддерживающий несколько продуктов.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Наконец, так можно включить несколько языков в минимальный макет.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Обслуживание минимального макета

Для обслуживания минимального макета после его создания используйте команды **verify** и **fix**. Команда **verify** определяет наличие поврежденных или отсутствующих пакетов в минимальном макете. Если после выполнения команды **verify** были обнаружены проблемы, используйте команду **fix**, чтобы исправить поврежденные пакеты или добавить отсутствующие.

* Так можно проверить, есть ли в макете поврежденные или отсутствующие пакеты:

  ```shell
  MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
  ```

* Исправить макет можно так:

  ```shell
  MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
  ```

>[!NOTE]
> Этот макет нельзя использовать для восстановления установки Visual Studio. Сведения об исправлении существующего экземпляра Visual Studio см. в статье [Восстановление Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Использование минимального автономного макета для обновления существующей установки Visual Studio

После создания минимального макета можно скопировать всю его папку на клиентский компьютер. Это необходимо, если у компьютера нет доступа к исходному расположению папки минимального макета.

Перейдите в папку и определите имя начального загрузчика. Имя начального загрузчика зависит от значения ProductId, указанного при создании минимального макета. Распространенные варианты приведены в таблице ниже.

| Значение ProductId                             | имя приложения;    |
|---------------------------------------------|---------------------|
| Microsoft.VisualStudio.Product.Enterprise   | vs_enterprise.exe   |
| Microsoft.VisualStudio.Product.Professional | vs_professional.exe |
| Microsoft.VisualStudio.Product.BuildTools   | vs_buildtools.exe   |

Обновление применяется к экземпляру Visual Studio в два шага. Сначала обновите Visual Studio Installer, а затем саму среду Visual Studio.

::: moniker range="vs-2017"

1. **Обновление Visual Studio Installer**

    Выполните приведенную ниже команду, подставив при необходимости правильное имя начального загрузчика вместо `vs_enterprise.exe`.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Обновление приложения Visual Studio**

    Чтобы обновить Visual Studio, необходимо указать путь установки экземпляра Visual Studio, который следует обновить. Если установлено несколько экземпляров Visual Studio, каждый из них необходимо обновить отдельно. Мы настоятельно рекомендуем указать параметр `–noWeb` с командой update, чтобы предотвратить установку компонентов, которые не входят в минимальный макет. Это позволит избежать перевода Visual Studio в непригодное для использования состояние.

    Выполните приведенную ниже команду, подставив нужное значение для параметра командной строки installPath. Кроме того, используйте соответствующее имя начального загрузчика.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

::: moniker-end

::: moniker range="vs-2019"

1. **Обновление Visual Studio Installer**

    Выполните приведенную ниже команду, подставив при необходимости правильное имя начального загрузчика вместо `vs_enterprise.exe`.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Обновление приложения Visual Studio**

    Чтобы обновить Visual Studio, необходимо указать путь установки экземпляра Visual Studio, который следует обновить. Если установлено несколько экземпляров Visual Studio, каждый из них необходимо обновить отдельно. Мы настоятельно рекомендуем указать параметр `–noWeb` с командой update, чтобы предотвратить установку компонентов, которые не входят в минимальный макет. Это позволит избежать перевода Visual Studio в непригодное для использования состояние.

    Выполните приведенную ниже команду, подставив нужное значение для параметра командной строки installPath. Кроме того, используйте соответствующее имя начального загрузчика.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise"
    ```

::: moniker-end

::: moniker range=">=vs-2022"

1. **Обновление Visual Studio Installer**

    Выполните приведенную ниже команду, подставив при необходимости правильное имя начального загрузчика вместо `vs_enterprise.exe`.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Обновление приложения Visual Studio**

    Чтобы обновить Visual Studio, необходимо указать путь установки экземпляра Visual Studio, который следует обновить. Если установлено несколько экземпляров Visual Studio, каждый из них необходимо обновить отдельно. Мы настоятельно рекомендуем указать параметр `–noWeb` с командой update, чтобы предотвратить установку компонентов, которые не входят в минимальный макет. Это позволит избежать перевода Visual Studio в непригодное для использования состояние.

    Выполните приведенную ниже команду, подставив нужное значение для параметра командной строки installPath. Кроме того, используйте соответствующее имя начального загрузчика.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise"
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
