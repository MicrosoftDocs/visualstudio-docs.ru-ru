---
ms.openlocfilehash: b2f9327da5e195c50bd074a468e1f9e57ece94ea
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750368"
---
## <a name="prerequisites"></a>Предварительные требования

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads), установленная с соответствующими рабочими нагрузками для выбранного языка:
  * ASP.NET: **ASP.NET и разработка веб-приложений**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), установленная с соответствующими рабочими нагрузками для выбранного языка:
  * ASP.NET: **ASP.NET и разработка веб-приложений**
::: moniker-end

* Подписка Azure. Если у вас еще нет подписки, [подпишитесь на бесплатную версию](https://azure.microsoft.com/free/dotnet/), которая включает кредит в размере 200 USD на 30 дней и 12 месяцев доступа к популярным бесплатным службам.

* ASP.NET Core. Следуйте инструкциям из статьи [Краткое руководство. Создание первого веб-приложения ASP.NET Core с помощью Visual Studio](../../ide/quickstart-aspnet-core.md) или выполните описанные ниже действия.
  ::: moniker range=">=vs-2019"
  На начальном экране Visual Studio 2019 выберите **Создать проект**. Если окно запуска не открыто, выберите **Файл** > **Окно запуска**. В поле поиска введите **веб-приложение**, укажите **C#** в качестве языка, выберите **ASP.NET Core Web Application (Model-View-Controller)** (Веб-приложение ASP.NET Core (модель — представление — контроллер)) и щелкните **Далее**. На следующем экране присвойте проекту имя **MyASPApp** и нажмите кнопку **Далее**.

  Выберите рекомендуемую версию целевой платформы (.NET Core 3.1) или .NET 5 и щелкните **Создать**.
  ::: moniker-end
  ::: moniker range="vs-2017"
  В Visual Studio 2017 выберите **Файл** > **Создать проект**, а затем щелкните **Visual C#**  >  **.NET Core** и выберите **Веб-приложение ASP.NET Core**. При появлении запроса выберите шаблон **Веб-приложение (модель-представление-контроллер)**, убедитесь, что выбран параметр **Без проверки подлинности**, после чего нажмите кнопку **ОК**.
  ::: moniker-end

* Прежде чем выполнять действия по развертыванию, выполните сборку проекта с помощью команды **Сборка > Построить решение**.