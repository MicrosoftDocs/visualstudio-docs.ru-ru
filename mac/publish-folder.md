---
title: Публикация в папку
description: Сведения о публикации веб-приложения в папку с помощью Visual Studio для Mac.
ms.date: 11/09/2020
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: 99127416b6a488cd7e795b3c4a1888ff103c8029
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607396"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Публикация в папке с помощью Visual Studio для Mac

Вы можете использовать средство публикации для публикации консольных приложений .NET Core или приложений ASP.NET Core в папке.

## <a name="prerequisites"></a>Предварительные требования

- Среда [Visual Studio 2019 для Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019), установленная с поддержкой .NET Core.
- Консоль .NET Core или проект ASP.NET Core. Если у вас еще нет проекта, вы можете [создать его](./create-new-projects.md).

## <a name="publish-to-folder"></a>Публикация в папку

С помощью Visual Studio для Mac можно публиковать проекты .NET Core в папке, используя средство публикации. После публикации в папке можно передать файлы в другую среду. Для публикации в папку выполните следующие действия.

 1. В окне решения щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**.

    ![Контекстное меню публикации](media/publish-context-menu.png)

 2. Если ранее вы публиковали этот проект, вы увидите профиль публикации в меню. Выберите этот профиль публикации, чтобы начать процесс публикации.

 3. Чтобы опубликовать этот проект в папку в первый раз, выберите **Публикация в папку**

    ![Контекстное меню "Публикация в папку"](media/publish-to-folder-context-menu.png)

 4. Появится диалоговое окно **Публикация в папку**. В этом диалоговом окне можно настроить папку, где будет опубликован проект. Нажмите кнопку **Обзор** или вставьте путь.

 5. После нажатия кнопки **Опубликовать** выполняются следующие действия. Сначала создается профиль публикации. Профиль публикации — это файл MSBuild, который импортируется в проект во время процесса публикации. Он содержит свойства, которые используются во время процесса публикации. Эти файлы хранятся в `Properties/PublishProfiles` и имеют расширение `.pubxml`. Затем запускается процесс публикации. Ход выполнения можно контролировать в строке состояния в Visual Studio для Mac.

    ![Строка состояния в интегрированной среде разработки с состоянием публикации](media/publish-to-folder-status-bar.png)

 6. После успешного завершения публикации в окне поиска откроется папка публикации. Созданный профиль публикации отображается в контекстном меню публикации.

    ![Контекстное меню публикации с профилем папки](media/publish-context-menu-with-folder-profile.png)

 7. Чтобы опубликовать проект еще раз с теми же параметрами, щелкните профиль в контекстном меню публикации.

## <a name="customize-publish-options"></a>Настройка параметров публикации

Чтобы изменить имя профиля публикации (которое отображается в контекстном меню публикации), переименуйте файл профиля публикации. Не меняйте расширение файла (`.pubxml`).

Чтобы изменить путь к папке публикации, откройте профиль публикации и измените значение `publishUrl`.

Чтобы изменить используемую конфигурацию сборки, измените свойство `LastUsedBuildConfiguration` в профиле публикации.

## <a name="see-also"></a>См. также раздел
 - [dotnet publish](https://docs.microsoft.com/dotnet/core/tools/dotnet-publish)
 - [Публикация веб-приложения на веб-сайте с помощью Visual Studio](https://docs.microsoft.com/visualstudio/deployment/quickstart-deploy-to-a-web-site?view=vs-2019)