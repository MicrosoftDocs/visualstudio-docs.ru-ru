---
title: Использование учетных записей, которые требуют многофакторную проверку подлинности
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: Сведения о том, как использовать Visual Studio с учетными записями, которые используют многофакторную идентификацию.
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9ac42ccff8c7bffcc22c453002aad1caf6935d28
ms.sourcegitcommit: e4630a3bb89b4d606fe2cbd709bc773c5b538b78
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2021
ms.locfileid: "112975683"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Использование Visual Studio с учетными записями, которые требуют многофакторную идентификацию

При взаимодействии с внешними гостевыми пользователями рекомендуется защищать свои приложения с помощью политик **условного доступа**, таких как **многофакторная идентификация**.  

Если такие политики применяются, для доступа к вашим ресурсам гостевым пользователям необходимо выполнить дополнительные требования безопасности, помимо ввода традиционных имени пользователя и пароля. Эти политики можно применять на уровне клиента, приложения или отдельных гостевых пользователей точно так же, как для сотрудников и членов организации. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>Как политики многофакторной идентификации влияют на работу с Visual Studio?
В версиях Visual Studio до 16.6 возможны определенные проблемы с проверкой подлинности при работе с учетными записями, которые используют политики условного доступа (например, многофакторную идентификацию) и связаны с несколькими клиентами.

В таких случаях в вашем экземпляре Visual Studio могут несколько раз в день появляться запросы на повторную проверку подлинности. Соответственно, вам будет необходимо снова вводить учетные данные ранее прошедших проверку подлинности клиентов даже в рамках одного и того же сеанса Visual Studio.

## <a name="using-visual-studio-with-mfa-policies"></a>Использование Visual Studio с политиками многофакторной идентификации
В версии 16.6 в Visual Studio 2019 были реализованы новые возможности, позволяющие оптимизировать процесс доступа пользователей к ресурсам, защищенным с помощью политик условного доступа, таких как многофакторная идентификация. Что воспользоваться этим усовершенствованным рабочим процессом, вам необходимо настроить установленный по умолчанию в системе веб-браузер в качестве механизма для добавления или повторной проверки подлинности учетных записей Visual Studio.  

> [!WARNING]
> Если вы не используете этот рабочий процесс, могут возникать проблемы, связанные с многократными запросами на ввод учетных данных при добавлении или повторной проверке подлинности учетных записей Visual Studio. 

### <a name="enabling-system-web-browser"></a>Настройка использования системного веб-браузера

> [!NOTE] 
> Для оптимального взаимодействия рекомендуется очистить данные веб-браузера по умолчанию, прежде чем продолжать работу с этим рабочим процессом. Кроме того, если у вас зарегистрированы рабочие или учебные учетные записи в параметрах Windows 10 в разделе **Доступ к учетной записи места работы или учебного заведения**, убедитесь, что они должным образом прошли проверку подлинности.

Чтобы использовать этот рабочий процесс, перейдите в диалоговое окно параметров Visual Studio **(Сервис > Параметры)** , откройте вкладку **Учетные записи** и выберите пункт **Системный веб-браузер** в раскрывающемся списке **Использовать для добавления и повторной проверки подлинности учетных записей**. 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Выберите системный веб-браузер в меню.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Вход в дополнительные учетные записи, использующие политики многофакторной идентификации 
После активации рабочего процесса с использованием системного веб-браузера вы можете выполнять вход в дополнительные учетные записи или добавлять их в Visual Studio обычным способом с помощью диалогового окна "Параметры учетной записи" **(Файл > Параметры учетной записи)** .   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Добавьте в Visual Studio новую учетную запись персонализации." border="false":::

В результате этого действия откроется установленный по умолчанию в системе веб-браузер и появится запрос на вход в учетную запись и прохождение проверки с использованием заданной политики многофакторной идентификации.

При входе в систему может отобразиться дополнительный запрос с предложением не выходить из системы. В этом запросе, скорее всего, второй раз отобразится учетная запись, используемая для входа. Чтобы избежать повторного ввода учетных данных, рекомендуется выбрать **Да**. Это гарантирует, что учетные данные будут сохранены в сеансах браузера.

:::image type="content" source="media/kmsi.png" alt-text="Не выходить из системы?":::

На основе действий разработки и конфигурации ресурсов вам может быть предложено повторно ввести учетные данные во время сеанса. Это может произойти при добавлении нового ресурса или при попытке получить доступ к ресурсу без предварительного соблюдения требований к авторизации ЦС или MFA.

## <a name="reauthenticating-an-account"></a>Повторная проверка подлинности учетной записи  
При возникновении проблем с учетной записью в Visual Studio может появиться запрос на повторный ввод ее учетных данных.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Выполните повторную проверку подлинности учетной записи Visual Studio.":::

Щелкните **Еще раз введите учетные данные**. Откроется установленный по умолчанию в системе веб-браузер, и будет предпринята попытка автоматически обновить ваши учетные данные. Если это не поможет, вам будет предложено войти в учетную запись и пройти проверку с использованием заданной политики ЦС или MFA.

> [!NOTE] 
> Чтобы обеспечить оптимальное взаимодействие, не закрывайте браузер, пока не будут проверены все политики ЦС или MFA для ваших ресурсов. Закрытие браузера может привести к потере ранее созданного состояния MFA, а вам могут отображаться дополнительные запросы на авторизацию.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Отключение работы с конкретным клиентом Azure Active Directory в Visual Studio

В версии 16.6 Visual Studio 2019 предусмотрен фильтр, с помощью которого можно отключать клиентов по отдельности или глобально, эффективно скрывая их в Visual Studio. В этом случае вам не придется проходить проверку подлинности для таких клиентов, но при этом вы не сможете получить доступ к связанным с ними ресурсам.

Эта возможность может быть полезна, если вам требуется оптимизировать среду разработки, ограничив круг клиентов. Кроме того, она пригодится в тех случаях, когда вы не можете пройти проверку с использованием какой-либо политики условного доступа (многофакторной идентификации) из-за нарушений со стороны отдельных клиентов. 

### <a name="how-to-filter-out-all-tenants"></a>Как отфильтровать всех клиентов
Чтобы глобально отфильтровать всех клиентов, откройте диалоговое окно "Параметры учетной записи" **(Файл > Параметры учетной записи...)** и снимите флажок **Authenticate Across all Azure Active Directories** (Проверка подлинности для всех каталогов Azure Active Directory).

При снятии этого флажка проверка подлинности выполняется только в клиенте учетной записи по умолчанию. Это также означает, что вы не сможете получать доступ к ресурсам, связанным с другими клиентами, в которых ваша учетная запись может быть гостевой.

### <a name="how-to-filter-out-individual-tenants"></a>Как отфильтровать отдельных клиентов
Чтобы выполнить фильтрацию клиентов, связанных с вашей учетной записью Visual Studio, откройте диалоговое окно "Параметры учетной записи" **(Файл > Параметры учетной записи)** и щелкните **Применить фильтр**. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Примените фильтр." border="false":::

Появится диалоговое окно **Фильтровать по учетной записи**, где вы можете выбрать клиентов, которые будут использоваться с вашей учетной записью. 

:::image type="content" source="media/select-filter-account.png" alt-text="Выберите учетную запись для фильтрации.":::

## <a name="see-also"></a>См. также

- [Вход в Visual Studio](signing-in-to-visual-studio.md)
- [Вход в Visual Studio для Mac](/visualstudio/mac/signing-in)
- [Работа с несколькими учетными записями пользователя](work-with-multiple-user-accounts.md)
