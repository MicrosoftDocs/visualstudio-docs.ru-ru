---
title: Поиск Visual Studio | Документация Майкрософт
description: Можно установить несколько экземпляров одной и той же версии Visual Studio. Узнайте, как использовать API-интерфейс запросов COM для поиска нужного экземпляра.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: cd0fcd294983d6a6567676f06703b4bd1dd376c4
ms.sourcegitcommit: b4cc3dee59421f7089112becf128a369acadaf61
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2021
ms.locfileid: "112990510"
---
# <a name="locate-visual-studio"></a>Расположение Visual Studio

Начиная с Visual Studio 2017 можно установить несколько экземпляров одной и той же версии или даже выпуска. Это полезно, если вы хотите предварительно просмотреть новые функциональные возможности на основном компьютере разработки, сохранив при этом предыдущую установку. Из-за этих изменений не существует одной переменной среды или значения реестра, которые можно использовать для нахождение экземпляра. Вместо этого можно использовать [API-интерфейс запросов com](/dotnet/api/microsoft.visualstudio.setup.configuration) для поиска экземпляров на основе критериев, относящихся к вашему расширению.

Это быстрый API-интерфейс только для чтения с пакетами NuGet, доступными для машинного и управляемого кода.

| Код | Package |
| ---- | --- |
| Собственный | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Управляемые | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Можно выбрать один экземпляр с учетом пути или текущего процесса или перечислить все экземпляры. Ознакомьтесь с [нашими примерами](https://github.com/Microsoft/vs-setup-samples) для получения полных примеров того, как найти Visual Studio.

## <a name="tools"></a>Инструменты

Для поиска Visual Studio и других средств в средах сборки, сценариев PowerShell, установщиков и других сценариев существует ряд средств с открытым кодом, которые можно использовать напрямую или распространять вместе с собственными скриптами.

| Проект | Описание |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Собственный исполняемый файл с одним файлом для поиска экземпляров, таких как выпуск или предварительная версия, установка продукта и устанавливаемые рабочие нагрузки. Также поддерживает поиск Visual Studio 2010 и более новых версий, хотя для Visual Studio 2017 и более поздних версий возвращается меньше информации. Примеры см. на [вики-сайте](https://github.com/Microsoft/vswhere/wiki) . |
| [Командлеты VSSetup](https://github.com/Microsoft/vssetup.powershell) | Командлеты PowerShell поддерживают 2,0 и более поздние версии, возвращающие подробные сведения в виде объектов, которые можно использовать для поиска экземпляров на основе тех же условий, что и _vswhere_ , а также для обнаружения еще более свойств экземпляров. Примеры см. на [вики-сайте](https://github.com/Microsoft/vssetup.powershell/wiki) . |
| [всиксбутстраппер](https://github.com/Microsoft/vsixbootstrapper) | Автоматически находит _всиксинсталлер_ и передает командную строку, чтобы установить *VSIX* -файл. Эта функция может быть полезна в установщиках, которые не поддерживают прямую поддержку интерфейсов API запросов. Примеры см. на [вики-сайте](https://github.com/Microsoft/vsixbootstrapper/wiki) . |

## <a name="see-also"></a>См. также

* [Изменения в программе установки Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Запуск Visual Studio с помощью DTE](launch-visual-studio-dte.md)
