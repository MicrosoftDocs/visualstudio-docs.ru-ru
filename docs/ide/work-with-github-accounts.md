---
title: Работа с учетными записями GitHub в Visual Studio
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: Сведения о том, как работать с учетными записями GitHub в Visual Studio.
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9f55a233cc2550cd452851edc9092b4b2f4f2411
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296369"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Работа с учетными записями GitHub в Visual Studio

Если у вас есть общедоступная учетная запись GitHub или GitHub Enterprise, вы можете добавить ее в цепочку ключей Visual Studio. После добавления учетной записи вы сможете использовать преимущества интеграции платформы, создавая репозитории GitHub и обращаясь к ним прямо из Visual Studio.

## <a name="adding-public-github-accounts"></a>Добавление общедоступных учетных записей GitHub

Вы можете добавить общедоступную учетную запись GitHub, если вы уже вошли в Visual Studio с рабочей или учебной учетной записью Майкрософт.

1. Щелкните значок с вашими инициалами в правом верхнем углу среды Visual Studio. Затем выберите **Параметры учетной записи…** для управления учетными записями. Диалоговое окно "Параметры учетной записи" также можно открыть, выбрав пункт меню **Файл** > **Параметры учетной записи**.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Параметры учетной записи":::

2. В подменю **Все учетные записи** щелкните значок "плюс", чтобы добавить учетную запись, и выберите **GitHub**.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="Выберите &quot;Добавить учетную запись GitHub&quot;":::

3. Вы будете перенаправлены в браузер, в котором можно выполнить вход с использованием учетных данных GitHub. После входа вы получите сообщение об успешном выполнении входа в браузере и сможете вернуться в Visual Studio.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Сообщение об успешном выполнении входа в браузере":::

4. В подменю **Все учетные записи** будут представлены обе учетные записи.

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Отображаются обе учетные записи":::

Если вы еще не вошли в Visual Studio с другой учетной записью, щелкните ссылку **Войти** в правом верхнем углу среды Visual Studio. Диалоговое окно "Параметры учетной записи" также можно открыть, выбрав пункт меню **Файл** > **Параметры учетной записи**. Затем следуйте приведенным выше инструкциям, чтобы добавить учетную запись GitHub.

![Пользователь, не выполнивший вход](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>Добавление учетных записей GitHub Enterprise

По умолчанию в Visual Studio включены только общедоступные учетные записи GitHub.

1. Чтобы включить учетные записи GitHub Enterprise, выберите **Инструменты** > **Параметры** и найдите раздел параметров **Учетные записи**.

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Меню параметров учетных записей":::

2. Затем установите флажок **Включить учетные записи GitHub Enterprise Server**. В следующий раз при переходе к **параметрам учетной записи** и при попытке добавить учетную запись GitHub вы увидите варианты действий для GitHub и GitHub Enterprise.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="Вход с использованием учетных данных GitHub Enterprise":::

3. После ввода адреса сервера GitHub Enterprise выберите **Войти с помощью браузера**. После этого вы сможете войти в систему с учетными данными GitHub Enterprise.

## <a name="see-also"></a>См. также

- [Работа с несколькими учетными записями пользователя](work-with-multiple-user-accounts.md)
- [Вход в Visual Studio](signing-in-to-visual-studio.md)
