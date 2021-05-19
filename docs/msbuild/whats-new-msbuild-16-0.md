---
title: Новые возможности MSBuild 16.0 | Документация Майкрософт
description: Сведения об измененных и обновленных функциях и свойствах для MSBuild 16.0, а также ссылки на заметки о выпуске.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: cdfb552c53a40b6ad2f2349556396475926900be
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848257"
---
# <a name="whats-new-in-msbuild-160"></a>Новые возможности в MSBuild 16.0

В этой статье описываются обновленные возможности и свойства MSBuild 16.0. Подробные заметки о выпуске см. в статье [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Измененный путь

 MSBuild устанавливается в папку *\Current* каждой версии Visual Studio, а исполняемые файлы находятся в подпапке *\Bin*. Например, путь к *MSBuild.exe* установленному с помощью сообщества Visual Studio 2019 — *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe*. Для поиска MSBuild можно также использовать модуль PowerShell: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Измененные свойства

 В связи с выходом нового номера версии изменены следующие свойства MSBuild.

- `MSBuildToolsVersion` для этой версии средств считается текущей. Версия сборки имеет такой же номер, как и Visual Studio 2017, т. е. 15.1.0.0.

- `VisualStudioVersion` для этой версии средств имеет значение 16.0.

## <a name="change-waves"></a>Изменение волн

Начиная с MSBuild 16.8 можно указать, следует ли явно отказаться от определенных изменений MSBuild, которые могут привести к нарушению работы. См. раздел [Волны изменений](change-waves.md).

## <a name="updates"></a>Обновления

MSBuild и Visual Studio теперь по умолчанию создают код для .NET Framework 4.7.2. Если вы хотите использовать новые функции API MSBuild, необходимо также обновить сборку, но существующий код будет продолжать работать.

## <a name="see-also"></a>См. также

- [MSBuild](../msbuild/msbuild.md)
