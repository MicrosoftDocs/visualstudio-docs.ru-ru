---
title: Включение обновлений администратора в Visual Studio с помощью Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Узнайте, как развернуть обновления администратора в Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: affb5a0c78c1ad1e230c571485385d9f55fc2bec
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307457"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Включение обновлений администратора в Visual Studio с помощью Microsoft Endpoint Configuration Manager

Microsoft Endpoint Configuration Manager (SCCM) может управлять обновлениями администратора Visual Studio 2017 и Visual Studio 2019 с помощью рабочего процесса управления обновлениями программного обеспечения.

> [!NOTE]
> Для упрощения документации в приведенном ниже содержимом продукты Visual Studio 2017, Visual Studio 2019 и Visual Studio 2022 будут обозначаться вместе как Visual Studio.

Когда корпорация Майкрософт публикует новое обновление Visual Studio в сети доставки содержимого (CDN), она одновременно публикует соответствующий пакет обновления администратора на серверах Центра обновления Майкрософт. Это впоследствии позволит администратору распространять обновление Visual Studio через [каталог Центра обновления Майкрософт](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) или [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS). Средство Configuration Manager можно настроить для синхронизации обновлений администратора Visual Studio из каталога WSUS с сервером сайта, а затем оно может загрузить обновление и распространить его на клиентские компьютеры Visual Studio по всей организации. Дополнительные сведения о том, какие исправления присутствуют в каждом выпуске Visual Studio, см. в [заметках о выпуске](/visualstudio/releases/2019/release-notes).

Чтобы распространять обновления администратора Visual Studio через Configuration Manager, вам необходимо выполнить следующие два начальных подготовительных шага:
1. разрешить Configuration Manager получать уведомления об обновлении администратора Visual Studio; 
2. разрешить (или запретить) клиентским компьютерам получать обновления администратора Visual Studio из Configuration Manager.

После выполнения этих шагов вы сможете использовать возможности управления обновлениями программного обеспечения Configuration Manager для развертывания обновлений администратора Visual Studio. Различные типы и характеристики обновлений администратора Visual Studio описаны в статье [Применение обновлений администратора](../install/applying-administrator-updates.md). В ней содержатся инструкции о том, как и когда следует распространять эти обновления в рамках организации. Дополнительные сведения о функциях и параметрах Configuration Manager см. в статье [Развертывание обновлений программного обеспечения в Microsoft Endpoint Configuration Manager](/mem/configmgr/sum/deploy-use/deploy-software-updates).

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Предоставление Configuration Manager возможности получать уведомления об обновлении администратора Visual Studio

Чтобы разрешить Configuration Manager управлять обновлениями администратора Visual Studio, вам потребуются:

* Текущая лицензированная версия Windows Server с Microsoft Endpoint Configuration Manager (текущая ветвь) и Windows Server Update Services (WSUS). Вы не можете использовать только службы WSUS для развертывания этих обновлений; их необходимо использовать вместе с Configuration Manager.

* Сервер WSUS верхнего уровня в иерархии и сервер сайта Configuration Manager верхнего уровня должны иметь доступ к URL-адресам и портам Visual Studio, перечисленным в этой статье: [Установка и использование Visual Studio и служб Azure, расположенных за брандмауэром или прокси-сервером](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md).  

* Чтобы получать уведомления о доступности пакетов обновлений администратора Visual Studio, необходимо настроить программу Microsoft Endpoint Configuration Manager.  Для этого выполните приведенные ниже действия. Дополнительные сведения см. в статье [Общие сведения об обновлении программного обеспечения в Microsoft Endpoint Configuration Manager](/mem/configmgr/sum/understand/software-updates-introduction).

  1. В консоли Configuration Manager выберите **Администрирование** (внизу слева), затем щелкните **Конфигурация сайта** (посередине слева), затем — **Сайты** и выберите свой сервер сайта.

  2. На ленте вкладки **Главная** вверху в группе **Параметры** выберите **Настройка компонентов сайта**, а затем — **Точка обновления программного обеспечения**.

  3. В диалоговом окне **Свойства компонента точки обновления программного обеспечения** сделайте следующее:

        * На вкладке **Продукты** в иерархии **"Средства для разработчиков", "Среды выполнения" и "Распространяемые компоненты"** выберите версии Visual Studio, которые необходимо синхронизировать.

        * На вкладке **Классификации** убедитесь, что выбраны пункты "Обновления безопасности", "Пакеты дополнительных компонентов" и "Обновления".

  4. Затем синхронизируйте обновления программного обеспечения с сервером WSUS. Для этого выберите **Библиотека программного обеспечения** (внизу слева), а затем на ленте вкладки **Главная** вверху нажмите кнопку **Синхронизировать обновления программного обеспечения**. Синхронизация обновлений программного обеспечения сделает доступные обновления администратора Visual Studio видимыми и доступными для развертывания из консоли Configuration Manager.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Включение (или отключение) возможности для клиентских компьютеров получать обновления администратора Visual Studio из Configuration Manager

Чтобы клиентский компьютер мог принимать обновления администратора Visual Studio, вам необходимо убедиться, что программа обнаружения клиентов Visual Studio установлена правильно. Кроме того, вам нужно будет установить раздел реестра, чтобы клиент мог получать обновления администратора.  

### <a name="visual-studio-client-detector-utility"></a>Программа обнаружения клиентов Visual Studio

Чтобы надлежащим образом получать и распознавать обновления администратора, на клиентских компьютерах должна быть установлена [программа обнаружения клиентов Visual Studio](https://support.microsoft.com/help/5001148). Эта программа была включена в состав всех обновлений Visual Studio 2017 и Visual Studio 2019, выпущенных 12 мая 2020 г. или позже. Она является необходимым компонентом всех обновлений администратора Visual Studio и доступна в [Каталоге Центра обновления Майкрософт](https://catalog.update.microsoft.com) для независимой установки.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>Кодирование намерения администратора на клиентских компьютерах

Чтобы получить обновления администратора, необходимо включить клиентские компьютеры. Этот шаг необходим для того, чтобы убедиться, что обновления не будут случайно применены на сторонних клиентских компьютерах.

Ключ  **AdministratorUpdatesEnabled**  предназначен для того, чтобы администратор закодировал свое намерение. Этот ключ может находиться в любом из стандартных расположений Visual Studio, как описано в статье  [Настройка параметров по умолчанию для корпоративного развертывания Visual Studio](/visualstudio/install/set-defaults-for-enterprise-deployments) документации. Чтобы создать и установить значение этого ключа, требуется доступ администратора на клиентском компьютере.

* Чтобы настроить на клиентском компьютере принятие обновлений администратора, установите для ключа REG_DWORD  **AdministratorUpdatesEnabled**  значение  **1**.
* Если ключ REG_DWORD  **AdministratorUpdatesEnabled**  **отсутствует или имеет значение 0**, применение обновлений администратора к клиентскому компьютеру будет заблокировано.

## <a name="feedback-and-support"></a>Отзывы и поддержка

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Вы можете использовать приведенные ниже методы, чтобы оставить отзыв об обновлениях администратора Visual Studio или сообщить о проблемах, которые влияют на обновления.

* Ознакомьтесь с руководством [Устранение неполадок при установке и обновлении Visual Studio](../install/troubleshooting-installation-issues.md).
* Задавайте вопросы в сообществе на [форуме вопросов и ответов по настройке Visual Studio](/answers/topics/vs-setup.html).
* Перейдите на [страницу поддержки Visual Studio](https://visualstudio.microsoft.com/vs/support/) и проверьте, указана ли ваша проблема в разделе с часто задаваемыми вопросами.  Вы также можете получить помощь в чате, нажав кнопку [Ссылка на службу поддержки](https://visualstudio.microsoft.com/vs/support/#talktous).
* [Отправьте отзыв о возможностях или сообщите о проблеме](https://aka.ms/vs/wsus/feedback), касающейся активации обновлений администратора, команде Visual Studio.
* Свяжитесь с менеджером по технической поддержке вашей организации для корпорации Майкрософт.

## <a name="see-also"></a>См. также раздел

* [Применение обновлений администратора](../install/applying-administrator-updates.md)
* [Руководство администратора Visual Studio](../install/visual-studio-administrator-guide.md)
* [Жизненный цикл и обслуживание продуктов Visual Studio](/visualstudio/productinfo/vs-servicing-vs)
* [Заметки о выпуске Visual Studio 2019](/visualstudio/releases/2019/release-notes)
* [Заметки о выпуске Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Установка Visual Studio](../install/install-visual-studio.md)
* [Часто задаваемые вопросы о каталоге Центра обновления Майкрософт](https://www.catalog.update.microsoft.com/faq.aspx)
* [Документация по Microsoft Endpoint Configuration Manager (SCCM)](/mem/configmgr)
* [Импорт обновлений из каталога Майкрософт в Configuration Manager](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Документация по Windows Server Update Services (WSUS)](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
