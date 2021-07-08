---
description: Импортирует, экспортирует или сбрасывает параметры Visual Studio. расширение файла vssettings
title: Импорт и экспорт параметров - команда
ms.date: 05/28/2021
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
ms.openlocfilehash: dba50cf598c3c74f6c9407fbef5d55f938941a11
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687640"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Команда Импорт и экспорт параметров (файл .vssettings)

Импортирует, экспортирует или сбрасывает файл параметров Visual Studio, `.vssettings`.

Схема файла открыта. Чаще всего схема соответствует XML-структуре, в которой каждая категория является тегом, который может содержать теги подкатегорий. Эти теги подкатегорий могут содержать теги значений свойств. Хотя большинство пакетов использует общую структуру, любой пакет в Visual Studio может внести в файл произвольный XML с помощью схемы, которую он выбрал.

## <a name="syntax"></a>Синтаксис

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Коммутаторы

/export:`filename`

Необязательный элемент. Экспортирует текущие параметры в указанный файл

/import:`filename`

Необязательный элемент. Импортирует текущие параметры в указанный файл

/reset

Необязательный элемент. Сбрасывает текущие параметры

## <a name="remarks"></a>Remarks

Выполнение этой команды без параметров командной строки открывает мастер **Импорт и экспорт параметров**. Дополнительные сведения см. в статьях о [синхронизации параметров](../synchronized-settings-in-visual-studio.md) и [параметрах среды](../environment-settings.md).

## <a name="example"></a>Пример

Следующая команда экспортирует текущие параметры в файл `MyFile.vssettings`.

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```



## <a name="see-also"></a>См. также раздел

- [Параметры среды](../../ide/environment-settings.md)
- [Синхронизация параметров](../../ide/synchronized-settings-in-visual-studio.md)
- [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
