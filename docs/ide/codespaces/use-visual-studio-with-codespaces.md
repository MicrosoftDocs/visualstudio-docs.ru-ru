---
title: Visual Studio с codespace (предварительная версия)
description: Сведения об использовании интегрированной среды разработки Visual Studio с GitHub Codespaces для разработки для Windows.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: add43a5d130d8938193774d50bb643f48ecc3f8c
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104673051"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>Использование Visual Studio с codespace (предварительная версия)

> [!Important] 
> По состоянию на 12 апреля 2021 г. подключение к GitHub Codespaces из Visual Studio 2019 больше не будет поддерживаться, и эта закрытая предварительная версия перестанет использоваться. Мы сосредоточены на разработке интерфейсов для облачных решений внутреннего цикла и VDI, оптимизированных для широкого спектра рабочих нагрузок Visual Studio. Рекомендуем следить за [форумом сообщества разработчиков](https://developercommunity.visualstudio.com/home) Visual Studio, чтобы получать информацию о будущих предварительных версиях и планах. 

Visual Studio отлично поддерживается разработка в GitHub Codespaces. Вы можете создать среду codespace и подключиться к ней, а затем использовать все возможности Visual Studio для работы над проектами в удаленной, размещенной среде. Несмотря на то, что исходный код и средства находятся в codespace и компиляция и отладка происходят в облаке, процесс разработки идет так же быстро и без задержек, как в локальной среде.

> [!NOTE]
> В этой статье описывается, как с помощью Visual Studio подключиться к GitHub Codespaces. Сведения о подключении к codespace с помощью других клиентов см. в документации по [Visual Studio Code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) или [GitHub](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace).

> [!NOTE]
> Если у вас еще не установлена [предварительная версия Visual Studio 2019](https://aka.ms/vspreview), ее можно скачать с сайта [visualstudio.microsoft.com](https://aka.ms/vspreview).

## <a name="enable-connect-to-github-codespaces"></a>Включение возможности подключения к GitHub Codespaces

Подключение к GitHub Codespaces с помощью предварительной версии Visual Studio 2019 не включено по умолчанию, поэтому сначала необходимо включить параметр "Функции предварительной версии".

1. В предварительной версии Visual Studio 2019 выберите пункт меню **Сервис** > **Параметры**, чтобы открыть диалоговое окно "Параметры".

2. В разделе **Среда** выберите **Функции предварительной версии** и установите флажок рядом с функцией **Подключение к GitHub Codespaces**.

   ![Включение функции предварительной версии "Подключение к GitHub Codespaces"](media/connect-to-github-codespaces-preview-feature.png)

3. Чтобы функция стала доступна, необходимо перезапустить Visual Studio.

## <a name="create-a-codespace"></a>Создание codespace

Если у вас еще нет среды codespace, ее можно создать в Visual Studio.

1. При запуске Visual Studio в начальном окне в разделе "Начало работы" будет кнопка **Подключиться к codespace**.

   ![Начальное окно Visual Studio с кнопкой "Подключиться к codespace"](media/visual-studio-start-window.png)

2. Нажмите кнопку **Подключиться к codespace**, и вам будет предложено войти в GitHub. Вы также можете создать учетную запись GitHub, если у вас ее еще нет.

   ![Вход в GitHub из Visual Studio](media/visual-studio-sign-in-to-github.png)

   Выбрав **Войти в GitHub**, следуйте указаниям по входу в GitHub.

3. Если вы еще не создавали среды codespace, вам будет предложено создать ее.

   В разделе "Сведения о codespace" необходимо указать **URL-адрес репозитория**. GitHub Codespaces клонирует указанный репозиторий в создаваемую среду codespace.

   Кроме того, в раскрывающихся списках можно изменить **тип экземпляра** и время ожидания **Приостановить через**. Указав сведения о codespace, нажмите кнопку **Создать и подключиться**.

   ![Сведения о codespace в Visual Studio](media/visual-studio-codespace-details.png)

   GitHub Codespaces начнет подготовку среды codespace и откроет Visual Studio, когда она будет готова.

   Имя codespace будет указано в строке меню вместе с именем удаленного репозитория.

   ![Среда Visual Studio, подключенная к codespace репозитория eShopOnWeb](media/visual-studio-eshoponweb-codespace.png)

4. Начните работать с Visual Studio так же, как в локальной среде. Возможные решения.

   * Просмотрите исходный код.
   * Выберите файл решения и выполните сборку решения (**CTRL+SHIFT+B**).
   * Установите точку останова в исходном файле и нажмите клавишу **F5**, чтобы запустить приложение в отладчике.
   * Внесите изменения и зафиксируйте их в репозитории.   

> [!NOTE]
> В настоящее время вы не можете создавать среды GitHub Codespaces для Visual Studio с помощью [портала Codespaces](https://github.com/codespaces) GitHub. Их можно создавать только с помощью Visual Studio.

## <a name="connect-to-a-codespace"></a>Подключение к codespace

После создания среды codespace ее можно открыть непосредственно из Visual Studio.

1. При запуске Visual Studio в начальном окне в разделе "Начало работы" будет кнопка **Подключиться к codespace**.

   ![Начальное окно Visual Studio с кнопкой "Подключиться к codespace"](media/visual-studio-start-window.png)

   Если вы уже находитесь в Visual Studio, то можете выбрать пункт меню **Файл** > **Подключиться к codespace**.

   ![Пункт "Подключиться к codespace" в меню "Файл" в Visual Studio](media/visual-studio-file-connect-to-codespace.png)

2. Выберите **Подключиться к codespace**. Вам будет предложено войти в GitHub, если вы еще не сделали этого.

3. После этого вы увидите все среды codespace GitHub, а также сведения о них на правой панели.

   ![Отображение доступных сред codespace GitHub и сведений о них в Visual Studio](media/visual-studio-connect-codespace.png)

   Все среды codespace, клонировавшие репозиторий Azure DevOps, будут отображаться только в Visual Studio, но не на странице GitHub Codespaces.

4. Выберите codespace и нажмите кнопку **Подключиться**. Если среда codespace была приостановлена, она будет перезапущена и откроется среда Visual Studio, подключенная к codespace.

   Имя codespace будет указано в строке меню вместе с именем удаленного репозитория.

   ![Среда Visual Studio, подключенная к codespace репозитория eShopOnWeb](media/visual-studio-eshoponweb-codespace.png)

5. Начните работать с Visual Studio так же, как в локальной среде. Возможные решения.

   * Просмотрите исходный код.
   * Выберите файл решения и выполните сборку решения (**CTRL+SHIFT+B**).
   * Установите точку останова в исходном файле и нажмите клавишу **F5**, чтобы запустить приложение в отладчике.
   * Внесите изменения и зафиксируйте их в репозитории.

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>См. также раздел

* [Что такое GitHub Codespaces?](codespaces-overview.md)
* [Настройка codespace](customize-codespaces.md)
* [Поддерживаемые функции Visual Studio](supported-features-codespaces.md)
