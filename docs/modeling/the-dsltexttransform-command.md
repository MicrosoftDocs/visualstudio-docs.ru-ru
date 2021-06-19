---
title: Команда DslTextTransform
description: Узнайте, что Дслтексттрансформ. cmd — это сценарий, который вызывает TextTransform.exe и запускает его с общими параметрами.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65d1e1d02c5b7d13c2e86343c6307306542d00e2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388650"
---
# <a name="the-dsltexttransform-command"></a>Команда DslTextTransform
Дслтексттрансформ. cmd — это скрипт, который вызывает TextTransform.exe и запускает его с общими параметрами. Дслтексттрансформатион. cmd можно использовать для автоматизации сборки проектов в ночное время [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Дополнительные сведения см. [в разделе Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 Дслтексттрансформ. cmd находится в следующем каталоге:

 **\<Visual Studio SDK Installation Path>\висуалстудиоинтегратион\тулс\бин**

 Можно указать следующие аргументы в качестве входных данных для Дслтексттрансформ. cmd:

- Выходной каталог проекта модели предметной области.

- Выходной каталог проекта определения конструктора.

- Расположение файла текстового шаблона.

  Дслтексттрансформ. cmd обрабатывает указанный файл текстового шаблона с помощью процессоров директив по умолчанию и сборок. При создании пользовательских обработчиков директив можно создать собственный пакетный файл, который вызывает TextTransform.exe. В этом пакетном файле можно указать сборки и связанные с ними обработчики пользовательских директив.
