---
title: Настройка codespace (предварительная версия)
description: Ознакомьтесь с дополнительными сведениями о том, как настроить codespace.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 0e23ca3255761f4d93f89251d00c12c14aecf7b9
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672355"
---
# <a name="how-to-customize-a-codespace-preview"></a>Настройка codespace (предварительная версия)

> [!Important] 
> По состоянию на 12 апреля 2021 г. подключение к GitHub Codespaces из Visual Studio 2019 больше не будет поддерживаться, и эта закрытая предварительная версия перестанет использоваться. Мы сосредоточены на разработке интерфейсов для облачных решений внутреннего цикла и VDI, оптимизированных для широкого спектра рабочих нагрузок Visual Studio. Рекомендуем следить за [форумом сообщества разработчиков](https://developercommunity.visualstudio.com/home) Visual Studio, чтобы получать информацию о будущих предварительных версиях и планах. 

GitHub Codespaces предоставляет полнофункциональную среду разработки в облаке. Для разработки на основе Windows с использованием Visual Studio 2019 экземпляры GitHub Codespaces по умолчанию могут послужить отличной отправной точкой, но можно также настроить среду под конкретный проект.

## <a name="installed-software"></a>Установленное программное обеспечение

В областях codespace в Windows уже установлено множество платформ и средств, так что вы можете сразу приступить к работе. В таблице ниже перечислены приложения и компоненты, доступные во всех средах Windows codespace.

| Приложение                                         | Псевдоним пути | Версия            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | Недоступно        | 4.8                |
| Среда выполнения .NET Core                           | dotnet     | 2.1, 3.1           |
| Пакет SDK для .NET Core                               | dotnet     | 2.1, 3.1.3, 3.1.4  |
| Azure CLI                                   | az         | 2.5                |
| Chocolatey                                  | choco      | 0.10.15            |
| CMake                                       | cmake      | 3,17               |
| Git                                         | git        | 2.26               |
| Microsoft Build                             | msbuild    | 16,7               |
| Microsoft SQL Server 2019 Express Edition   | Недоступно        | 15.0               |
| Ninja                                       | ninja      | 1.8.2              |
| Node.js                                     | node       | 12.16              |
| npm                                         | npm        | 6,14               |
| Python                                      | python     | 3,7                |
| Диспетчер пакетов VC                          | vcpkg      | 2020.02            |
| Пакет Windows SDK                                 | Недоступно        | 10.0.18362         |

Приведенный выше список не является исчерпывающим и не содержит многие средства, устанавливаемые Visual Studio (например, IISExpress). Компонент также может иметь дополнительную версию или версию исправления, отличную от указанной выше.

Подробные сведения о предварительно установленных платформах и средствах приведены в разделе [Особенности установленного программного обеспечения](#installed-software-specifics) ниже.

## <a name="modifications-to-a-codespace"></a>Изменения в codespace
 
После создания среды codespace любые изменения в ней сохраняются, пока экземпляр codespace доступен в GitHub Codespaces. Вы можете клонировать дополнительные репозитории, устанавливать средства и генераторы приложений, а также добавлять другие ресурсы разработки, и эти изменения будут сохраняться даже при приостановке действия codespace. Однако если удалить codespace, все изменения будут утеряны.

> [!NOTE]
> При удалении codespace все изменения в локальном репозитории codespace (ожидающие или зафиксированные) будут утеряны. Перед удалением codespace не забудьте отправить изменения из репозитория в удаленное расположение.

При подключении к codespace с помощью Visual Studio можно использовать терминал Visual Studio для выполнения программ командной строки. Вы можете использовать либо PowerShell, либо командную строку Windows. В обоих случаях требуются повышенные права учетной записи локального администратора. Дополнительные сведения о терминале Visual Studio см. в [блоге объявлений, связанных с терминалом Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/).

## <a name="customize-a-codespace"></a>Настройка codespace

Ценность GitHub Codespaces заключается в возможности создания уникальных, повторяемых сред разработки в облаке, адаптированных для вас и вашей команды. Используя как основу экземпляр GitHub Codespaces по умолчанию, можно настроить установленные в codespace компоненты.

В следующих разделах описаны два способа настройки codespace: с помощью файла *.devcontainer.json* и файла *.devinit.json*. Эти файлы позволяют настроить установленные в codespace платформы и средства. При добавлении в репозиторий любой пользователь, создающий codespace на основе вашего репозитория, будет получать одну и ту же удаленную среду разработки.

## <a name="customize-with-devcontainerjson"></a>Настройка с помощью devcontainer.json

При создании codespace GitHub Codespaces ищет файл [*devcontainers.json*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) в корне репозитория и использует параметры в нем для настройки среды codespace или подключающихся к ней клиентских экземпляров (браузерный редактор, Visual Studio или Visual Studio Code). Большинство параметров в файле *devcontainer.json* применяются к средам codespace на основе Linux или к двум другим клиентам, но доступны и параметры для codespace на основе Windows и Visual Studio.

Файл *devcontainer.json* можно поместить в репозитории в одном из двух мест:

1. *{корень-репозитория}/.devcontainer.json*
2. *{корень-репозитория}/.devcontainer/devcontainer.json*

GitHub Codespaces поддерживает указанные ниже свойства *devcontainer.json*. Настройка конкретных свойств Visual Studio Code полезна, если вы планируете подключаться к codespace не только с помощью Visual Studio, но и с помощью других клиентов. 

* `extensions` — массив расширений [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/vscode), которые необходимо установить.
* `settings` — набор [параметров Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings), которые следует применить.
* `forwardPorts` — порт или массив портов, для которых должна автоматически выполняться локальная переадресация при выполнении codespace.
* `postCreateCommand` — командная строка или список аргументов команды для выполнения после создания codespace.

> [!NOTE]
> Файлы **devcontainer.json** также используются для поддержки [удаленной разработки](https://code.visualstudio.com/docs/remote/remote-overview) в Visual Studio Code и имеют дополнительные свойства, не описываемые в этом документе. Эти дополнительные свойства можно добавить в файл, но они будут игнорироваться службой Codespaces. Дополнительные сведения см. в [справке по devcontainer.json](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) на сайте code.visualstudio.com.

## <a name="customize-with-devinit"></a>Настройка с помощью devinit

[devinit](../../devinit/getting-started-with-devinit.md) — это программа командной строки, включаемая в codespace на основе Windows и позволяющая устанавливать платформы и средства в среде. Ее можно запустить вручную из командной строки (`devinit run -t require-dotnetcoresdk`), но весь ее потенциал раскрывается при создании пользовательского файла [ *.devinit.json*](../../devinit/devinit-json.md) для единообразной настройки создаваемых сред codespace.

`devinit` включает набор средств для установки отдельных компонентов, таких как SQL Server и Azure CLI, а также запуска стандартных диспетчеров пакетов, таких как chocolatey, npm и vcpkg. Полный список средств `devinit` можно найти в документации по [доступным средствам](../../devinit/devinit-tool-list.md).

### <a name="devinitjson"></a>devinit.json

Хотя программу командной строки `devinit` можно запустить напрямую, мы рекомендуем создать файлы конфигурации [*devinit.json*](../../devinit/devinit-json.md), описывающие выполняемый набор средств `devinit`. 

Например, если нужно установить [пакет SDK для .NET Core](/dotnet/core/sdk), файл *.devinit.json* будет выглядеть следующим образом:

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

При создании файла *.devinit.json* в корне проекта он будет использоваться при запуске `devinit init`. По умолчанию `devinit.exe` ищет файл в следующих расположениях:

1. *{текущий-каталог}\\.devinit.json*
2. *{текущий-каталог}\\.devinit\devinit.json*

### <a name="running-devinit-when-creating-a-codespace"></a>Запуск devinit при создании codespace

Вы можете указать, что служба GitHub Codespaces должна запустить `devinit` после создания codespace, с помощью свойства `postCreateCommand` в файле *devcontainers.json*. Как упоминалось выше, GitHub Codespaces ищет файл *devcontainer.json* в клонированном репозитории, чтобы настроить codespace или экземпляр клиента, и выполняет все команды, указанные в свойстве `postCreateCommand`.

При указании `devinit init` `devinit` будет выполняться с использованием конфигурации из *devinit.json*.

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>Пример

Ниже приведен простой пример установки программы командной строки .NET Core Entity Framework `dotnet-ef`.

**devcontainer.json**

Содержимое файла *.devcontainer.json* в корне репозитория. 

```json
{
  "postCreateCommand": "devinit init"
}
```

**devinit.json**

Содержимое файла *.devinit.json*. Этот файл должен находиться в той же папке, что и *.devcontainer.json*.

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

Дополнительные примеры `devinit` можно найти в [списке примеров](../../devinit/sample-readme.md) `devinit`.

## <a name="port-forwarding"></a>перенаправление портов;

GitHub Codespaces предоставляет доступ к службам и приложениям, выполняющимся в удаленных средах, посредством переадресации портов. По умолчанию из соображений безопасности порты не переадресуются. Однако вы можете указать определенные порты, которые необходимо открыть в codespace.

### <a name="configure-port-forwarding"></a>Настройка перенаправления портов

Если для определенного репозитория необходимо по умолчанию переадресовывать один или несколько портов, соответствующую настройку можно осуществить в файле *devcontainer.json* с помощью свойства `forwardPorts`.

* `forwardPorts` — порт или массив портов, для которых должна автоматически выполняться локальная переадресация при выполнении среды.

## <a name="installed-software-specifics"></a>Особенности установленного программного обеспечения

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Microsoft SQL Server 2019 Express Edition доступен и работает как локальная служба (localdb) в среде codespace на основе Windows. Текущий пользователь, от имени которого выполняются приложение и терминал Visual Studio, имеет права администратора SQL в SQL Server. Для администрирования сервера необходимо использовать PowerShell в терминале Visual Studio или другие программы командной строки, такие как `dotnet-ef`. В настоящее время SQL Server Management Studio и другие средства удаленного администрирования недоступны.

#### <a name="example-connection-string"></a>Пример строки подключения

Ниже приведен пример строки подключения для локального сервера Microsoft SQL.

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Azure CLI

Интерфейс Azure CLI устанавливается во всех средах codespace на основе Windows и доступен по пути как `az`.

#### <a name="using-azure-resources"></a>Использование ресурсов Azure

Если вы используете удостоверение Azure Active Directory для проверки подлинности приложения в ресурсах Azure, необходимо сначала войти в Azure из терминала Visual Studio. Чтобы выполнить вход, используйте команду Azure CLI `login` с потоком входа устройства (как показано в примере ниже). После входа приложение и сеанс терминала должны иметь возможность использовать это удостоверение.

```powershell
> az login --use-device-code
```

Дополнительные сведения о команде `az login` см. в [документации по Azure CLI](/cli/azure/reference-index#az_login).

## <a name="see-also"></a>См. также раздел

- [Что такое GitHub Codespaces?](codespaces-overview.md)
- [Использование Visual Studio с codespace](use-visual-studio-with-codespaces.md)