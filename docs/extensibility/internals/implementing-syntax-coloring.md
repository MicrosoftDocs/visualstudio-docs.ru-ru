---
title: Применение цветового выделения синтаксиса | Документация Майкрософт
description: Узнайте, как реализовать цветовую раскраску синтаксиса в Visual Studio с помощью функций языковой службы платформы управляемого пакета (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c46cea481eceadef5118388633f84402870a209
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069612"
---
# <a name="implementing-syntax-coloring"></a>Реализация цветовой маркировки синтаксиса
Если языковая служба предоставляет цветовую раскраску синтаксиса, средство синтаксического анализа преобразует строку текста в массив цветных элементов и возвращает типы токенов, соответствующие этим цветовым элементам. Средство синтаксического анализа должно возвращать типы токенов, принадлежащие списку цветовых элементов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отображает каждый цветовой элемент в окне кода в соответствии с атрибутами, назначенными объектом тонирования, соответствующему типу токена.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не указывает интерфейс средства синтаксического анализа, и реализация средства синтаксического анализа является абсолютной. Однако реализация средства синтаксического анализа по умолчанию предоставляется в проекте языкового пакета Visual Studio. Для управляемого кода платформа управляемого пакета (MPF) обеспечивает полную поддержку выделения цветом текста.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации цветового выделения синтаксиса см. в разделе [Пошаговое руководство. выделение текста](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Шаги, за которыми следует редактор для выделения цветом текста

1. Редактор получает тонированный элемент, вызывая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> объекта.

2. Редактор вызывает метод, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> чтобы определить, требуется ли, чтобы для параметра «цветовой цвет» было необходимо поддерживать состояние каждой строки за пределами тонирования.

3. Если для параметра тонирования требуется поддерживать состояние вне области выделения, редактор вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> метод для получения состояния первой строки.

4. Для каждой строки в буфере редактор вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, который выполняет следующие действия:

    1. Строка текста передается сканеру для преобразования текста в маркеры. Каждый токен задает текст маркера и тип токена.

    2. Тип токена преобразуется в индекс в список цветовых элементов.

    3. Сведения о токене используются для заполнения массива таким, чтобы каждый элемент массива соответствовал символу в строке. Значения, хранящиеся в массиве, являются индексами в списке цветовых элементов.

    4. Состояние в конце строки возвращается для каждой строки.

5. Если для этого режима требуется поддерживать состояние, редактор кэширует состояние этой строки.

6. Редактор отображает строку текста, используя сведения, возвращенные <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> методом. Для этого необходимо выполнить следующие действия:

    1. Для каждого символа в строке Возвращает цветовой индекс элемента.

    2. При использовании цветовых элементов по умолчанию можно получить доступ к списку цветовых элементов редактора.

    3. В противном случае вызовите метод языковой службы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> для получения цветового элемента.

    4. Используйте сведения в элементе с цветовым цветом, чтобы подготовить текст к отображению.

## <a name="managed-package-framework-colorizer"></a>Цветовой пакет для платформы управляемых пакетов
 Платформа управляемого пакета (MPF) предоставляет все классы, необходимые для реализации выделения цветом. Класс языковой службы должен наследовать <xref:Microsoft.VisualStudio.Package.LanguageService> класс и реализовать необходимые методы. Необходимо предоставить сканер и средство синтаксического анализа, реализовав <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс, и вернуть экземпляр этого интерфейса из <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метода (один из методов, которые должны быть реализованы в <xref:Microsoft.VisualStudio.Package.LanguageService> классе). Дополнительные сведения см. [в разделе тонирование синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
