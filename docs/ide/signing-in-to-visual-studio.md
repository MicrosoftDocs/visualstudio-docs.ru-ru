---
title: Войти
description: Вход в Visual Studio, чтобы продлить пробный период Visual Studio, разблокировка Visual Studio и многое другое
ms.custom: contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b4c91a2ff4693b62ce8ac4d40d493995c52b81b
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549476"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Вход в Visual Studio в Windows 

Хотя входить в систему не обязательно, это дает много преимуществ. В этой статье вы узнаете, [как выполнить вход](#how-to-sign-in), как [обновить профиль](#update-your-profile) и какие преимущества дает использование Visual Studio. 

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Вход в Visual Studio для Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> Для работы с ресурсами, настроенными для условного доступа, выполните обновление до Visual Studio 2019 версии 16.6 или последующей. Дополнительные сведения см. в статье [Использование Visual Studio с учетными записями, которые требуют многофакторную идентификацию](work-with-multi-factor-authentication.md).
> Использование Visual Studio 2017 для доступа к ресурсам, настроенным для условного доступа, может вызвать проблему с проверкой подлинности, когда в течение одного сеанса Visual Studio будут появляться повторные запросы на аутентификацию. 
> 
::: moniker-end

Ниже приведен полный список возможностей, которые вы получаете после входа:

|Преимущество|Описание|
|---|---|
|Продление пробного периода Visual Studio|Пробный период Visual Studio Professional и Visual Studio Enterprise **продлевается с 30 до 90 дней**. <br/>См. [Расширение пробной версии или обновление лицензии](../ide/how-to-unlock-visual-studio.md).|
|Разблокировка Visual Studio (подписка Visual Studio или организация Azure DevOps)|Разблокировка Visual Studio при использовании учетной записи, связанной с подпиской Visual Studio или организацией Azure DevOps.<br/>См. [Расширение пробной версии или обновление лицензии](../ide/how-to-unlock-visual-studio.md).|
|Синхронизация параметров Visual Studio|Настраиваемые параметры, например привязки клавиш, макет окна и цветовая тема, вступают в силу, как только вы войдете в Visual Studio на любом устройстве. <br/>См. статью [Синхронизация параметров Visual Studio на нескольких компьютерах](../ide/synchronized-settings-in-visual-studio.md).|
|Автоматическое подключение к службам|Подключение к таким службам, как Azure и Azure DevOps Services, в интегрированной среде разработки без повторного запроса учетных данных одной и той же учетной записи.|
|Продолжение использования выпуска Visual Studio Community|Если установка выпуска Community запрашивает лицензию, войдите в интегрированную среду разработки, чтобы продолжить использовать Visual Studio Community **бесплатно**. |
|Получение Visual Studio Dev Essentials|В эту программу входят бесплатные предложения ПО, обучение, поддержка и многое другое. <br/>См. [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/).|


## <a name="how-to-sign-in"></a>Как войти 

При первом открытии Visual Studio появляется запрос на вход и ввод основных регистрационных сведений.

![Запрос на вход](../ide/media/vs2019_signinpopup.png)

1. Выберите учетную запись Майкрософт или рабочую либо школьную учетную запись, которую вам будет удобнее использовать. Если у вас нет таких учетных записей, можно создать учетную запись Майкрософт бесплатно, перейдя по ссылке под кнопкой входа. При возникновении проблем см. статью [Как создать новую учетную запись Майкрософт?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Выберите параметры пользовательского интерфейса и цветовую тему, которые должны использоваться в Visual Studio. Visual Studio запоминает эти параметры и синхронизирует их во всех средах Visual Studio, в которых вы выполняли вход. Список синхронизируемых параметров см. в разделе [Синхронизированные параметры](../ide/synchronized-settings-in-visual-studio.md). Параметры можно изменить позже в меню **Сервис** > **Параметры** Visual Studio.
   После задания параметров будет запущена среда Visual Studio, чтобы можно было начать работу; при этом будет выполнен вход в систему. 
   
1. Чтобы проверить, выполнен ли вход, найдите свое имя в правом верхнем углу среды Visual Studio.

![Текущий пользователь, вошедший в систему VS2019](../ide/media/vs2019_username.png)

Если вы решили не выполнять вход при первом открытии Visual Studio, это можно запросто сделать позже. Найдите ссылку **Вход** в правом верхнем углу среды Visual Studio.

![Пользователь, не выполнивший вход](../ide/media/vs2019_usernotsignedin.png)

Если не выходить из системы, вы будете автоматически входить в Visual Studio при запуске среды. Также будут автоматически применены все изменения синхронизированных параметров. Чтобы выйти из системы, нажмите значок рядом с именем профиля в правом верхнем углу среды Visual Studio, выберите команду **Параметры учетной записи**, а затем ссылку **Выход**. Чтобы снова войти в систему, выберите команду **Вход** в правом верхнем углу среды Visual Studio.

## <a name="update-your-profile"></a>Обновление профиля

1. Выберите **Файл** > **Параметры учетной записи** и щелкните ссылку **Управление профилем Visual Studio**.

1. В окне браузера щелкните **Изменить профиль** и измените нужные параметры.

1. После завершения операции выберите **Сохранить изменения**.

## <a name="troubleshooting"></a>Устранение неполадок

Дополнительные сведения см. на странице [поддержки подписок](https://visualstudio.microsoft.com/subscriptions/support/).
