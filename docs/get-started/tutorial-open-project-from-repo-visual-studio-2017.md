---
title: Учебник. Открытие проекта из репозитория в Visual Studio 2017
description: Узнайте, как открывать проекты из репозитория Git или Azure DevOps с помощью Visual Studio 2017.
ms.custom: vs-acquisition, get-started
ms.date: 02/15/2021
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
monikerRange: vs-2017
ms.openlocfilehash: 5543a568f7246d9600ba375d9a1cf19af4cbd2d4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389206"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Учебник. Открытие проекта из репозитория в Visual Studio 2017

В этом руководстве вы будете применять Visual Studio 2017 для первичного подключения к репозиторию и открытия проекта.

> [!TIP]
> Теперь в [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) доступен новый полностью интегрированный интерфейс подключения к репозиторию GitHub. Дополнительные сведения см. на странице [**Интерфейс GIT в Visual Studio**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Открытие проекта из репозитория GitHub с помощью Visual Studio 2017

1. Откройте Visual Studio 2017.

1. В верхней строке меню выберите **Файл** > **Открыть** > **Открыть из системы управления версиями**.

   Откроется **панель подключения к Team Explorer**.

    ![Окно Team Explorer в интегрированной среде разработки Visual Studio](./media/open-proj-repo-team-explorer.png)

1. В разделе **Локальные репозитории Git** выберите меню **Клонировать**.

    ![Выбор действия клонирования из раздела локальных репозиториев Git](./media/open-proj-repo-local-git-repo-clone.png)

1. В поле с текстом ***Enter the URL of a Git repo to clone** _ (Введите URL-адрес клонируемого репозитория Git) введите или вставьте URL-адрес нужного репозитория и нажмите клавишу _*ВВОД**. (Если появится запрос на вход в GitHub, выполните его.)

   Завершив клонирование репозитория, Visual Studio закрывает Team Explorer и открывает обозреватель решений. Появится сообщение *Click on Solutions and Folders above to view a list of Solutions* (Щелкните выше "Решения и папки", чтобы просмотреть список решений). Щелкните **Решения и папки**.

   ![Выбор представления "Решения и папки" в обозревателе решений](./media/open-proj-repo-github-solutions-folders.png)

1. Если у вас есть файл решения, он будет отображаться в раскрывающемся меню "Решения и папки". Выберите его, и Visual Studio откроет нужное решение.

   ![Выбор элемента для отображения из раскрывающегося списка в обозревателе решений](./media/open-proj-repo-github-solutions-folders-picker.png)

   Если в используемом репозитории нет файла решения (SLN-файла), раскрывающееся меню будет содержать текст No Solutions Found (Решение не найдено). Но вы можете дважды щелкнуть любой файл в меню папок, чтобы открыть этот файл в редакторе кода Visual Studio.

### <a name="review-your-work"></a>Проверка работы

Просмотрите следующую анимацию для проверки работы, выполненной в предыдущем разделе.

   ![Анимация открытия проекта из репозитория GitHub с помощью Visual Studio](./media/open-project-from-github.gif)

> [!NOTE]
> Сведения для Visual Studio 2019 см. на странице [Открытие проекта из репозитория в Visual Studio 2019](tutorial-open-project-from-repo-visual-studio-2019.md).

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Открытие проекта из репозитория Azure DevOps с помощью Visual Studio 2017

1. Откройте Visual Studio 2017.

1. В верхней строке меню выберите **Файл** > **Открыть** > **Открыть из системы управления версиями**.

   Откроется **панель подключения к Team Explorer**.

    ![Окно Team Explorer в интегрированной среде разработки Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Ниже описаны два способа подключиться к репозиторию Azure DevOps.

      - В разделе **Поставщики размещенных служб** выберите **Подключить…** .

        ![Раздел поставщиков размещенных служб в окне Team Explorer интегрированной среды разработки Visual Studio](./media/open-proj-repo-azure-devops.png)

      - В раскрывающемся списке **Управление подключениями** выберите команду **Подключиться к проекту…** .

        ![Раздел управления соединениями в окне Team Explorer интегрированной среды разработки Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. В диалоговом окне **Подключение к проекту** выберите репозиторий, с которым нужно установить соединение, а затем нажмите кнопку **Клонировать**.

      ![Диалоговое окно "Подключение к проекту" в Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Содержимое этого списка зависит от того, какие репозитории Azure DevOps вам доступны.

1. Завершив клонирование репозитория, Visual Studio закрывает Team Explorer и открывает обозреватель решений. Появится сообщение *Click on Solutions and Folders above to view a list of Solutions* (Щелкните выше "Решения и папки", чтобы просмотреть список решений). Щелкните **Решения и папки**.

      ![Уведомление "Решения и папки" от Team Explorer в Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Файл решения (SLN-файл) будет отображаться в раскрывающемся меню "Решения и папки". Выберите его, и Visual Studio откроет нужное решение.

   Если в используемом репозитории нет файла решения, раскрывающееся меню будет содержать текст No Solutions Found (Решение не найдено). Но вы можете дважды щелкнуть любой файл в меню папок, чтобы открыть этот файл в редакторе кода Visual Studio.

## <a name="next-steps"></a>Дальнейшие действия

Если вы готовы создавать код в Visual Studio 2017, переходите к любому из следующих учебников по конкретным языкам:

- [Учебники по Visual Studio | **C#**](./csharp/index.yml)
- [Учебники по Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Учебники по Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Учебники по Visual Studio | **Python**](../python/index.yml)
- [Учебники по Visual Studio | **JavaScript**, **TypeScript** и **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>См. также раздел

- [Открытие проекта из репозитория в Visual Studio 2019](tutorial-open-project-from-repo-visual-studio-2019.md)
- [Новый интерфейс Git в Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Azure DevOps Services. Начало работы с Azure Repos и Visual Studio)
- [Microsoft Learn. Начало работы с Azure DevOps](/learn/modules/get-started-with-devops/)
