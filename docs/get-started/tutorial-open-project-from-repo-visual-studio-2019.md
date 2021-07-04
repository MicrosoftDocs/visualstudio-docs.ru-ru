---
title: Учебник. Открытие проекта из репозитория в Visual Studio 2019
description: Узнайте, как открывать проекты из репозитория Git или Azure DevOps с помощью Visual Studio 2019.
ms.custom: vs-acquisition, get-started
ms.date: 03/18/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2019
ms.openlocfilehash: b6f7cd57a1753ca5926ac73a9bb4c8c918d1bd10
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389947"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Учебник. Открытие проекта из репозитория

В этом руководстве вы примените Visual Studio для первичного подключения к репозиторию и открытия проекта.

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

## <a name="open-a-project-from-a-github-repo"></a>Открытие проекта из репозитория GitHub

Способ открывать проекты из репозитория GitHub с помощью Visual Studio 2019 зависит от версии. В частности, если вы установили [**версию 16.8**](/visualstudio/releases/2019/release-notes/) или более позднюю, вам доступны [новые полностью интегрированные возможности Git](../ide/git-with-visual-studio.md).

Но вы всегда можете открыть проект из репозитория GitHub с помощью Visual Studio, какая бы версия у вас ни была.

#### <a name="168-and-later"></a>[16.8 или более поздней версии](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Клонирование репозитория GitHub, а затем открытие проекта

1. Запустите Visual Studio 2019.

1. В начальном окне выберите раздел **Клонировать репозиторий**.

   ![Снимок экрана: диалоговое окно "Клонировать репозиторий" в Visual Studio 2019 версии 16.8 и более поздней](../ide/media/vs-2019/clone-repository.png)

1. Введите или укажите расположение репозитория, а затем нажмите кнопку **Клонировать**.

   ![Снимок экрана: диалоговое окно "Клонировать репозиторий" с URL-адресом репозитория Git в Visual Studio 2019 версии 16.8 и более поздней](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Возможно, появится диалоговое окно **Сведения о пользователе Git** с запросом на информацию для входа. Вы можете либо добавить сведения, либо изменить указанные сведения по умолчанию.

   ![Снимок экрана: диалоговое окно "Сведения о пользователе Git", где нужно ввести или изменить сведения учетной записи, в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/git-user-information-dialog.png)

    Нажмите кнопку **Сохранить**, чтобы добавить эту информацию в GITCONFIG-файл. (Или нажмите кнопку **Отменить**, чтобы сделать это позже.)

    > [!TIP]
    > Дополнительные сведения о входе в Visual Studio см. на странице [Вход в Visual Studio](../ide/signing-in-to-visual-studio.md). Дополнительные сведения о том, как использовать учетную запись GitHub для входа, см. на странице [Работа с учетными записями GitHub в Visual Studio](../ide/work-with-github-accounts.md).

    Затем Visual Studio автоматически загрузит и откроет решение из репозитория.

   ![Снимок экрана: проект в Git, открытом в обозревателе решений в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/git-solution-explorer.png )

1. Если репозиторий содержит несколько решений, они будут отображаться в обозревателе. Список решений можно просмотреть, нажав кнопку **Переключить представления** в обозревателе решений.

   ![Снимок экрана: проект в Git, открытом в обозревателе решений с выделенной кнопкой "Переключить представления" в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   В обозревателе решений можно либо открыть корневую папку в **представлении папки**, либо выбрать файл решения, который следует открыть.

   ![Снимок экрана: SLN-файл в Git, открытом в обозревателе решений после нажатия кнопки "Переключить представления" в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Чтобы сменить представление, нажмите кнопку **Переключить представления** еще раз.

    > [!TIP]
    > Вы также можете использовать меню **Git** в интегрированной среде разработки Visual Studio, чтобы клонировать репозиторий и открыть проект.
    >
    > ![Снимок экрана: меню Git в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Открытие локального проекта из репозитория GitHub, клонированного ранее

1. Запустите Visual Studio 2019.

1. В начальном окне выберите **Открыть проект или решение**.

    В Visual Studio откроется проводник. Найдите решение или проект и выберите его, чтобы открыть.

   ![Снимок экрана: окно "Открыть проект или решение" в Visual Studio 2019 версии 16.8 или более поздней](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Если вы недавно открывали проект или решение, его можно быстро открыть снова из раздела **Открыть последние**.

    > [!TIP]
    > Кроме того, можно использовать меню **Git** в интегрированной среде разработки Visual Studio, чтобы открывать локальные папки и файлы из репозитория, который ранее клонировали.
    >
    > ![Снимок экрана: меню Git в Visual Studio 2019 версии 16.8 или более поздней с развернутым подменю локальных репозиториев](../ide/media/vs-2019/git-menu-local-repositories.png)

    Теперь можно приступать к написанию кода.

#### <a name="167-and-earlier"></a>[16.7 и более ранней версии](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Клонирование репозитория GitHub, а затем открытие проекта

1. Запустите Visual Studio 2019.

1. В начальном окне выберите **Клонирование или извлечение кода**.

   ![Снимок экрана: окно "Создание проекта" в Visual Studio 2019 версии 16.7 или более ранней](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Введите или укажите расположение репозитория, а затем нажмите кнопку **Клонировать**.

   ![Снимок экрана: окно "Клонирование или извлечение кода" в Visual Studio 2019 версии 16.7 и более ранней](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio откроет проект из репозитория.

1. Если у вас есть файл решения, он будет отображаться в раскрывающемся меню "Решения и папки". Выберите его, и в Visual Studio откроется нужное решение.

   ![Снимок экрана: раскрывающийся список в обозревателе решений в Visual Studio 2019 версии 16.7 и более ранней](./media/open-proj-repo-github-solutions-folders-picker.png)

   Если в вашем репозитории нет файла решения (а именно SLN-файла), во всплывающем меню будет сообщение "Решения не найдены.". Но вы можете дважды щелкнуть любой файл в меню папок, чтобы открыть этот файл в редакторе кода Visual Studio.

    Теперь можно приступать к написанию кода.

---

> [!NOTE]
> Сведения для Visual Studio 2017 см. на странице [Открытие проекта из репозитория в Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md).

## <a name="connect-to-an-azure-devops-server"></a>Подключение к Azure DevOps Server

Сведения, отображаемые при подключении к Azure DevOps Server с помощью Visual Studio 2019, зависят от установленной версии. В частности, если вы установили [**версию 16.8**](/visualstudio/releases/2019/release-notes/) или более позднюю, то уже получили новый полностью интегрированный [интерфейс Git в Visual Studio](../ide/git-with-visual-studio.md).

Но, независимо от установленной версии, вы всегда можете подключиться к серверу Azure DevOps Server с помощью Visual Studio.

#### <a name="168-and-later"></a>[16.8 или более поздней версии](#tab/vs168later)

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

#### <a name="167-and-earlier"></a>[16.7 и более ранней версии](#tab/vs167earlier)

1. Запустите Visual Studio 2019.

1. В начальном окне выберите **Клонирование или извлечение кода**.

   ![Снимок экрана: окно "Создание проекта" в Visual Studio 2019 версии 16.7 или более ранней](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. В разделе **Просмотреть репозиторий** выберите пункт **Azure DevOps**.

   ![Снимок экрана: окно "Клонирование или извлечение кода" с разделом "Просмотреть репозиторий", где указан пункт Azure DevOps в Visual Studio 2019 версии 16.7 или более ранней](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Если появится окно входа, войдите в свою учетную запись.

1. В диалоговом окне **Подключение к проекту** выберите репозиторий, с которым нужно установить соединение, а затем нажмите кнопку **Клонировать**.

      ![Снимок экрана: диалоговое окно "Подключение к проекту" в Visual Studio 2019 версии 16.7 или более ранней](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Содержимое этого списка зависит от того, какие репозитории Azure DevOps вам доступны.

   Visual Studio открывает **Team Explorer**, и после завершения клонирования появится уведомление.

     ![Снимок экрана: окно "Team Explorer" в Visual Studio 2019 версии 16.7 или более ранней после завершения клонирования](./media/vs-2019/clone-complete-azure-devops.png)

1. Чтобы просмотреть папки и файлы, нажмите ссылку **Показать представление папки**.

     ![Снимок экрана: раздел решений в окне Team Explorer в Visual Studio 2019 версии 16.7 или более ранней после завершения клонирования](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio откроет **обозреватель решений**.

1. Нажмите ссылку **Решения и папки**, чтобы найти файл решения (SLN-файл), который нужно открыть.

      ![Снимок экрана: уведомление "Решения и папки" в Team Explorer в Visual Studio 2019 версии 16.7 или более ранней](./media/open-proj-repo-solutions-folders.png)

   Если в используемом репозитории нет файла решения, появится сообщение "Решения не найдены.". Но вы можете дважды щелкнуть любой файл в меню папок, чтобы открыть этот файл в редакторе кода Visual Studio.

---

## <a name="next-steps"></a>Дальнейшие действия

Если вы готовы создавать код в Visual Studio, переходите к любому из следующих учебников по конкретным языкам:

- [Учебники по Visual Studio | **C#**](./csharp/index.yml)
- [Учебники по Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Учебники по Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Учебники по Visual Studio | **Python**](../python/index.yml)
- [Учебники по Visual Studio | **JavaScript**, **TypeScript** и **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>См. также раздел

- [Открытие проекта из репозитория в Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Новый интерфейс Git в Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Наглядное сравнение Git и Team Explorer](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Azure DevOps Services. Начало работы с Azure Repos и Visual Studio)
- [Microsoft Learn. Начало работы с Azure DevOps](/learn/modules/get-started-with-devops/)
