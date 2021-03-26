---
title: Автоматическое форматирование в языковой службе прежних версий | Документация Майкрософт
description: Сведения об автоматическом форматировании в языковой службе прежних версий, которая автоматически вставляет фрагмент кода при начале ввода известной конструкции кода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a08a56a6820917b3a954c162b1875430875c7585
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086278"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Автоматическое форматирование в языковой службе прежних версий
При автоматическом форматировании языковая служба автоматически вставляет фрагмент кода, когда пользователь начинает вводить известную конструкцию кода.

## <a name="automatic-formatting-behavior"></a>Поведение автоматического форматирования
 Например, при вводе значения, *Если* языковая служба автоматически вставляет парные скобки или нажата клавиша ВВОД, языковая служба принудительно устанавливает точку вставки на новой строке на соответствующий уровень отступа в зависимости от того, открывается ли Предыдущая строка в новой области.

 Фильтр команд, используемый для оставшейся версии языковой службы, также можно использовать для автоматического форматирования. Можно также выделить Парные фигурные скобки, вызвав метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
