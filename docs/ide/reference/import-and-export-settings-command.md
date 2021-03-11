---
description: Импортирует, экспортирует или сбрасывает параметры Visual Studio.
title: Импорт и экспорт параметров - команда
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f2ea4811af2c44277b9a6dc285972c5267b28d7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223681"
---
# <a name="import-and-export-settings-command"></a>Импорт и экспорт параметров - команда

Импортирует, экспортирует или сбрасывает параметры Visual Studio.

## <a name="syntax"></a>Синтаксис

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Коммутаторы

/export:`filename`

Необязательный параметр. Экспортирует текущие параметры в указанный файл

/import:`filename`

Необязательный параметр. Импортирует текущие параметры в указанный файл

/reset

Необязательный параметр. Сбрасывает текущие параметры

## <a name="remarks"></a>Комментарии

Выполнение этой команды без параметров командной строки открывает мастер **Импорт и экспорт параметров**. Дополнительные сведения см. в статьях о [синхронизации параметров](../synchronized-settings-in-visual-studio.md) и [параметрах среды](../environment-settings.md).

## <a name="example"></a>Например, .

Следующая команда экспортирует текущие параметры в файл `MyFile.vssettings`.

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>См. также раздел

- [Параметры среды](../../ide/environment-settings.md)
- [Синхронизация параметров](../../ide/synchronized-settings-in-visual-studio.md)
- [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
