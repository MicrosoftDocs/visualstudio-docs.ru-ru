---
title: Назначение подписок Visual Studio с GitHub Enterprise | Документация Майкрософт
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: Управление подписками в подписках Visual Studio с GitHub Enterprise
ms.openlocfilehash: 5837ec33e6f17f0970178a0f1b306960e9c42668
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249693"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Управление подписками Visual Studio с GitHub Enterprise
Клиенты, заключившие с корпорацией Майкрософт соглашения Enterprise (EA), имеют право приобрести новое предложение, в котором объединены стандартные подписки Visual Studio и GitHub Enterprise. Таким образом, подписчики Visual Studio смогут снизить затраты на приобретение GitHub Enterprise. 

Управление подписками Visual Studio с GitHub Enterprise, которые приобретает ваша организация, осуществляется в два этапа.

## <a name="manage-visual-studio-subscriptions"></a>Управление подписками Visual Studio
Если ваша организация приобрела подписки Visual Studio с GitHub Enterprise, относящаяся к Visual Studio часть подписки предоставляется незамедлительно, а подписки становятся доступны для назначения и управления на [портале администрирования подписок](https://manage.visualstudio.com) Visual Studio. После назначения подписки Visual Studio с GitHub Enterprise подписчик получит сообщение электронной почты с информацией о том, что он может получить доступ к своей подписке Visual Studio по адресу <https://my.visualstudio.com/subscriptions>.

Дополнительные сведения об управлении подписками Visual Studio см. в следующих разделах.
- [Использование портала администрирования](using-admin-portal.md)
- [Назначение подписок](assign-license.md)
- [Изменение подписок](edit-license.md)
- [Удаление подписок](delete-license.md)
- [Превышение доступности](handle-overclaimed-license.md)

> [!Important]
> Если подписки Visual Studio с GitHub Enterprise назначаются администраторами подписки Visual Studio без предварительного приобретения, GitHub не будет уведомлен о том, что вы хотите создать учетную запись GitHub Enterprise.  Прежде чем назначать подписки, необходимо **приобрести хотя бы одну** подписку Visual Studio с GitHub Enterprise.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>Переход на подписку Visual Studio с GitHub Enterprise
Если ваша организация приобрела подписки Visual Studio с планами GitHub Enterprise после назначения стандартных подписок Visual Studio Enterprise и Visual Studio Professional, на портале администрирования будет доступна функция для перехода существующих подписчиков в подписки Visual Studio Enterprise с GitHub Enterprise и (или) Visual Studio Professional с GitHub Enterprise.  Например, подписчики Visual Studio Professional перейдут на подписки Visual Studio Professional с GitHub Enterprise. На расположенной слева панели "Обзор" отобразится такая плитка:

   > [!div class="mx-imgBorder"]
   > ![Плитка с кнопкой "Перейти сейчас"](_img/assign-github/move-now.png "Нажмите кнопку "Перейти сейчас", чтобы выполнить переход на подписки Visual Studio с GitHub Enterprise.")

> [!IMPORTANT]
> Как упоминалось выше, существующие данные подписчиков, их журналы и идентификаторы подписки будут сохранены, а все преимущества, которые они активировали, не будут потеряны при переходе.  
>
> Эта функция развертывается поэтапно и может быть недоступна для вашего соглашения.

После нажатия кнопки **Перейти сейчас** появится всплывающая панель с рекомендациями по переносу ваших подписок Enterprise и (или) Professional:

   > [!div class="mx-imgBorder"]
   > ![Всплывающая панель](_img/assign-github/fly-out.png)

На панели будет показано, сколько пользователей перейдут на новую подписку. Кроме того, здесь можно указать, следует ли отправлять им уведомление по электронной почте по завершении перехода.  В уведомлении будет сказано, что их преимущества сохраняются, и предложено начать работу с GitHub.  

Нажав кнопку **Move all subscribers** (Выполнить переход всех подписчиков), вы подтвердите свой выбор. На выполнение этого действия потребуется несколько секунд.  Если у вас оформлены подписки Professional и Enterprise, переход нужно выполнять отдельно для каждой из них.  


## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>Что представляет собой процесс настройки Visual Studio с GitHub Enterprise?
GitHub Enterprise настраивается отдельно от подписок Visual Studio, и управление им также осуществляется отдельно. После покупки подписки Visual Studio с GitHub Enterprise начинается процесс настройки учетной записи GitHub Enterprise, и одновременно с этим процессом (но отдельно от него) происходит заключение соглашения на сайте [manage.visualstudio.com](https://manage.visualstudio.com). Настройка учетной записи GitHub Enterprise может занять некоторое время. 

После того как ваша организация настроит учетную запись GitHub Enterprise, подписчики, которым были назначены подписки Visual Studio с GitHub Enterprise, получат уведомление от GitHub о том, что их подписки Visual Studio связаны с GitHub Enterprise. После получения этого сообщения подписчики могут обратиться к администратору организации GitHub, чтобы получить приглашение для соответствующей организации.

Сведения о настройке GitHub Enterprise см. в [документации для подписчика](access-github.md).   

## <a name="manage-github-enterprise-subscriptions"></a>Управление подписками GitHub Enterprise
При приобретении подписок GitHub Enterprise клиенты получают со стороны GitHub помощь в создании и настройке организаций, которые будут получать доступ к GitHub, а также в определении администраторов.  Пользователи, назначенные в качестве администраторов, получат соответствующие уведомления.  

Из-за более высокой сложности процесса полная настройка организаций и администраторов может занимать несколько дней с момента приобретения подписок.

Доступ к GitHub реализуется посредством облака через веб-сайт GitHub.com или с помощью локального сервера GitHub Enterprise Server.  Процессы управления для этих двух версий различаются.  На сайте GitHub доступны различные справочные материалы и руководства по управлению подписками GitHub Enterprise.  Ссылки на некоторые из этих ресурсов приводятся ниже.  

## <a name="support-resources"></a>Ресурсы поддержки

- Дополнительные сведения о назначении GitHub см. в [документации GitHub](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle).
- В [справке по GitHub](https://help.github.com/en) можно найти ответы на самые разные вопросы, связанные с GitHub.
- Кроме того, вы можете воспользоваться помощью других пользователей GitHub, посетив [форум сообщества GitHub](https://github.community/).
- По вопросам продаж, выставления счетов за подписки Visual Studio, использования подписок и учетных записей обращайтесь в [службу поддержки подписок](https://visualstudio.microsoft.com/subscriptions/support/).
- У вас есть вопросы о Visual Studio IDE, Azure DevOps Services или других продуктах или службах Visual Studio?  Перейдите на [страницу поддержки Visual Studio](https://visualstudio.microsoft.com/support/).
- Обратитесь в [службу технической поддержки](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) для GitHub Enterprise.   

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

Дополнительные сведения об управлении подписками Visual Studio с GitHub Enterprise см. также на [портале администрирования подписок](https://visualstudio.microsoft.com/subscriptions-administration/) Visual Studio.