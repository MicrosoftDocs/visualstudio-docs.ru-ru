---
title: Пользовательские параметры решения (. Suo), файл | Документация Майкрософт
description: Сведения о файле параметров пользователя решения (. suo), содержащем параметры решения "на пользователя" в структурированном файле хранилища, который хранится в двоичном формате.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a38eb865cf003f7a2f9bafde7b6e527ce24f2bd
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899619"
---
# <a name="solution-user-options-suo-file"></a>Файл параметров пользователя решения (SUO-файл)
Файл параметров пользователя решения (. suo) содержит параметры решения "на пользователя". Этот файл не должен быть возвращен в систему управления исходным кодом.

 Файл пользовательских параметров решения (SUO) представляет собой структурированное хранилище или составной файл, хранящийся в двоичном формате. Сведения о пользователе сохраняются в потоках с именем, которое является ключом, который будет использоваться для обнаружения информации в SUO. Файл параметров пользователя решения используется для хранения параметров настройки пользователя и создается автоматически при сохранении решения в Visual Studio.

 Когда среда открывает suo-файл, она перечисляет все загруженные пакеты VSPackage. Если пакет VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> метод для пакета VSPackage, запрашивающий загрузку всех своих данных из файла SUO.

 Это обязанность VSPackage, чтобы узнать, какие потоки были записаны в suo-файл. Для каждого потока, который он написал, пакет VSPackage обращается к среде с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> для загрузки определенного потока, определяемого ключом, который является именем потока. Затем среда выполняет обратный вызов VSPackage, чтобы прочитать конкретный поток, передающий имя потока и `IStream` указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> метод.

 На этом этапе выполняется еще один вызов, позволяющий `LoadUserOptions` определить, существует ли другой раздел suo-файла для чтения. Этот процесс продолжится до тех пор, пока все потоки данных в файле SUO не будут считаны и обработаны средой.

 При сохранении или закрытии решения среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> метод с указателем на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> метод. Объект `IStream` , содержащий сохраняемые двоичные данные, передается в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> метод, который затем записывает сведения в suo-файл и вызывает `SaveUserOptions` метод еще раз, чтобы проверить наличие другого потока данных для записи в suo-файл.

 Эти два метода `SaveUserOptions` и `WriteUserOptions` вызываются рекурсивно для каждого потока данных, сохраняемых в файле SUO, передавая указатель на `IVsSolutionPersistence` . Они вызываются рекурсивно, чтобы разрешить запись нескольких потоков в файл. suo. Таким образом, сведения о пользователе сохраняются в решении и гарантированно будут в следующий раз при открытии решения.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Решения](../../extensibility/internals/solutions-overview.md)
