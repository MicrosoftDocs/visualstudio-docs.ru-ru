---
title: -ResetSettings (devenv.exe)
description: Узнайте, как использовать параметр командной строки ResetSettings devenv для восстановления параметров Visual Studio по умолчанию и автоматического запуска интегрированной среды разработки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e523738ff23b40c80b5df21d90b582d94c59087f
ms.sourcegitcommit: a8031c1387d2090129ed33e063744f9f31653dcd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2021
ms.locfileid: "110724542"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Восстанавливает параметры по умолчанию Visual Studio и автоматически запускает интегрированную среду разработки Visual Studio. При необходимости выполняет сброс параметров в соответствии с указанным файлом параметров (`*.vssettings`).

Параметры определяются профилем, который был выбран при первом запуске Visual Studio.

> [!TIP]
> Дополнительные сведения о сбросе параметров с помощью интегрированной среды разработки (IDE) см. в разделе [Сброс параметров](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Синтаксис

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Аргументы

- *SettingsFile*

  Необязательный параметр. Полный путь и имя файла `.vssettings`, применяемого к Visual Studio.

- *DefaultCollectionSpecifier*

  Необязательный параметр. Описатель, представляющий коллекцию параметров для восстановления по умолчанию. Выберите один из перечисленных в таблице описателей коллекции по умолчанию.

  | Имя коллекции по умолчанию | Описатель коллекции |
  | --- | --- |
  | **Общие** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Веб-разработка** | `Web` |
  | **Веб-разработка (только код)** | `WebCode` |

## <a name="remarks"></a>Комментарии

Если файл *SettingsFile* не указан, интегрированная среда разработки открывается с использованием существующих параметров. 


## <a name="example"></a>Пример

Первый пример применяет параметры, сохраненные в файле `MySettings.vssettings`.

Второй пример восстанавливает профиль Visual C# по умолчанию.

Третий пример также будет закрывать Visual Studio после применения параметров. Можно добавить `/Command "File.Exit"`.

```shell
devenv /ResetSettings "%USERPROFILE%\MySettings.vssettings"

devenv /ResetSettings CSharp

devenv /NoSplash /ResetSettings General /Command Exit 
```

## <a name="see-also"></a>См. также раздел

- [Параметры среды](../environment-settings.md)
- [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
