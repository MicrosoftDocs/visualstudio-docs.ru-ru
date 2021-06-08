---
title: Добавление подключения в базу данных SQL Azure | Документация Майкрософт
description: Добавление подключения к базе данных SQL Azure в приложение с помощью Visual Studio Подключенные службы
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 26a01bfe2a34422f9596710f832a1c4af699fd3b
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588492"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Добавление подключения к базе данных SQL Azure

С помощью Visual Studio можно подключить любой из следующих компонентов к базе данных SQL Azure, используя функцию **подключенные службы** :

- Платформа .NET Framework консольное приложение
- ASP.NET MVC (платформа .NET Framework) 
- ASP.NET Core
- .NET Core (включая консольное приложение, WPF, Windows Forms, библиотеку классов)
- Рабочая роль .NET Core
- Функции Azure
- Приложение универсальная платформа Windows
- Xamarin
- Cordova

Подключенные службы добавляют необходимые ссылки и код подключения в проект и вносят соответствующие изменения в файлы конфигурации.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Подключенные службы в Visual Studio для Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Предварительные требования

- Visual Studio с установленной рабочей нагрузкой Azure.
- Проект одного из поддерживаемых типов

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Подключение к базе данных SQL Azure с помощью Подключенные службы

1. Откройте проект в Visual Studio.

1. В **Обозреватель решений** щелкните правой кнопкой мыши узел **подключенные службы** и в контекстном меню выберите команду **Добавить подключенную службу**.

1. На вкладке **подключенные службы** выберите значок + для **зависимости службы**.

    ![Добавить зависимость службы](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. На странице **Добавление зависимости** выберите **база данных SQL Azure**.

    ![Добавление службы базы данных SQL Azure](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Если вы еще не вошли в систему, войдите в свою учетную запись Azure. Если у вас нет учетной записи Azure, вы можете зарегистрироваться и получить [бесплатную пробную версию](https://azure.microsoft.com/account/free).

1. На экране **Настройка базы данных SQL Azure** выберите существующую базу данных SQL Azure и нажмите кнопку **Далее**.

    Если необходимо создать новый компонент, перейдите к следующему шагу. В противном случае перейдите к шагу 7.

    ![Подключение к существующему компоненту базы данных SQL Azure](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Чтобы создать базу данных SQL Azure, сделайте следующее:

   1. Выберите **создать базу данных SQL** в нижней части экрана.

   1. Заполните **базу данных SQL Azure: создать новый** экран и нажмите кнопку **создать**.

       ![Новая база данных SQL Azure](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Когда откроется экран **Настройка базы данных SQL Azure** , в списке появится новая база данных. Выберите новую базу данных в списке и нажмите кнопку **Далее**.

1. Введите имя строки подключения или выберите значение по умолчанию и укажите, должна ли строка подключения храниться в локальном файле секретов или в [Azure Key Vault](/azure/key-vault).

   ![Укажите строку подключения](./media/azure-sql-database-add-connected-service/connection-string.png)

1. На экране **Сводка изменений** отображаются все изменения, которые будут внесены в проект, если вы завершите процесс. Если изменения выглядят нормально, нажмите кнопку **Готово**.

   ![Сводка изменений](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   При появлении запроса на установку правил брандмауэра выберите **Да**.

   ![Правила брандмауэра](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. Подключение появится в разделе " **зависимости службы** " на вкладке " **подключенные службы** ".

   ![Зависимости служб](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>См. также раздел

- [Страница продукта базы данных SQL Azure](https://azure.microsoft.com/services/sql-database/)
- [Документация по базе данных SQL Azure](/azure/azure-sql/database/)
- [Подключенные службы ( Visual Studio для Mac)](/visualstudio/mac/connected-services)
