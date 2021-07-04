---
title: Примеры параметров командной строки для установки
description: Настройте эти примеры, чтобы произвести собственную установку Visual Studio из командной строки.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5685de34235dcd9b903cbf5be6371ebf3f1e84c3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307548"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Примеры параметров командной строки для установки Visual Studio

Чтобы проиллюстрировать [использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md) на практике, здесь приводится несколько примеров, которые вы можете настроить в соответствии с требуемыми задачами.

В каждом примере `vs_enterprise.exe`, `vs_professional.exe` и `vs_community.exe` представляет собой соответствующий выпуск небольшой программы начальной загрузки Visual Studio (размер файла около 1 МБ), которая запускает процесс скачивания. Если вы используете другой выпуск, выберите соответствующую программу начальной загрузки.

> [!NOTE]
> Для выполнения всех команд требуются повышенные права администратора. Если запустить процесс с другими правами, появится запрос системы контроля учетных записей пользователей.
>
> [!NOTE]
> Чтобы объединить несколько строк в одну команду, используйте символ `^` в конце командной строки. Кроме того, можно просто поместить эти строки в одну строку. В PowerShell вместо этого используется символ обратного апострофа (`` ` ``).

Список рабочих нагрузок и компонентов, которые можно установить с помощью командной строки, см. в статье [Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017](workload-and-component-ids.md).

## <a name="using---installpath"></a>Использование параметра --installPath

* Установите минимальный экземпляр Visual Studio без интерактивных запросов с отображением хода выполнения процесса:

  ```shell
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Обновите экземпляр Visual Studio с помощью командной строки без интерактивных запросов но с отображением хода выполнения процесса:

   ```shell
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Рекомендуются обе команды. Первая команда обновляет Visual Studio Installer. Первая команда обновляет экземпляр Visual Studio. Чтобы избежать появления диалогового окна "Контроль учетных записей", запустите командную строку с правами администратора.

* Выполните автоматическую установку экземпляра Visual Studio для настольных ПК с французским языковым пакетом. Управление должно возвращаться только после завершения установки продукта.

  ```shell
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Использование параметра --wait

* Этот параметр используется в пакетных файлах или скриптах для указания того, что нужно дождаться завершения работы установщика Visual Studio, прежде чем выполнять следующую команду. При использовании пакетных файлов переменная среды `%ERRORLEVEL%` будет содержать значение, возвращаемое командой, как описано в статье [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md). Некоторые программы командной строки требуют указания дополнительных параметров для ожидания завершения работы и получения возвращаемого значения установщика. Ниже приведен пример дополнительных параметров, используемых в команде скрипта PowerShell Start-Process:

   ```shell
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $process = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   Write-Output $process.ExitCode 
   ```

   или

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* Первый параметр, --wait, используется Visual Studio Installer, а второй, -Wait, — скриптом Start-Process для ожидания завершения работы. Параметр -PassThru используется скриптом Start-Process для получения возвращаемого значения с помощью кода выхода установщика.

## <a name="using---layout"></a>Использование параметра --layout

* Загрузите базовый редактор Visual Studio (минимальная конфигурация Visual Studio). Включите только английский языковой пакет:

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Скачайте среду .NET для настольного ПК и рабочие нагрузки .NET, а также все рекомендуемые компоненты и расширение GitHub. Включите только английский языковой пакет:

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Использование параметра --all

* Запустите интерактивную установку всех рабочих нагрузок и компонентов, доступных для выпуска Visual Studio Enterprise:

   ```shell
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Использование параметра --includeRecommended

* Установите второй именованный экземпляр Visual Studio Professional на компьютер с уже установленным выпуском Visual Studio Community с поддержкой разработки на Node.js:

   ```shell
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Использование параметра --remove

::: moniker range="vs-2017"

* Удалите компонент средств профилирования из установленного по умолчанию экземпляра Visual Studio:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Удалите компонент средств профилирования из установленного по умолчанию экземпляра Visual Studio:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range=">=vs-2022"

* Удалите компонент средств профилирования из установленного по умолчанию экземпляра Visual Studio:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Использование параметра --path

::: moniker range="vs-2017"

Эти параметры командной строки **впервые добавлены в версии 15.7**. Дополнительные сведения об их использовании см. в статье [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

* Указание пути для файлов установки, кэша и общих файлов:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Указание только пути для файлов установки и кэша:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Указание только пути для общих файлов:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Указание только пути для файлов установки:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Использование export

::: moniker range="vs-2017"

Эта команда командной строки **появилась в 15.9**. Дополнительные сведения см. в статье [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

* Использование export для сохранения выбранного компонента из установки:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Использование export для сохранения пользовательского выбранного компонента с нуля:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Использование --config

::: moniker range="vs-2017"

Этот параметр командной строки **появился в 15.9**. Дополнительные сведения см. в статье [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

* Использование --config для установки рабочих нагрузок и компонентов из ранее сохраненного файла конфигурации установки:

  ```shell
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Использование --config для добавления рабочих нагрузок и компонентов а существующую установку:

  ```shell
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
