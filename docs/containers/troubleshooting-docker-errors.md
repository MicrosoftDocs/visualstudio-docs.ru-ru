---
title: Устранение неполадок клиента Docker в Windows | Документация Майкрософт
description: Устранение неполадок, которые возникают при использовании Visual Studio для создания и развертывания веб-приложений в Docker в Windows с помощью Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jmartens
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 5f48b5c06e91b9c05e6edc7e2a1738aeb677a7ba
ms.sourcegitcommit: 69456d802203d21dabc3ae8662547a3241c24f47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2021
ms.locfileid: "110235915"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Устранение неполадок при разработке с Docker в Visual Studio

Используя средства Visual Studio для работы с контейнерами, вы можете столкнуться с некоторыми проблемами при создании или отладке приложения. Далее приведены некоторые распространенные действия по устранению неполадок.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Совместное использование тома не включено. Включите совместное использование тома в параметрах Docker CE для Windows (только для контейнеров Linux)

Управление общим доступом к файлам необходимо только при использовании Hyper-V с Docker. Если используется WSL 2, приведенные ниже действия можно опустить, а параметр общего доступа к файлам не будет отображатся. Для разрешения этой проблемы:

1. Щелкните правой кнопкой мыши **Docker for Windows** (Docker для Windows) в области уведомлений, а затем выберите **Параметры**.
1. Выберите **Ресурсы** > **Общий доступ к файлам** и предоставьте общий доступ к нужной папке. Вы также можете предоставить доступ ко всему системному диску, однако мы не рекомендуем делать это.

    :::image type="content" source="media//troubleshooting-docker-errors/docker-settings-image.png" alt-text="Общие диски":::

> [!TIP]
> В версиях позднее Visual Studio 2017 15.6 выдается предупреждение, если **Общие диски** не настроены.

## <a name="unable-to-start-debugging"></a>Невозможно начать отладку

Одна из причин может быть связана с наличием устаревших компонентов отладки в папке профиля пользователя. Чтобы последние компоненты отладки скачались при следующем сеансе отладки, выполните следующие команды для удаления папок:

- del %userprofile%\vsdbg;
- del %userprofile%\onecoremsvsmon.

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Ошибки, характерные для сетей при отладке приложения

Попробуйте выполнить сценарий, который можно скачать из репозитория GitHub для [очистки сетей узлов контейнера](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), который обновит связанные с сетью компоненты на вашем хост-компьютере.

## <a name="mounts-denied"></a>Отказ в подключении

При использовании Docker для macOS может появиться ошибка со ссылкой на папку /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Добавьте папку на вкладку общего доступа к файлам в Docker.

## <a name="docker-users-group"></a>Группа пользователей Docker

При работе с контейнерами в Visual Studio может возникнуть следующая ошибка.

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Для работы с контейнерами Docker требуются разрешения, предоставляемые участникам группы docker-users.  Чтобы добавить себя в эту группу в Windows 10, выполните указанные ниже действия.

1. В меню "Пуск" откройте **Управление компьютером**.
1. Разверните узел **Локальные пользователи и группы** и выберите узел **Группы**.
1. Найдите группу **docker-users**, щелкните ее правой кнопкой мыши и выберите пункт **Добавить в группу**.
1. Добавьте свою учетную запись пользователя или несколько учетных записей.
1. Выйдите из системы и войдите снова, чтобы изменения вступили в силу.

Добавлять пользователей в группы можно также с помощью команды `net localgroup` в командной строке администратора.

```cmd
net localgroup docker-users DOMAIN\username /add
```

В PowerShell используйте командлет [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember).

## <a name="low-disk-space"></a>Недостаточно места на диске

По умолчанию Docker хранит образы в папке *%ProgramData%/Docker/* , которая обычно находится на системном диске — *C:\ProgramData\Docker\*. Чтобы образы не занимали место на системном диске, можно изменить расположение папки образов. Для этого сделайте следующее:

 1. Щелкните правой кнопкой мыши значок Docker на панели задач и выберите **Параметры**.
 1. Выберите **Docker Engine** (Обработчик Docker). 
 1. На панели редактирования добавьте параметр свойства `graph`, указывающий требуемое расположение для образов Docker:

```json
    "graph": "D:\\mypath\\images"
```

:::image type="content" source="media/troubleshooting-docker-errors/docker-daemon-settings.png" alt-text="Снимок экрана: общий доступ к файлам в Docker":::

Нажмите **Применить и перезагрузить**. Эти действия изменяют файл конфигурации: *%ProgramData%\docker\config\daemon.json*. Ранее созданные образы не перемещаются.

## <a name="container-type-mismatch"></a>Несоответствие типов контейнеров

При добавлении в проект поддержки Docker выберите контейнер Windows или Linux. Если узел сервера Docker не настроен на запуск того же типа контейнера, что и целевой объект проекта, то, скорее всего, появится сообщение об ошибке, аналогичное приведенному ниже:

:::image type="content" source="media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png" alt-text="Снимок экрана: несоответствие узла Docker и проекта":::

Для разрешения этой проблемы:

- В области уведомлений щелкните правой кнопкой мыши значок Docker для Windows и выберите **Switch to Windows containers...** (Переключиться на контейнеры Windows...) или **Switch to Linux containers...** (Переключиться на контейнеры Linux...).

## <a name="microsoftdockertools-github-repo"></a>Репозиторий GitHub Microsoft/DockerTools

При возникновении других проблем дополнительные сведения см. в репозитории [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).

## <a name="see-also"></a>См. также

- [Устранение неполадок в Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
