---
title: Создание пакета расширений
description: Узнайте, как использовать шаблон элемента для создания пакета расширений.
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 213e3e71503ebea8074594bbc88a06980e3e64b4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905141"
---
# <a name="walkthrough-create-an-extension-pack"></a>Пошаговое руководство. Создание пакета расширений

Пакет расширений представляет собой набор расширений, которые можно устанавливать вместе. Пакеты расширений позволяют легко делиться избранными расширениями с другими пользователями или объединять расширения в специальный набор для конкретных сценариев.

## <a name="prerequisites"></a>Предварительные требования

Начиная с версии 2015, установка Visual Studio включает пакет SDK для Visual Studio в качестве дополнительного компонента. Пакет SDK для VS можно установить и позже. Дополнительные сведения: [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

Функция пакетов расширений впервые стала доступной в Visual Studio 15.8, предварительная версия 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Создание расширения с помощью шаблона элемента для пакета расширений

Шаблон элемента "Пакет расширений" создает пакет с набором расширений, которые можно устанавливать вместе.

1. В диалоговом окне **Новый проект** выполните поиск по слову "vsix" и выберите **Проект VSIX**. В качестве **Имени проекта** введите "Тестовый пакет расширений". Нажмите кнопку **создания**.

2. Щелкните правой кнопкой мыши узел проекта в **Обозревателе решений**, а затем выберите **Добавить** > **Новый элемент**. Перейдите в узел **Расширяемости** для Visual C# и выберите **Пакет расширений**. Оставьте нетронутым имя файла по умолчанию (ExtensionPack1.cs).

3. Будет добавлен файл ExtensionPack1.vsext, который содержит следующий код.

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. Идентификатор vsixId расширения, которое будет включено в пакет расширений, можно найти в [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Найдите расширение, которое необходимо включить, и щелкните **Копировать идентификатор**. Вы можете обновить существующий идентификатор **vsixId** в приведенном выше файле или добавить другое расширение в список.

    ![Копирование vsixId из Marketplace](media/vsixid-marketplace.png)

5. Выполните сборку проекта и отправьте свое расширение в Marketplace. См. статью [Публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Пакет расширений может устанавливать только расширения, доступные в [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или в [закрытой коллекции](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Установка пакета расширений из Visual Studio Marketplace

После публикации расширения установите и протестируйте его в Visual Studio.

::: moniker range="vs-2017"

1. Находясь в Visual Studio, в меню **Сервис** щелкните **Расширения и обновления**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Находясь в Visual Studio, в меню **Расширения** щелкните **Управляемые расширения**.

::: moniker-end

2. Выберите **В сети** и выполните поиск "Тестовый пакет расширений".

3. Щелкните элемент **Загрузить**. После этого расширение и связанный с ним список расширений, входящих в пакет, будут запланированы для установки.

4. Ниже показан пример представления для загрузки пакета расширений в диалоговом окне **Управление расширениями**. Если вы хотите устанавливать лишь некоторые из расширений, входящих в пакет, вы можете изменить их список в разделе **Запланировано для установки**.

    ![Скачивание пакета расширений из Marketplace](media/vside-extensionpack.png)

5. Закройте все экземпляры Visual Studio для завершения установки.

## <a name="remove-the-extension"></a>Удаление расширения

Чтобы удалить расширение с компьютера, сделайте следующее.

::: moniker range="vs-2017"

1. Находясь в Visual Studio, в меню **Сервис** щелкните **Расширения и обновления**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Находясь в Visual Studio, в меню **Расширения** щелкните **Управляемые расширения**.

::: moniker-end

2. Выберите **Тестовый пакет расширений**, а затем щелкните **Удалить**. После этого расширение и связанный с ним список расширений, входящих в пакет, будут запланированы для удаления.

3. Чтобы завершить удаление, закройте все экземпляры Visual Studio.
