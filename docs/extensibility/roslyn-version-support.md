---
title: Поддерживаемые сопоставления версий пакетов Roslyn
description: В этой статье показано, какие версии пакетов платформы компилятора .NET (Roslyn) поддерживаются для различных версий Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8fd9e62de70dd5bff81b5fdaee05822c7171981e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060514"
---
# <a name="net-compiler-platform-package-version-reference"></a>Справочник по версии пакета платформы компилятора .NET

В следующей таблице показано, какие версии [пакетов платформы компилятора .NET (Roslyn)](https://www.nuget.org/packages/Microsoft.Net.Compilers/) поддерживаются для различных версий Visual Studio.

Например, чтобы убедиться, что пользовательский анализатор работает во всех версиях Visual Studio 2017, он должен быть предназначен для версии 2,0 Microsoft.Net. compilers.

| Версия пакета Roslyn | Минимальная поддерживаемая версия Visual Studio |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 версии 15.9 |
| 2.9.0 | Visual Studio 2017 версии 15.8 |
| 2.8.2 | Visual Studio 2017 версии 15.7 |
| 2.7.0 | Visual Studio 2017 версии 15.6 |
| 2.6.1 | Visual Studio 2017 версии 15.5 |
| 2.4.0 | Visual Studio 2017 версии 15.4 |
| 2.3.2 | Visual Studio 2017 версия 15.3 |
| 2.2.0 | Visual Studio 2017 версии 15.2 |
| 2.1.0 | Visual Studio 2017 версии 15.1 |
| 2.0.0 | Visual Studio 2017 RTM |
| 1.3.2 | Visual Studio 2015 с обновлением 3 |
| 1.2.2 | Visual Studio 2015 с обновлением 2 |
| 1.1.1 | Обновление 1 для Visual Studio 2015 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> Для пакетов Roslyn, в которых минимальная поддерживаемая версия Visual Studio является версией Visual Studio 2017, все версии Visual Studio 2019 также поддерживаются, так как они появились позже.

## <a name="see-also"></a>См. также

- [Пакет SDK для .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
- [Начало работы с анализаторами Roslyn](getting-started-with-roslyn-analyzers.md)
