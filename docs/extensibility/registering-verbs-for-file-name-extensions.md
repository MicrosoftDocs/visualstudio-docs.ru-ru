---
title: Регистрация команд для расширений имен файлов | Документация Майкрософт
description: Узнайте, как зарегистрировать команду, связанную с программным идентификатором для расширения имени файла, с помощью ключа оболочки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c223dea7e265d8d040d502c99ded09380e89690f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901231"
---
# <a name="register-verbs-for-file-name-extensions"></a>Регистрация команд для расширений имен файлов
Сопоставление расширения имени файла с приложением обычно имеет предпочитаемое действие, которое происходит при двойном щелчке файла пользователем. Это предпочтительное действие связано с командой, например Open, которая соответствует действию.

 Вы можете зарегистрировать команды, связанные с программным идентификатором (ProgID) для расширения, с помощью ключа оболочки, расположенного по адресу **HKEY_CLASSES_ROOT \{ ProgID} \шелл**. Дополнительные сведения см. в разделе [типы файлов](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Регистрация стандартных команд
 Операционная система распознает следующие стандартные команды:

- Открыть

- Изменить

- Воспроизведение

- Печать

- Предварительный просмотр

  По возможности Зарегистрируйте стандартную команду. Наиболее распространенным выбором является команда Open. Используйте команду Edit, только если есть четкое различие между открытием файла и редактированием файла. Например, открытие файла *.htm* отображает его в браузере, в то время как редактирование файла *.htm* запускает редактор HTML. Стандартные команды локализованы с локальными языками операционной системы.

> [!NOTE]
> При регистрации стандартных команд не устанавливайте значение по умолчанию для открытого ключа. Значение по умолчанию содержит отображаемую строку в меню. Операционная система предоставляет эту строку для стандартных команд.

 Файлы проекта должны быть зарегистрированы для запуска нового экземпляра, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] когда пользователь открывает файл. В следующем примере показана стандартная Регистрация команд для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] проекта.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Чтобы открыть файл в существующем экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , зарегистрируйте ключ ддиксек. В следующем примере показана стандартная регистрация для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *CS* -файла.

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Задание глагола по умолчанию
 Глагол по умолчанию — это действие, выполняемое, когда пользователь дважды щелкает файл в проводнике Windows. Глагол по умолчанию — это команда, указанная в качестве значения по умолчанию для **HKEY_CLASSES_ROOT \\ *ProgID*\шелл** Key. Если значение не указано, команда по умолчанию является первой командой, указанной в списке **HKEY_CLASSES_ROOT \\ *ProgID*\шелл** Key.

> [!NOTE]
> Если вы планируете изменить глагол по умолчанию для расширения в параллельном развертывании, учитывайте влияние на установку и удаление. Во время установки исходное значение по умолчанию перезаписывается.

## <a name="see-also"></a>См. также
- [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md)
