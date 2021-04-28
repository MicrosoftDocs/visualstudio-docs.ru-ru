---
title: JavaScript и TypeScript в Visual Studio 2019
description: Узнайте, как Visual Studio 2019 предоставляет широкие возможности для разработки на JavaScript, используя JavaScript напрямую, а также с помощью языка программирования TypeScript.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 267bd8567b60a66bcf9d78c3aef8f02bbc942e0d
ms.sourcegitcommit: e12d6cdaeb37564f05361965db2ec8ad0d4f21ad
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025882"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript и TypeScript в Visual Studio 2019

## <a name="overview"></a>Обзор

Visual Studio 2019 предоставляет обширную поддержку для разработки JavaScript, как с помощью прямого использования JavaScript, также и с помощью [языка программирования TypeScript](http://www.typescriptlang.org/), который был разработан с целью повышения продуктивности и интереса во время разработки на JavaScript, особенно при разработке масштабных проектов. Код JavaScript или TypeScript в Visual Studio можно написать для многих типов приложений и служб.

## <a name="javascript-language-service"></a>Служба языка JavaScript

Опыт работы с JavaScript в Visual Studio 2019 обеспечивается тем же обработчиком, что и поддержка TypeScript. Это позволяет улучшить поддержку компонентов, функциональность и интеграцию сразу в готовом виде.

Функция восстановления устаревшей языковой службы JavaScript более не доступна. Теперь пользователи сразу получают новую языковую службу JavaScript. Новая языковая служба основана исключительно на языковой службе TypeScript, которая базируется на статическом анализе. Это позволяет нам оптимизировать инструментарий, поэтому ваш код на JavaScript может использовать преимущества расширенной поддержки IntelliSense на основе определений типов. Новая служба имеет небольшой размер и использует меньше памяти, чем устаревшие службы, обеспечивая более высокую производительность пользовательского кода по мере его масштабирования. Также мы улучшили производительность языковой службы для обработки более крупных проектов.

## <a name="typescript-support"></a>Поддержка TypeScript

Visual Studio 2019 предоставляет несколько вариантов для интеграции компиляции TypeScript в проект.

* [Пакет NuGet для TypeScript.](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) Когда в проект устанавливается пакет NuGet или TypeScript 3.2 или более новой версии, в редактор загружается соответствующая версия языковой службы TypeScript.
* [Пакет npm для TypeScript.](https://www.npmjs.com/package/typescript) Когда в проект устанавливается пакет npm или TypeScript 2.1 или более новой версии, в редактор загружается соответствующая версия языковой службы TypeScript.
* Также как и стандартный SDK, который можно скачать из [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395), TypeScript SDK доступен в установщике Visual Studio по умолчанию.

> [!TIP]
> Для проектов, которые разработаны в Visual Studio 2019, рекомендуется использовать пакеты TypeScript NuGet и TypeScript npm. Они обеспечивают лучшую портативность в различных средах и платформах. Дополнительные сведения см. в статьях [Компиляция кода TypeScript (ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) и [Компиляция кода TypeScript (Node.js)](../javascript/compile-typescript-code-npm.md).

## <a name="projects"></a>Проекты

Приложения UWP на JavaScript больше не поддерживаются в Visual Studio 2019. Невозможно создать или открыть проекты UWP на JavaScript (файлы с расширением *JSPROJ*). Дополнительные сведения см. в [документации по созданию прогрессивных веб-приложений (PWA), эффективно работающих на Windows](/microsoft-edge/progressive-web-apps-chromium).
