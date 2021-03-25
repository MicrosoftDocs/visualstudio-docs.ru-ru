---
title: Указание расположения файла VSPackage для оболочки VS | Документация Майкрософт
description: Узнайте, как можно сделать так, чтобы Visual Studio обнаружила библиотеку DLL сборки для загрузки VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: efec1ac3f7ccb3884265f3740108aaef261e9378
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064089"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Выбор расположения файла VSPackage к оболочке Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] должна иметь возможность размещать библиотеку DLL сборки для загрузки VSPackage. Его можно разместить различными способами, как описано в следующей таблице.

| Метод | Описание |
| - | - |
| Используйте раздел реестра CodeBase. | Ключ базы кода можно использовать для направления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загрузки сборки VSPackage из любого полного пути к файлу. Значение ключа должно быть путем к файлу DLL. Это лучший способ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загрузки сборки пакета. Этот метод иногда называют способом «каталог установки "база кода/частный"». Во время регистрации значение базы кода передается в классы атрибутов регистрации через экземпляр <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> типа. |
| Поместите DLL в каталог **PrivateAssemblies** . | Поместите сборку в подкаталог **PrivateAssemblies** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] каталога. Сборки, расположенные в **PrivateAssemblies** , обнаруживаются автоматически, но не отображаются в диалоговом окне " **Добавление ссылок** ". Различие между **PrivateAssemblies** и **"publicassemblies"** заключается в том, что сборки в **"publicassemblies"** перечисляются в диалоговом окне **Добавление ссылок** . Если вы решили не использовать методику «каталог установки "CodeBase/Private"», то следует установить в каталог **PrivateAssemblies** . |
| Используйте сборку со строгим именем и раздел реестра сборки. | Ключ сборки можно использовать для явного направления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загрузки сборки VSPackage со строгим именем. Значение ключа должно быть строгим именем сборки. |
| Поместите DLL в каталог **"publicassemblies"** . | Наконец, сборка также может быть помещена в подкаталог **"publicassemblies"** . Сборки, расположенные в **"publicassemblies"** , обнаруживаются автоматически и также отображаются в диалоговом окне **Добавление ссылок** в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> Сборки VSPackage должны размещаться в каталоге **"publicassemblies"** только в том случае, если они содержат управляемые компоненты, предназначенные для повторного использования другими разработчиками VSPackage. Большинство сборок не соответствует этому критерию. |

> [!NOTE]
> Используйте подписанные сборки со строгими именами для всех зависимых сборок. Эти сборки также должны быть установлены в собственном каталоге или глобальном кэше сборок (GAC). Это защищает от конфликтов с сборками, имеющими одинаковое имя базового файла, называемое привязкой слабого имени.
