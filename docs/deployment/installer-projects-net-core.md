---
description: Упаковка приложений как MSI часто осуществляется с помощью расширения проектов Visual Studio Installer.
title: Проекты Visual Studio Installer и .NET Core 3,1
titleSuffix: ''
ms.date: 08/18/2020
ms.topic: conceptual
helpviewer_keywords:
- installer projects
- installer projects, .NETCore
author: MSLukeWest
ms.author: lukewest
manager: MSLukeWest
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5a78c1cf4f7b1562408e0a3fb598075f2c114fc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171244"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Расширение проектов Visual Studio Installer и .NET Core 3.1

Упаковка приложений как MSI часто осуществляется с помощью расширения проектов Visual Studio Installer.

Расширение можно скачать здесь: [Visual Studio Installer проекты](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects) .

## <a name="update-for-net-core"></a>Обновление для .NET Core
В .NET Core есть две различные модели для публикации.

- Развертывания, зависящие от платформы

- Автономные приложения включают в себя среду выполнения.

Дополнительные сведения об этих стратегиях развертывания см. в статье [Общие сведения о публикации приложений в .NET Core](/dotnet/core/deploying/).

### <a name="workflow-changes-for-net-core-31"></a>Изменения рабочих процессов для .NET Core 3,1

1. Выберите **опубликовать элементы** вместо **основных выходных данных** , чтобы получить правильные выходные данные для проектов .NET Core 3,1.  Чтобы открыть это диалоговое окно, выберите **Добавить**  >  **выходные данные проекта...** в контекстном меню проекта.

    ![Выходная группа "опубликовать элементы" в диалоговом окне "Добавление выходной группы проекта"](../deployment/media/installer-projects-net-core-publish-items-output.png "Выбор публикации элементов")

2. Чтобы создать автономный установщик, задайте свойство **публишпрофилепас** в узле **Публикация элементов** в проекте установки, используя относительный путь к профилю публикации с установленными правильными свойствами.

    ![Задание профиля публикации для выходного элемента проекта публикации элементов](../deployment/media/installer-projects-net-core-publish-profile.png "Задать профиль публикации")

### <a name="prerequisites-for-net-core-31"></a>Необходимые компоненты для .NET Core 3,1

Если вы хотите, чтобы установщик мог установить необходимую среду выполнения для приложения .NET Core 3,1, зависящего от платформы, это можно сделать с помощью [необходимых компонентов](../deployment/application-deployment-prerequisites.md).  В диалоговом окне Свойства проекта установщика откройте диалоговое окно **Предварительные требования...** , и вы увидите следующие записи:

![Элементы .NET Core в диалоговом окне "необходимые компоненты"](../deployment/media/installer-projects-net-core-prerequisites.png "Предварительные требования для .NET Core")

Параметр **среды выполнения .NET Core.** .. следует выбрать для консольных приложений, для приложений WPF и WinForms следует выбрать значение **Среда выполнения .NET** ....

>[!NOTE]
>Эти элементы представлены начиная с выпуска Visual Studio 2019 с обновлением 7.

## <a name="see-also"></a>См. также раздел

- [Диалоговое окно «Необходимые компоненты»](../ide/reference/prerequisites-dialog-box.md)
- [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)
