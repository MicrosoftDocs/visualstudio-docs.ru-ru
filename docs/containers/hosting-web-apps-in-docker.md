---
title: Развертывание контейнера Docker для ASP.NET в реестре ACR
description: Сведения об использовании инструментов Visual Studio для работы с контейнерами и развертывания веб-приложения ASP.NET Core или ASP.NET Core в реестре контейнеров
author: ghogen
manager: jmartens
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-azure
ms.date: 03/15/2021
ms.author: ghogen
ms.openlocfilehash: d549a3097416f499adc9d03f83d7b4ef4c953442
ms.sourcegitcommit: c875360278312457f4d2212f0811466b4def108d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107315970"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Развертывание контейнера ASP.NET в реестр контейнеров из Visual Studio

## <a name="overview"></a>Обзор

Docker — это облегченная платформа контейнеров, чем-то похожая на виртуальную машину, которую можно использовать для размещения приложений и служб.
Это руководство покажет как с помощью Visual Studio публиковать контейнерные приложения в [реестре контейнеров Azure](https://azure.microsoft.com/services/container-registry).

Если у вас еще нет подписки Azure, [создайте бесплатную учетную запись Azure](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs), прежде чем начинать работу.

## <a name="prerequisites"></a>Предварительные требования

Для работы с этим руководством вам понадобится следующее:

::: moniker range="vs-2017"
* Установите последнюю версию [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) с рабочей нагрузкой "ASP.NET и разработка веб-приложений"
::: moniker-end
::: moniker range=">=vs-2019"
* Установите последнюю версию [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с рабочей нагрузкой "ASP.NET и разработка веб-приложений"
::: moniker-end
* Установить [Docker для Windows](https://docs.docker.com/docker-for-windows/install/).

## <a name="create-an-aspnet-core-web-app"></a>Создание веб-приложения ASP.NET Core

Давайте создадим простое приложение ASP.NET Core, которое мы будем использоваться в этом руководстве. Если у вас уже есть проект, этот раздел можно пропустить.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

::: moniker range="vs-2017"

## <a name="publish-your-container-to-azure-container-registry"></a>Опубликуйте контейнер в реестре контейнеров Azure

1. В **обозревателе решений** щелкните правой кнопкой проект и выберите **Опубликовать**.
2. В диалоговом окне **Целевой объект публикации** выберите **Реестр контейнеров**.
3. Выберите **Создать реестр контейнеров Azure** и щелкните **Опубликовать**.
4. Заполните нужные значения в окне **Создать новый реестр контейнеров Azure**.

    | Параметр      | Рекомендуемое значение  | Описание                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-префикс** | Глобально уникальное имя | Имя, которое однозначно идентифицирует реестр контейнеров. |
    | **Подписка** | Выберите свою подписку | Подписка Azure, которую нужно использовать. |
    | **[Группа ресурсов](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Имя группы ресурсов, в которой создается реестр контейнеров. Чтобы создать группу ресурсов, выберите **Создать**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Стандартный | Уровень обслуживания в реестре контейнеров  |
    | **Расположение реестра** | Расположение рядом с вами | Выберите расположение в ближайшем [регионе](https://azure.microsoft.com/regions/) или в регионе, расположенном рядом с другими службами, которые будут использовать реестр контейнеров. |

    ![Диалоговое окно "Создание реестра контейнеров Azure" Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Нажмите кнопку **Создать**.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Опубликуйте контейнер в реестре контейнеров Azure
1. В **обозревателе решений** щелкните правой кнопкой проект и выберите **Опубликовать**.
2. В диалоговом окне **Публикации** выберите **Реестр контейнеров Docker**.

   ![Снимок экрана диалогового окна публикации — выбор реестра контейнеров DOCKER](media/container-tools/vs-2019/docker-container-registry.png)

3. Выберите **Создать Реестр контейнеров Azure**.
 
   ![Снимок экрана диалогового окна публикации — создание реестра контейнеров DOCKER](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. Заполните нужные значения в окне **Реестр контейнеров Azure**.

    | Параметр      | Рекомендуемое значение  | Описание                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-префикс** | Глобально уникальное имя | Имя, которое однозначно идентифицирует реестр контейнеров. |
    | **Подписка** | Выберите свою подписку | Подписка Azure, которую нужно использовать. |
    | **[Группа ресурсов](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Имя группы ресурсов, в которой создается реестр контейнеров. Чтобы создать группу ресурсов, выберите **Создать**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Стандартный | Уровень обслуживания в реестре контейнеров  |
    | **Расположение реестра** | Расположение рядом с вами | Выберите расположение в ближайшем [регионе](https://azure.microsoft.com/regions/) или в регионе, расположенном рядом с другими службами, которые будут использовать реестр контейнеров. |

    ![Диалоговое окно "Создание реестра контейнеров Azure" Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png)

5. Нажмите кнопку **Создать**.

6. Нажмите кнопку **Готово**, чтобы завершить процесс.
::: moniker-end

Теперь можно извлечь контейнер из реестра в любой узел, поддерживающий работу образов Docker, например [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>См. также раздел

[Краткое руководство. Развертывание экземпляра контейнера в Azure с помощью Azure CLI](/azure/container-instances/container-instances-quickstart)
