---
title: Поддержка .NET Core
description: В этом документе перечислены версии .NET Core, поддерживаемые Visual Studio для Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: a04d15fc2fc768c2d6896396df5dc0f134d1720b
ms.sourcegitcommit: 67f3bdeee583a4fb41cacc7f38839a737bfecc6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2021
ms.locfileid: "105735529"
---
# <a name="net-core-support"></a>Поддержка .NET Core

В следующей таблице перечислены версии .NET Core, поддерживаемые в стабильных и предварительных версиях Visual Studio для Mac.

| Версия пакета SDK для .NET Core |Visual Studio для Mac 8.1 | Visual Studio для Mac 8.2 | Visual Studio для Mac 8.3 | Visual Studio для Mac 8.4 | Visual Studio для Mac 8.5 | Visual Studio для Mac 8.6 |
|---------|---------|---------|---------|---------|---------|---------|
|Версии 2.1.0–2.1.5xx | | | | | | |
|Версия 2.1.600 или последующая |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|Версии 2.2.1–2.2.1xx | | | | | | |
|Начиная с версии 2.2.200 |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|✔︎|✔︎|
|Версия 3.1 | | | |✔︎|✔︎|✔︎|
|Версия 5.0 | | | | | |✔︎|

> [!IMPORTANT]
> Предварительные версии пакета SDK для .NET Core не поддерживаются. Обновите пакет до выпущенной версии. При установке Visual Studio для Mac 8.4 будет установлена выпущенная версия .NET Core 3.1.

> [!IMPORTANT]
> Если вы ранее использовали .NET Core версии 2.2.1xx с Visual Studio для Mac 8.0, необходимо вручную выполнить обновление до поддерживаемой версии .NET Core, как указано в таблице выше. Рекомендуется версия [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) или [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2).

* Для версий 8.4, 8.5 и 8.6 по умолчанию устанавливается .NET Core 3.1.
* Для версии 8.3 по умолчанию устанавливается .NET Core 3.0.
* Установщик по умолчанию устанавливает .NET Core версии 2.1.701 (v2.1.700 для 8.1).
* Чтобы скачать любую другую версию .NET Core, посетите [страницу dotnet](https://dotnet.microsoft.com/download/dotnet-core).
* При использовании .NET Core 3.0 по умолчанию используется версия C# 8. C# 7.3 — это версия по умолчанию при использовании .NET Core 2.x. Дополнительные сведения см. в статье [Управление версиями языка C#](/dotnet/csharp/language-reference/configure-language-version).
* Сведения об установке предварительной версии Visual Studio для Mac см. в [этом руководстве](./install-preview.md).