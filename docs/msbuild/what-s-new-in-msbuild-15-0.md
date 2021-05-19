---
title: Новые возможности MSBuild 15 | Документация Майкрософт
description: Здесь приведены измененные, обновленные и новые функции MSBuild 15, доступные для пакета SDK для .NET Core и для создания проектов .NET Core в Windows, macOS и Linux.
ms.custom: SEO-VS-2020
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: e0fe78e781af4f2fafa52a230036bc20b657fd8e
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848270"
---
# <a name="whats-new-in-msbuild-15"></a>Новые возможности в MSBuild 15

MSBuild теперь предоставляется в составе [основного пакета SDK .NET](https://www.microsoft.com/net/download/core). Проекты на базе .NET Core можно создавать в Windows, macOS и Linux.

## <a name="changed-path"></a>Измененный путь

 Теперь MSBuild устанавливается в папку в пути установки каждой версии Visual Studio. Например, *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. Для поиска MSBuild можно использовать следующий модуль PowerShell: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 Теперь MSBuild не регистрируется в глобальном кэше сборок. Чтобы обратиться к MSBuild программным образом, используйте пакеты NuGet. См. подробнее об [обновлении существующего приложения для использования MSBuild 15.0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Измененные свойства

 В связи с выходом нового номера версии изменены следующие свойства MSBuild.

- `MSBuildToolsVersion` для этой версии средств имеет значение 15.0. Версия сборки имеет значение 15.1.0.0.

- `MSBuildToolsPath` теперь не имеет фиксированного расположения. По умолчанию он находится в папке *MSBuild\15.0\Bin* относительно расположения для установки Visual Studio, но расположение для установки Visual Studio можно изменить во время установки.

- Значения `ToolsVersion` теперь не сохраняются в реестре.

- Свойства `SDK35ToolsPath` и `SDK40ToolsPath` указывают на пакет SDK для платформы .NET Framework, поставляемый с соответствующей версией Visual Studio (например, 10.0A для инструментов 4.X).

## <a name="updates"></a>Обновления

- В элемент [Project](../msbuild/project-element-msbuild.md) добавлен атрибут `SDK`. Также атрибут `Xmlns` стал необязательным. Дополнительные сведения об использовании атрибута `SDK` см в статьях [Информация об использовании пакетов SDK проекта MSBuild](../msbuild/how-to-use-project-sdk.md), [Пакеты, метапакеты и платформы](/dotnet/core/packages) и [Дополнения к формату CSPROJ для .NET Core](/dotnet/core/tools/csproj).
- Для внешних целевых объектов элемента [Item](../msbuild/item-element-msbuild.md) добавлен атрибут `Update`. Кроме того, снято ограничение на атрибут `Remove`.
- Пользовательский файл *Directory.Build.props* содержит настройки персонализации для проектов в своем каталоге. Этот файл автоматически импортируется из *Microsoft.Common.props*, если свойству `ImportDirectoryBuildTargets` не задано значение **false**. *Directory.Build.targets* импортируется с помощью *Microsoft.Common.targets*.
- Все метаданные с именами, которые не противоречат текущему списку атрибутов, можно по желанию разработчика выразить в виде атрибута. Дополнительные сведения см. в [этой статье](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Новые функции свойств

- `EnsureTrailingSlash` добавляет завершающую косую черту к пути, если она отсутствует.
- `NormalizePath` объединяет элементы пути и проверяет, что выходная строка имеет правильные знаки разделения для каталогов, используемые в текущей операционной системе.
- `NormalizeDirectory` объединяет элементы пути, добавляет косую черту при необходимости и проверяет, что выходная строка имеет правильные знаки разделения для каталогов, используемые в текущей операционной системе.
- `GetPathOfFileAbove` возвращает путь к файлу, непосредственно предшествующему данному. Она функционально эквивалентна вызову такой инструкции: `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>См. также раздел

- [MSBuild](../msbuild/msbuild.md)
