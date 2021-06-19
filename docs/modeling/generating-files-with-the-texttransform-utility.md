---
title: Создание файлов с помощью служебной программы TextTransform
description: Узнайте, как служебная программа TextTransform является средством командной строки, которое можно использовать для преобразования текстового шаблона.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 743b7deb118bb3506773ec1a82d2331633afa7bc
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388832"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Создание файлов с помощью служебной программы TextTransform

TextTransform.exe — это программа командной строки, которую можно использовать для преобразования текстового шаблона. При вызове TextTransform.exe необходимо указать имя файла текстового шаблона в качестве аргумента. TextTransform.exe вызывает модуль преобразования текста и обрабатывает текстовый шаблон. TextTransform.exe обычно вызывается из скриптов. Однако обычно это не требуется, так как можно выполнить преобразование текста в Visual Studio или в процессе сборки.

> [!NOTE]
> Если вы хотите выполнить преобразование текста как часть процесса сборки, рассмотрите возможность использования задачи преобразования текста MSBuild. Дополнительные сведения см. [в разделе Создание кода в процессе сборки](../modeling/code-generation-in-a-build-process.md). На компьютере, на котором установлена Visual Studio, можно также написать расширение приложения или Visual Studio, которое может преобразовывать текстовые шаблоны. Дополнительные сведения см. [в разделе Обработка текстовых шаблонов с помощью пользовательского узла](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform.exe находится в следующем каталоге:

::: moniker range=">=vs-2019"

**\Program Files (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

для выпуска Professional Edition или

**\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

для выпуска Enterprise Edition.

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

для выпуска Professional Edition или

**\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

для выпуска Enterprise Edition.

В предыдущих версиях Visual Studio файл находится в следующем расположении:

**\Program Files (x86) \Common Files\Microsoft Шаред\тексттемплатинг \{ версия}**

где {Version} зависит от установленной предыдущей версии.

::: moniker-end

## <a name="syntax"></a>Синтаксис

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Параметры

|**Argument**|**Описание**|
|-|-|
|`templateName`|Определяет имя файла шаблона, который требуется преобразовать.|

|**Параметр**|**Описание**|
|-|-|
|**-out**\<filename>|Файл, в который записывается выходные данные преобразования.|
|**-r**\<assembly>|Сборка, используемая для компиляции и выполнения текстового шаблона.|
|**-u**\<namespace>|Пространство имен, используемое для компиляции шаблона.|
|**-I**\<includedirectory>|Каталог, содержащий текстовые шаблоны, содержащиеся в указанном текстовом шаблоне.|
|**-P**\<referencepath>|Каталог для поиска сборок, указанных в текстовом шаблоне, или для использования параметра **-r** .<br /><br /> Например, чтобы включить сборки, используемые для Visual Studio API, используйте<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-DP** \<processorName> ! \<className>\<assemblyName&#124;codeBase>|Имя, полное имя типа и сборка обработчика директив, которые могут использоваться для обработки пользовательских директив в текстовом шаблоне.|
|**-a** [процессорнаме]! [Директивенаме]! \<parameterName> !\<parameterValue>|Укажите значение параметра для обработчика директив. Если указать только имя и значение параметра, параметр будет доступен для всех процессоров директив. Если указан процессор директив, параметр доступен только для указанного процессора. Если указать имя директивы, параметр будет доступен только при обработке указанной директивы.<br /><br /> Чтобы получить доступ к значениям параметров из обработчика директив или текстового шаблона, используйте [итексттемплатинженгинехост. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). В текстовом шаблоне включите `hostspecific` в директиву шаблона и вызовите сообщение в `this.Host` . Пример:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Всегда вводите метки "!", даже если опустить необязательные имена процессора и директивы. Пример.<br /><br /> `-a !!param!value`|
|**-h**|Предоставляет справку.|

## <a name="related-topics"></a>Связанные темы

|Задача|Раздел|
|-|-|
|Создание файлов в решении Visual Studio.|[Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Написание процессоров директив для преобразования собственных источников данных.|[Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)|
|Напишите узел текстовых шаблонов, который позволяет вызывать текстовые шаблоны из собственного приложения.|[Обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md)|
