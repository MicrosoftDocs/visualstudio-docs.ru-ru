---
title: Определение требований к системе | Документация Майкрософт
description: Узнайте, как настроить Microsoft установщик Windows для определения требований к системе, таких как установленный выпуск Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffb00ca42376f8b7c150552c862bba7a24a5c1fb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056770"
---
# <a name="detect-system-requirements"></a>Определение требований к системе
Пакет VSPackage не может работать, если не установлена Visual Studio. При использовании установщик Windows Майкрософт для управления установкой пакета VSPackage можно настроить установщик, чтобы определить, установлена ли Visual Studio. Кроме того, его можно настроить для проверки системы на наличие других требований, например конкретной версии Windows или определенного объема ОЗУ.

## <a name="detect-visual-studio-editions"></a>Обнаружение выпусков Visual Studio
 Чтобы определить, установлен ли выпуск Visual Studio, убедитесь, что значение раздела реестра **Install** — *(REG_DWORD) 1* в соответствующей папке, как указано в следующей таблице. Обратите внимание, что существует иерархия выпусков Visual Studio:

1. Предприятие

2. Professional

3. Сообщество

При установке более нового выпуска добавляются разделы реестра для этого выпуска, а также для более ранних выпусков. То есть если установлен выпуск Enterprise Edition, то для ключа **установки** устанавливается значение *1* для Enterprise, а также для выпусков Professional и Community. Поэтому необходимо проверить только наличие самой последней версии.

> [!NOTE]
> В 64-разрядной версии редактора реестра 32-разрядные ключи отображаются в разделе **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Ключи Visual Studio находятся в **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Продукт|Ключ|
|-------------|---------|
|Visual Studio Enterprise|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Оболочка Visual Studio 2015 (интегрированная и изолированная)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Определить, когда работает Visual Studio
 Невозможно правильно зарегистрировать VSPackage, если Visual Studio работает при установке VSPackage. Установщик должен определить, когда работает Visual Studio, а затем отказаться от установки программы. Установщик Windows не позволяет использовать записи таблицы для включения такого обнаружения. Вместо этого необходимо создать пользовательское действие следующим образом: использовать `EnumProcesses` функцию для обнаружения *devenv.exe* процесса, а затем либо задать свойство установщика, которое используется в условии запуска, либо условно отобразить диалоговое окно, предлагающее пользователю закрыть Visual Studio.

## <a name="see-also"></a>См. также
- [Установка пакетов VSPackage с помощью установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
