---
title: Выбор стратегии развертывания ClickOnce | Документация Майкрософт
description: Узнайте о стратегиях развертывания приложения ClickOnce и о том, как выбрать стратегию в зависимости от типа развертываемого приложения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4c20689c79529edf4a34edca857dedf1420b03f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895119"
---
# <a name="choose-a-clickonce-deployment-strategy"></a>Выбор стратегии развертывания ClickOnce
Существует три разные стратегии развертывания приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Выбираемая стратегия зависит главным образом от типа развертываемого приложения. Ниже перечисляются следующие три стратегии развертывания:

- установка из Интернета или общего сетевого ресурса;

- установка с компакт-диска;

- запуск приложения из Интернета или общего сетевого ресурса.

    > [!NOTE]
    > Помимо выбора стратегии развертывания потребуется также выбрать стратегию предоставления обновлений приложения. Дополнительные сведения см. [в статье Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="install-from-the-web-or-a-network-share"></a>Установка из Интернета или общего сетевого ресурса
 При использовании этой стратегии приложение развертывается на веб-сервер или в общий сетевой файловый ресурс. Когда конечный пользователь хочет установить приложение, он или она щелкает значок на веб-странице или дважды щелкает значок в общем файловом ресурсе. Тогда приложение загружается, устанавливается и запускается на компьютере конечного пользователя. Элементы добавляются в меню **Пуск** и в группу **Установка и удаление программ** на **Панели управления**.

 Так как эта стратегия зависит от связности узлов в сети, она оптимальна для приложений, которые разворачиваются для пользователей, имеющих доступ к локальной сети или высокоскоростное подключение к Интернету.

 Если приложение развертывается из Интернета, можно передать аргументы в приложение при его активации с помощью URL-адреса. Дополнительные сведения см. [в разделе инструкции. Получение сведений о строке запроса в приложении ClickOnce в сети](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Аргументы невозможно передать в приложение, которое активируется с помощью любого другого метода, описанного в данном документе.

 Чтобы активировать эту стратегию развертывания в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], щелкните **Из Интернета** или **Из UNC-пути или общего файлового ресурса** на странице **Способ установки** мастера публикаций.

 Эта стратегия развертывания используется по умолчанию.

## <a name="start-the-application-from-the-web-or-a-network-share"></a>Запуск приложения из Интернета или общего сетевого ресурса
 Эта стратегия подобна первой стратегии за исключением того, что приложение ведет себя как веб-приложение. Когда пользователь щелкает ссылку на веб-странице (или дважды щелкает значок в общем файловом ресурсе), запускается приложение. Когда пользователи закрывают приложение, оно больше не доступно на их локальном компьютере; в меню **Пуск** и группу **Установка и удаление программ** на **Панели управления** ничего не добавляется.

> [!NOTE]
> Технически приложение загружается и устанавливается в кэш приложения на локальном компьютере, точно так, как веб-приложение загружается в веб-кэш. Как и в случае веб-кэша, файлы в конечном счете извлекаются из кэша приложений. Однако согласно восприятию пользователя приложение выполняется из Интернета или общего файлового ресурса.

 Данная стратегия оптимально подходит для приложений, которые используются редко — например средство расчета пособий работающим по найму, которое обычно выполняться лишь один раз в год.

 Чтобы активировать эту стратегию развертывания в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], щелкните **Не устанавливать приложение** на странице **Установить или выполнить из Интернета** мастера публикаций.

 Чтобы активировать эту стратегию развертывания вручную, измените тег **install** в манифесте развертывания. (Его значение может быть равно **true** или **false**. В программе *Mage.exe* используйте параметр **Только интерактивно** в списке **Тип приложения**.)

## <a name="install-from-a-cd"></a>установка с компакт-диска;
 При использовании этой стратегии приложение развертывается на съемный носитель, такой как компакт-диск или DVD-диск. Как и в случае предыдущего варианта, когда пользователь выбирает установку приложения, оно устанавливается и запускается, а элементы добавляются в меню **Пуск** и группу **Установка и удаление программ** на **Панели управления**.

 Эта стратегия оптимально подходит для приложений, которые развертываются для пользователей, не имеющих постоянной связности узлов сети или оснащенных малопроизводительными подключениями. Так как приложение устанавливается со съемного носителя, для установки не требуется сетевое подключение; однако связность узлов сети по-прежнему необходима для обновлений приложения.

 Чтобы активировать эту стратегию развертывания в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], щелкните **С компакт-диска или DVD-диска** на странице **Способ установки** мастера публикаций.

 Чтобы активировать эту стратегию развертывания вручную, измените тег **deploymentProvider** в манифесте развертывания. (В Visual Studio это свойство представляется как **URL-адрес установки** на странице **Публикация** конструктора проектов. В программе *Mage.exe* это **Начальное местоположение**.)

## <a name="web-browser-support"></a>Поддержка веб-браузеров
 Приложения, предназначенные для платформы .NET Framework 3.5, могут быть установлены с помощью любого браузера.

 Для приложений, предназначенных для платформы .NET Framework 2.0, требуется Internet Explorer.

## <a name="see-also"></a>См. также раздел
- [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Как опубликовать приложение ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)