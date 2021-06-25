---
title: Служебная программа CreatePkgDef | Документация Майкрософт
description: Узнайте о служебной программе CreatePkgDef, которая принимает файл .dll для расширения Visual Studio в качестве параметра и создает pkgdef-файл, сопровождающий файл .dll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bfbd4b42d9ceddd40e08c28926a59aecba719fe9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898127"
---
# <a name="createpkgdef-utility"></a>Служебная программа CreatePkgDef
Принимает файл .dll для расширения Visual Studio в качестве параметра и создает *pkgdef* -файл, сопровождающий файл *.dll* . Файл *pkgdef* содержит все данные, которые в противном случае были бы записаны в системный реестр при установке расширения.

> [!NOTE]
> Большинство шаблонов проектов, включенных в пакет SDK для Visual Studio, автоматически создают файлы *pkgdef* в рамках процесса сборки. Этот документ предназначен для тех, кто хочет создавать пакеты вручную, или преобразовать существующие пакеты для развертывания *. pkgdef*  .

## <a name="syntax"></a>Синтаксис

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Аргументы
**/out = &lt; имя файла&gt;**\
Обязательный. Задает имя файла выходных данных *. pkgdef* &lt; &gt; .

**/CodeBase**\
Необязательный элемент. Принудительная регистрация с помощью служебной программы **CodeBase** .

**/Assembly**\
Принудительная регистрация с помощью служебной программы **сборки** .

**&lt;AssemblyPath&gt;**\
Путь к файлу *.dll* , из которого необходимо создать *pkgdef*.

## <a name="remarks"></a>Remarks
Развертывание расширения с помощью файлов *pkgdef* заменяет требования к реестру в более ранних версиях Visual Studio.

::: moniker range=">=vs-2019"

Файлы *pkgdef* должны быть установлены в одном из следующих расположений:

- *%Локалаппдата%\микрософт\висуал Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Если папка установки — *%Локалаппдата%\микрософт\висуал Studio\16.0\Extensions \\*, расширение распознается Visual Studio, но по умолчанию отключено. Пользователь может включить расширение, используя **Управление расширениями**.

Если папка установки — *%vsinstalldir%\Common7\IDE\Extensions \\*, расширение включено по умолчанию.

> [!NOTE]
> Средство **Управление расширениями** не может использоваться для доступа к расширению, если оно не установлено как часть пакета VSIX.

::: moniker-end

::: moniker range="vs-2017"

Файлы *pkgdef* должны быть установлены в одном из следующих расположений:

- *%Локалаппдата%\микрософт\висуал Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Если папка установки — *%Локалаппдата%\микрософт\висуал Studio\15.0\Extensions \\*, расширение распознается Visual Studio, но по умолчанию отключено. Пользователь может включить расширение с помощью **расширений и обновлений**.

Если папка установки — *%vsinstalldir%\Common7\IDE\Extensions \\*, расширение включено по умолчанию.

> [!NOTE]
> Средство " **расширения и обновления** " нельзя использовать для доступа к расширению, если оно не установлено как часть пакета VSIX.

::: moniker-end

## <a name="see-also"></a>См. также
- [Служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
