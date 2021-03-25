---
title: Поддержка NGen в VSIX v3 | Документация Майкрософт
description: Узнайте, как включить генератор образов в машинном кодах — инструмент, который разработчики расширений могут использовать для повышения производительности управляемых приложений.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0f8de3b662875a4af0423930eecfdd77e4e05b08
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090594"
---
# <a name="ngen-support-in-vsix-v3"></a>Поддержка NGen в VSIX v3

С помощью Visual Studio 2017 и нового формата манифеста расширения VSIX v3 (версия 3) разработчики расширений теперь могут "NGen" их сборки во время установки.

Ниже приведен фрагмент из MSDN, в котором объясняется, что делает NGen:

>Генератор образов в машинном кодах (*Ngen.exe*) — это средство, которое повышает производительность управляемых приложений. *Ngen.exe* создает образы в машинном коде, которые являются файлами, содержащими скомпилированный для конкретного процессора машинный код, и устанавливают их в кэш образов в машинном коде на локальном компьютере. Среда выполнения может использовать образы в машинном коде, находящиеся в кэше, вместо использования JIT-компилятора для компиляции исходной сборки.
>
>от [Ngen.exe (генератор образов в машинном код)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Чтобы "NGen" сборку, необходимо установить VSIX "для каждого экземпляра на компьютер". Это можно включить, установив флажок "все пользователи" в `extension.vsixmanifest` конструкторе:

![Проверка всех пользователей](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Включение Ngen

Чтобы включить генератор NGen для сборки, можно использовать окно **Свойства** в Visual Studio.

Можно задать 4 свойства.

1. **NGen** (логическое значение) — Если значение true, установщик Visual Studio будет "NGen" сборкой.
2. **NGen Application** (строка) — NGen предоставляет возможность использовать файл *app.config* приложения для разрешения зависимостей сборки. Это значение должно быть задано для приложения, *app.config* необходимо использовать (относительно каталога установки Visual Studio).
3. **Архитектура NGen** (enum) — архитектура для компиляции сборки в собственном коде. Возможные варианты: a. NotSpecified б. X86 c. X64 d. Все
4. **Приоритет NGen** (целое число от 1 до 3). уровень приоритета NGen задокументирован на [Ngen.exe уровнях приоритета](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Вот как выглядит окно **свойств** в действии:

![свойства Ngen](media/ngen-in-properties.png)

Это приведет к добавлению метаданных в ссылку на проект в файле *. csproj* проекта VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Файл. csproj можно изменить непосредственно, если предпочитаете.

## <a name="extra-information"></a>Дополнительные сведения

Изменения конструктора свойств применяются не только к ссылкам на проекты; Вы также можете задать метаданные NGen для элементов внутри проекта (используя те же методы, описанные выше), если элементы являются сборками .NET.
