---
title: Подписки Visual Studio в MPSA | Документация Майкрософт
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/21/2021
ms.topic: conceptual
description: Узнайте об управлении подписками Visual Studio в рамках соглашения о продуктах и службах Майкрософт (MPSA)
ms.openlocfilehash: 63124e8853184fde04db7bc202e5acea3cfbe89f
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776536"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Подписки Visual Studio в соглашении о продуктах и службах Майкрософт (MPSA)
Если вы приобрели Подписки Visual Studio по программе MPSA, то существуют несколько моментов, которые следует учесть перед тем, как вы сможете стать администратором подписок Visual Studio и назначать подписки своим пользователям. Если вы уже назначены в качестве администратора, то можете перейти непосредственно на [портал администрирования подписок Visual Studio](https://manage.visualstudio.com/).

Пользователи с соглашением MPSA могут управлять ресурсами, приобретенными через MPSA, на портале [Business Center](https://businessaccount.microsoft.com/Customer), который поддерживает возможности, предоставляемые Volume Licensing Service Center (VLSC). К ним относятся просмотр сводных данных о ваших лицензиях, заказов, файлов для загрузки, ключей, пользователей и т. д. Однако действие подписок Visual Studio в MPSA больше сходно с облачными службами. Портал Business Center также использует рабочие учетные записи для входа, а не учетные записи Майкрософт (MSA). Если ваша организация использует облачные службы, такие как Office 365 или Azure Active Directory, и ваш адрес электронной почты является частью одной из этих служб, этот адрес уже является рабочей учетной записью. Это позволяет вам регистрироваться на портале Business Center при помощи существующего пароля. Если ваша организация не использует облачные службы и ваш адрес электронной почты не является рабочей учетной записью, вы можете использовать его для регистрации на портале Business Center.

Кроме того, получив права администратора подписок Visual Studio, вы сможете назначать подписки на [портале администрирования](https://manage.visualstudio.com/) подписок Visual Studio. В соглашении MPSA подписки Visual Studio необходимо подготовить для соответствующего портала управления, которым является портал администрирования подписок Visual Studio. Для этого необходимо связать учетную запись покупателя с клиентом (например, contoso.onmicrosoft.com).

Обратите внимание, что существует два типа арендаторов — управляемые и неуправляемые. Управляемый клиент — клиент, который уже управляется администраторами в организации.

Неуправляемый арендатор — это арендатор, у которого нет собственных администраторов и который не может использоваться для веб-служб, таких как Office 365. Неуправляемые клиенты также создаются при регистрации на портале Business Center при помощи адреса электронной почты, который не является рабочей учетной записью. Если при регистрации в Business Center было предложено создать пароль, то это означает, что ваш адрес электронной почты не является рабочей учетной записью и был создан неуправляемый клиент.

Прежде, чем установить связь с клиентом, необходимо выполнить некоторые действия, чтобы стать администратором Подписок Visual Studio. Эти действия описаны ниже.

## <a name="pre-tenant-association-managed-tenant"></a>Перед установлением связи с клиентом (управляемый клиент)
- Необходимо зарегистрироваться на портале Business Center.
- Необходимо быть администратором пользователей (как минимум) или глобальным администратором в рамках своего клиента. (В случае, если ваша компания уже использует облачные службы.) Указанные роли требуются для того, чтобы стать администратором подписок Visual Studio.
- Необходимо быть глобальным администратором в своем клиенте, чтобы иметь возможность связать вашу учетную запись покупателя с клиентом.
- Необходимо быть администратором учетных записей или диспетчером учетных записей на портале Business Center.
- В вашем профиле пользователя (и любого другого пользователя) поле "Страна или регион" на портале [Azure](https://portal.azure.com/) должно быть заполнено в соответствии с вашим регионом (т. е. США, Калифорния и т. д.). 

> [!NOTE]
> Все пользователи, которых нужно сделать администраторами подписок Visual Studio, необязательно должны быть пользователями портала Business Center, они должны удовлетворять только условиям номер 2 и 5.

Когда соблюдены условия, описанные выше, можно продолжить установление связи учетной записи покупателя с арендатором с помощью следующих действий.
1. Войдите на портал [Business Center](https://businessaccount.microsoft.com/Customer).
2. Щелкните вкладку **Учетная запись** и выберите **Связать домены**.
3. Выберите необходимую **учетную запись покупателя** (если у вас их больше одной).
4. Выберите **арендатор** (например, contoso.onmicrosoft.com).
5. Нажмите кнопку **Связать домен**.

Обычно при установлении связи процесс подготовки пользователей, соответствующих критериям, в качестве администраторов подписок Visual Studio занимает считаные минуты. Однако в некоторых случаях процесс может занимать до 24 часов. После завершения подготовки арендатора вы получите доступ к порталу администрирования подписок Visual Studio. Если это занимает больше 24 часов, обратитесь в [службу поддержки Business Center](https://businessaccount.microsoft.com/Customer/ContactUs).

> [!NOTE]
> При наличии новых пользователей, соответствующих условиям номер 2 и 5 (после установления связи), вам необходимо обратиться в службу поддержки MPSA. Поддержка MPSA будет оказывать помощь новым администраторам Подписок Visual Studio.

## <a name="tenant-association-unmanaged"></a>Установление связи с клиентом (неуправляемый клиент)
Если вы зарегистрировались на портале Business Center с помощью адреса электронной почты, который не является рабочей учетной записью (не зарегистрирован в Azure Active Directory (Azure AD)), как описано выше, то процесс установления связи с клиентом будет немного отличаться. Вам необходимо будет выполнить так называемый "перехват домена". Во время этого процесса вы сами назначите себя глобальным администратором, что изменит вашего клиента с неуправляемого на управляемый.

Более подробное описание этого процесса вы можете найти в [кратких руководствах](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Скачайте руководство *Настройка и использование веб-служб*, в котором описывается процедура перехвата домена. После выполнения этого действия ваша учетная запись покупателя будет связана с арендатором.

> [!NOTE]
> После завершения процесса перехвата домена вы станете удовлетворять пяти условиям из раздела "Перед установлением связи с арендатором (управляемый арендатор)". После выполнения всех условий останется только связаться со службой поддержки MPSA для подготовки дополнительных администраторов подписок Visual Studio.

## <a name="support-resources"></a>Ресурсы поддержки
- По вопросам администрирования подписок Visual Studio обратитесь в [службу поддержки подписок Visual Studio](https://aka.ms/vsadminhelp).

## <a name="see-also"></a>См. также
- [Документация по Visual Studio](/visualstudio/)
- [Документация по Azure DevOps](/azure/devops/)
- [Документация по Azure](/azure/)
- [Документация по Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Дальнейшие действия
Узнайте больше об управлении подписками Visual Studio.
- [Назначение отдельных подписок](assign-license.md)
- [Назначение нескольких подписок](assign-license-bulk.md)
- [Изменение подписок](edit-license.md)
- [Удаление подписок](delete-license.md)
- [Определение максимального использования](maximum-usage.md)