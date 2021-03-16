---
title: Развертывание в локальную папку
description: Узнайте, как вы можете использовать средство публикации для публикации приложений ASP.NET, ASP.NET Core, .NET Core и Python в папку из Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23ef2036af7b93ee6eeaaa14cb8733a4e0ced638
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249504"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Развертывание приложения в папку с помощью Visual Studio

Вы можете использовать средство **публикации** для публикации приложений ASP.NET, ASP.NET Core, .NET Core и Python в папку из Visual Studio. Для Node.js эти действия поддерживаются, однако отличается пользовательский интерфейс.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]
::: moniker range=">=vs-2017"
> [!NOTE]
> Если вам нужно опубликовать классическое приложение Windows в папку, см. статью о [развертывании классического приложения с помощью ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# или Visual Basic). Для C + +/ CLR см. раздел [Развертывание собственного приложения с помощью ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications). Для C/C++ см. раздел [Развертывание собственного приложения с помощью проекта установки](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
> Если нужно опубликовать классическое приложение Windows .NET Core 3.1 или более поздней версии в папку, см. [эту статью](quickstart-deploy-using-clickonce-folder.md).

::: moniker-end

## <a name="deploy-to-a-local-folder"></a>Развертывание в локальную папку

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать** (или воспользуйтесь командой меню **Сборка** > **Опубликовать**).

    ![Команда Опубликовать в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-publish.png "Выбор команды Опубликовать")

1. Если ранее вы настроили какие-либо профили публикации, появится окно **Опубликовать**. Нажмите кнопку **Создать**.

1. В окне **Публикация** выберите **Папка**.

   ![Выбор папки в качестве целевого объекта публикации](../deployment/media/quickstart-publish-folder-new.png "Выбор папки")

   ::: moniker range=">=vs-2019"

   При развертывании приложения Windows .NET Core 3.1 или более поздней версии может потребоваться выбрать **папку** в окне **Указанный целевой объект**.

   ![Выбор папки в качестве указанного целевого объекта](../deployment/media/quickstart-publish-folder-targets.png "Выбор указанного целевого объекта")

   Если вы хотите опубликовать приложение Windows .NET Core 3.1 или более поздней версии с использованием ClickOnce, см. [эту статью](quickstart-deploy-using-clickonce-folder.md).
   ::: moniker-end

1. Введите путь или выберите **Обзор**, чтобы указать папку.

   ![Указание пути к папке](../deployment/media/quickstart-publish-folder-path.png "Выбор папки")

   ::: moniker range=">=vs-2019"
   Щелкните **Готово**, чтобы сохранить профиль.

   ![Панель свойств публикации с обзором профиля](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. Нажмите **Публиковать**. Visual Studio создает проект и публикует его в указанной папке.

   ::: moniker range="vs-2017"
   Отображается панель **Публикация** со свойствами проекта, содержащая сводку по профилю.

   ![Панель свойств публикации с обзором профиля](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. Чтобы настроить параметры развертывания, выберите **Изменить** в сводке по профилю публикации и откройте вкладку **Параметры**.

   Отображаемые параметры зависят от типа приложения. На следующем рисунке показан пример параметров для приложения ASP.NET Core.

    ![Параметры профиля](../deployment/media/quickstart-profile-settings.png "Параметры профиля")

    Дополнительные сведения о выборе параметров в .NET см. в следующих статьях:

    - [Развертывание, зависящее от платформы, и автономное развертывание](/dotnet/core/deploying/)
    - [Идентификаторы целевой среды выполнения (переносной RID и т. п.)](/dotnet/core/rid-catalog)
    - [Конфигурации отладки и выпуска](../ide/understanding-build-configurations.md)

1. Настройте параметры, например следует ли развернуть конфигурацию отладки или выпуска, а затем выберите **Сохранить**.

1. Для повторной публикации выберите **Публиковать**.

Разверните опубликованные файлы любым удобным вам способом. Например, можно упаковать их в *ZIP-файл*, использовать простую команду copy или развернуть их с помощью любого установочного пакета на выбор.

## <a name="next-steps"></a>Следующие шаги

Для приложений .NET:

- [Развертывание приложения .NET Core с помощью средства публикации](/dotnet/core/deploying/deploy-with-vs)
- [Публикация приложений .NET Core (развертывание, зависящее от платформы, и автономное развертывание)](/dotnet/core/deploying/)
- [Развертывание .NET Framework и приложений](/dotnet/framework/deployment/)
::: moniker range=">=vs-2019"
- [Развертывание приложения Windows .NET помощью ClickOnce](quickstart-deploy-using-clickonce-folder.md)
 ::: moniker-end
