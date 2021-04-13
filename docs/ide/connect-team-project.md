---
title: Подключение к проектам в Team Explorer
description: Сведения о том, как использовать Team Explorer в Visual Studio для взаимодействия с членами команды при разработке проектов и управлении ими.
ms.custom: SEO-VS-2020
ms.date: 03/31/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 78a71911bb4334e04a085d91ff51238d34981beb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216609"
---
# <a name="connect-to-projects-in-team-explorer"></a>Подключение к проектам в Team Explorer

::: moniker range="vs-2017"

Окно средства **Team Explorer** используется для координации усилий с другими членами команды при разработке проекта, а также для управления работой, назначенной вам, вашей команде или вашим командным проектам. **Team Explorer** обеспечивает подключение Visual Studio к репозиториям Git и GitHub, репозиториям системы управления версиями Team Foundation (TFVC), а также проектам, размещенным в [службах Azure DevOps](/azure/devops/user-guide/what-is-azure-devops-services) или на локальном [сервере Azure DevOps](/azure/devops/index-all) (прежнее название TFS). Можно управлять исходным кодом, рабочими элементами и сборками.

::: moniker-end

::: moniker range="vs-2019"

Team Explorer обеспечивает подключение Visual Studio к репозиториям системы управления версиями Team Foundation (TFVC), а также проектам, размещенным в экземпляре [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) или в локальном экземпляре [Azure DevOps Server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) (ранее — TFS). Можно управлять исходным кодом, рабочими элементами и сборками.

> [!IMPORTANT]
> В последнем выпуске Visual Studio 2019 [**версии 16.8**](/visualstudio/releases/2019/release-notes/) новый интерфейс управления версиями Git включен по умолчанию. Дополнительные сведения о сравнении с Team Explorer см. в статье [**Параллельное сравнение Git и Team Explorer**](git-team-explorer-feature-comparison.md).
>
> Но если вы предпочитаете и дальше использовать Team Explorer, выберите **Средства**>**Параметры**>**Среда**>**Функции предварительной версии** и снимите флажок **Новый пользовательский интерфейс Git**.

Способ использования Team Explorer для подключения к проекту зависит от рабочей версии Visual Studio 2019.

## <a name="in-version-168-and-later"></a>Версия 16.8 и выше

1. Запустите Visual Studio 2019.

1. В начальном окне выберите раздел **Клонировать репозиторий**.

   ![Снимок экрана: диалоговое окно "Клонировать репозиторий" для Azure DevOps в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/clone-repository.png)

1. В разделе **Просмотреть репозиторий** выберите пункт **Azure DevOps**.

    ![Снимок экрана: раздел "Просмотреть репозиторий" в диалоговом окне "Подключение к проекту" в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Если появится окно входа, войдите в свою учетную запись.

1. В диалоговом окне **Подключение к проекту** выберите репозиторий, с которым нужно установить соединение, а затем нажмите кнопку **Клонировать**.

      ![Снимок экрана: диалоговое окно "Подключение к проекту" в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Если вы не видите предварительно заполненный список репозиториев для подключения, выберите меню **Добавление Azure DevOps Server**, чтобы ввести URL-адрес сервера. (Кроме того, вы можете увидеть сообщение "Серверы не обнаружены." со ссылками для добавления имеющегося сервера Azure DevOps Server или создания учетной записи Azure DevOps.)

   Затем в Visual Studio откроется окно **Обозреватель решений** с папками и файлами.

1. Перейдите на вкладку **Team Explorer**, чтобы просмотреть действия Azure DevOps.

      ![Снимок экрана: диалоговое окно "Team Explorer", созданное в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>Версия 16.7 и выше

1. Запустите Visual Studio 2019.

1. В начальном окне выберите **Клонирование или извлечение кода**.

   ![Снимок экрана: окно "Создание проекта" в Visual Studio 2019 версии 16.7 или более ранней](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. В разделе **Просмотреть репозиторий** выберите пункт **Azure DevOps**.

   ![Снимок экрана: окно "Клонирование или извлечение кода" с разделом "Просмотреть репозиторий", где указан пункт Azure DevOps в Visual Studio 2019 версии 16.7 или более ранней](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Если появится окно входа, войдите в свою учетную запись.

1. В диалоговом окне **Подключение к проекту** выберите репозиторий, с которым нужно установить соединение, а затем нажмите кнопку **Клонировать**.

      ![Снимок экрана: диалоговое окно "Подключение к проекту" в Visual Studio 2019 версии 16.7 или более ранней](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Содержимое этого списка зависит от того, какие репозитории Azure DevOps вам доступны.

   Visual Studio открывает **Team Explorer**, и после завершения клонирования появится уведомление.

     ![Снимок экрана: окно "Team Explorer" в Visual Studio 2019 версии 16.7 или более ранней после завершения клонирования](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Чтобы просмотреть папки и файлы, нажмите ссылку **Показать представление папки**.

     ![Снимок экрана: раздел решений в окне Team Explorer в Visual Studio 2019 версии 16.7 или более ранней после завершения клонирования](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio откроет **обозреватель решений**.

1. Нажмите ссылку **Решения и папки**, чтобы найти файл решения (SLN-файл), который нужно открыть.

      ![Снимок экрана: уведомление "Решения и папки" в Team Explorer в Visual Studio 2019 версии 16.7 или более ранней](../get-started/media/open-proj-repo-solutions-folders.png)

   Если в используемом репозитории нет файла решения, появится сообщение "Решения не найдены.&quot;. Но вы можете дважды щелкнуть любой файл в меню папок, чтобы открыть этот файл в редакторе кода Visual Studio.

::: moniker-end

::: moniker range=&quot;vs-2017&quot;

![Домашняя страница Team Explorer в Visual Studio](media/team-explorer/team-explorer.png &quot;Team Explorer — домашняя страница в Visual Studio.")

> [!TIP]
> Если при запуске Visual Studio окно **Team Explorer** не появляется, откройте его, выбрав команду **Вид** > **Team Explorer** в строке меню или воспользовавшись клавишами **CTRL**+ **&#92;** , **CTRL**+**M**.

## <a name="connect-to-a-project-or-repository"></a>Подключение к проекту или репозиторию

Подключение к проекту или репозиторию можно выполнить на странице **Подключение**.

![Страница подключения в Team Explorer](media/team-explorer/connect.png "Team Explorer — страница Подключения в Visual Studio.")

Подключение к проекту:

1. Откройте страницу **Подключение**, щелкнув значок **Управление подключениями**.

   ![Кнопка Управление подключениями в Team Explorer](media/team-explorer/manage-connections.png "Team Explorer — кнопка Управление подключениями в Visual Studio.")

1. На странице **Подключение** выберите **Управление подключениями**>**Подключиться к проекту**.

   ![Подключение к проекту в Team Explorer](media/team-explorer/connect-project.png "Team Explorer — вариант Подключение к проекту в Visual Studio.")

> [!TIP]
> Если вы хотите открыть проект из репозитория, см. статью [Открытие проекта из репозитория](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md). Если вы хотите создать новый проект или добавить пользователей в существующий, ознакомьтесь со статьями [Создание проекта (Azure DevOps)](/azure/devops/organizations/projects/create-project) и [Добавление пользователей в проект или команду (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

::: moniker-end

## <a name="see-also"></a>См. также

- [Наглядное сравнение Git и Team Explorer](git-team-explorer-feature-comparison.md)
- [Новый интерфейс Git в Visual Studio](git-with-visual-studio.md)
- [Справка по Team Explorer](reference/team-explorer-reference.md)
- [Подключение к проекту (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Устранение неполадок с подключением к проекту](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
