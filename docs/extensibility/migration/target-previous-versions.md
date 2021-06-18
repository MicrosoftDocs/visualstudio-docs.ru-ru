---
title: Целевая версия Visual Studio 2019 при создании расширения в предварительной версии Visual Studio 2022
description: Узнайте, как сделать расширение Visual Studio работать с Visual Studio 2019, если вы создадите проект с помощью предварительной версии Visual Studio 2022.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: dcf556e271e6a805110eac0c978a845f2195e28f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308646"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>Нацеливание на предыдущую версию при создании расширения в предварительной версии Visual Studio 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

При создании нового проекта VSIX с помощью предварительной версии Visual Studio 2022 проект создается на основе шаблона, предназначенного для Visual Studio 2022. Если вы хотите ориентироваться на Visual Studio 2019 или более раннюю версию, необходимо изменить созданный проект.

Рассмотрите возможность использования [общих проектов](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) для visual Studio 2019 и visual Studio 2022 при совместном использовании всего или всего кода в расширении.

Выполните следующие действия в проекте VSIX, который должен ориентироваться на Visual Studio 2019:

1. Измените `source.extension.vsixmanifest` файл, чтобы удалить `ProductArchitecture` элемент и диапазон версий:

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   Также обновите необходимое условие:

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    Проверьте файл на наличие других обновлений, которые могут потребоваться.

1. Измените версии пакетов SDK VS, на которые вы ссылаетесь в файле проекта:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
