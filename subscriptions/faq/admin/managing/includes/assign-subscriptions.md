---
title: Как назначать подписки Visual Studio?
description: Пользователям можно назначать по одной подписке за раз. Также можно использовать функцию массового добавления для быстрой и удобной передачи данных большого...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 12/03/2020
ms.openlocfilehash: 5a12d59f90ee2a09002efcb99c78cfd563060006
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96584539"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>Как назначать подписки Visual Studio?

Пользователям можно назначать по одной подписке за раз. Также можно использовать функцию массового добавления для быстрой и удобной передачи данных большого числа подписчиков.

Чтобы назначить подписки отдельным пользователям, сделайте следующее:

1. Откройте вкладку [Управление подписчиками](https://manage.visualstudio.com/subscribers) в верхней части страницы [manage.visualstudio.com](https://manage.visualstudio.com).
2. Нажмите "Добавить" и введите имя и адрес электронной почты пользователя, которому нужно назначить подписку.
    1. Если ваша организация использует Azure Active Directory, найти пользователя в текущем каталоге можно с помощью поля "Имя". Вы можете выбрать пользователя в результатах поиска или добавить его вручную.
3. Чтобы предоставить подписчику доступ для скачивания программного обеспечения при входе на [портал управления подписками Visual Studio](https://my.visualstudio.com/), оставьте включенным переключатель "Скачивания" в разделе "Параметры скачивания".
4. Укажите требуемые сведения в разделе "Настройки общения", чтобы выбрать язык, на котором подписчики получат сообщение о назначении.
5. Добавить заметки, связанные с назначением, можно в разделе с примечаниями.
6. Нажмите "Добавить" в нижней части всплывающей панели, чтобы завершить процесс назначения подписки. Ваш подписчик получит сообщение электронной почты и сразу же сможет начать работу с подпиской Visual Studio (ему не нужно ее активировать).

Чтобы назначить подписки нескольким пользователям, сделайте следующее:

1. Откройте вкладку [Управление подписчиками](https://manage.visualstudio.com/subscribers) в верхней части страницы [manage.visualstudio.com](https://manage.visualstudio.com).
2. Нажмите "Массовое добавление", скачайте шаблон Excel и сохраните его локальную копию.
3. Нужно заполнить все поля, кроме поля с примечанием.
    1. Проследите за тем, чтобы ни одно из полей формы не содержало запятые.
    2. Удалите пробелы до и после полей формы.
    3. Имена и фамилии пользователей, состоящие из двух частей, не должны содержать пробелы (например, имя "Maggie May" следует вводить как "MaggieMay").
4. Вернитесь на сайт [manage.visualstudio.com](https://manage.visualstudio.com), нажмите "Массовое добавление" и отправьте сохраненную копию шаблона Excel.
5. После отправки отобразится страница подтверждения и список новых подписчиков. Ваши подписчики получат сообщение электронной почты и сразу же смогут начать работу с подпиской Visual Studio (им не нужно ее активировать).

Для получения [дополнительных сведений](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) о том, как быстро и легко назначить подписки, обратитесь к статье о назначении подписок на Портале администрирования подписок на Visual Studio.  [Дополнительные сведения](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) об управлении подписками Visual Studio с GitHub Enterprise. 

## <a name="what-is-the-github-enterprise-setup-process"></a>Что представляет собой процесс настройки GitHub Enterprise? 

GitHub Enterprise настраивается отдельно от подписок Visual Studio, и управление им также осуществляется отдельно. После покупки подписки Visual Studio с GitHub Enterprise начинается процесс настройки учетной записи GitHub Enterprise, и одновременно с этим процессом (но отдельно от него) происходит заключение соглашения на сайте manage.visualstudio.com. Настройка учетной записи GitHub Enterprise может занять некоторое время.  

После того как ваша организация настроит учетную запись GitHub Enterprise, подписчики, которым были назначены подписки Visual Studio с GitHub Enterprise, получат уведомление от GitHub о том, что их подписки Visual Studio связаны с GitHub Enterprise. После получения этого сообщения подписчики могут обратиться к администратору организации GitHub, чтобы получить приглашение для соответствующей организации. 

[Дополнительные сведения](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) об управлении подписками Visual Studio с GitHub Enterprise. Дополнительные сведения о процессе настройки GitHub Enterprise см. в [документации для подписчиков](https://docs.microsoft.com/visualstudio/subscriptions/access-github). 