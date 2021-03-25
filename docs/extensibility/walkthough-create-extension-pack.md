---
title: Создание пакета расширения
description: Узнайте, как создать пакет расширений с помощью шаблона элемента пакета расширений.
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 57b447be3ee411b737c1aea5b0a4be5ef966c8c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062152"
---
# <a name="walkthrough-create-an-extension-pack"></a>Пошаговое руководство. Создание пакета расширения

Пакет расширений — это набор расширений, которые можно установить вместе. Пакеты расширений позволяют легко предоставлять доступ к избранным расширениям другим пользователям или объединять набор расширений для конкретного сценария.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, пакет SDK для Visual Studio входит в состав программы установки Visual Studio в качестве дополнительного компонента. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

Функция пакета расширений доступна начиная с версии Visual Studio 15,8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Создание расширения с помощью шаблона элемента пакета расширений

Шаблон элемента пакета расширений создает пакет расширений с набором расширений, которые можно установить вместе.

1. В диалоговом окне **Новый проект** найдите "VSIX" и выберите **проект VSIX**. В качестве **имени проекта** введите "пакет расширения теста". Нажмите кнопку **создания**.

2. В **Обозреватель решений** щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить**  >  **новый элемент**. Перейдите в узел **расширяемость** Visual C# и выберите **пакет расширения**. Оставьте имя файла по умолчанию (ExtensionPack1. cs).

3. Добавлен файл ExtensionPack1. всекст, содержащий следующий код.

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

4. Идентификатор vsixid расширения, включаемого в пакет расширений, можно найти на [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Найдите расширение, которое необходимо включить, и щелкните **идентификатор копии**. Вы можете обновить существующий **идентификатор vsixid** в указанном выше файле или добавить другое расширение в список.

    ![Копирование идентификатор vsixid из Marketplace](media/vsixid-marketplace.png)

5. Создайте проект и отправьте расширение в Marketplace. См. раздел [Публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Пакет расширений может устанавливать только расширения, доступные в [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или в [частном каталоге](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Установите пакет расширений из Visual Studio Marketplace

Теперь, когда расширение Опубликовано, установите его в Visual Studio и протестируйте его.

::: moniker range="vs-2017"

1. В Visual Studio в меню **Сервис** выберите **расширения и обновления**.

::: moniker-end

::: moniker range=">=vs-2019"

1. В Visual Studio в меню **расширения** выберите **управляемые расширения**.

::: moniker-end

2. Щелкните "в **сети** " и выполните поиск по запросу "пакет расширения теста".

3. Щелкните элемент **Загрузить**. После этого расширение и его список расширений, включенных в пакет расширений, будут запланированы для установки.

4. Ниже приведен пример представления загрузки пакета расширений диалогового окна **Управление расширениями** . Если вы предпочитаете устанавливать только некоторые из включенных расширений в пакете расширений, можно изменить список расширений в списке **запланировано для установки**.

    ![Скачать пакет расширений из Marketplace](media/vside-extensionpack.png)

5. Чтобы завершить установку, закройте все экземпляры Visual Studio.

## <a name="remove-the-extension"></a>Удаление расширения

Чтобы удалить расширение с компьютера, выполните следующие действия.

::: moniker range="vs-2017"

1. В Visual Studio в меню **Сервис** выберите **расширения и обновления**.

::: moniker-end

::: moniker range=">=vs-2019"

1. В Visual Studio в меню **расширения** выберите **управляемые расширения**.

::: moniker-end

2. Выберите **тест пакет расширений** и нажмите кнопку **Удалить**. После этого расширение и его список расширений, включенных в пакет расширений, будут запланированы для удаления.

3. Чтобы завершить удаление, закройте все экземпляры Visual Studio.
