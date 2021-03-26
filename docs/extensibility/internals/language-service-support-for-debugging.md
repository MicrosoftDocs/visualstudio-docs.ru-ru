---
title: Поддержка языковой службы для отладки | Документация Майкрософт
description: Сведения о функциях языковой службы в интерфейсе Ивслангуажедебугинфо, обеспечивающих поддержку отладки в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c00d0af21d5d165b7733267e0a97ae71ca6e573
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074578"
---
# <a name="language-service-support-for-debugging"></a>Поддержка языковой службы для отладки
Языковая служба может предоставлять функции, поддерживающие отладчик через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> интерфейс. Эти функции включают проверку точек останова и предоставление списка выражений в окне **видимые** .

 Однако для отладки языка требуется средство оценки выражений. Средство оценки выражений отвечает за вычисление выражений для получения значений во время отладки. Дополнительные сведения о реализации вычислителей выражений CLR см. в следующих статьях:

- [Вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Пример средства оценки управляемого выражения](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Выходные данные компилятора
 Тип компилятора определяет, что необходимо сделать для реализации отладки для вашего языка. Если компилятор предназначен для операционной системы Windows и записывает PDB-файл, можно выполнять отладку программ с помощью машинного модуля отладки кода, интегрированного в Visual Studio. Если компилятор создает MSIL, можно выполнять отладку программ с помощью модуля отладки управляемого кода, который также интегрирован в Visual Studio. Если компилятор предназначен для собственной операционной системы или другой среды выполнения, необходимо написать собственный модуль отладки.

 Дополнительные сведения о реализации отладки для вашего языка см. в разделе [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) в пакете SDK для отладки Visual Studio.
