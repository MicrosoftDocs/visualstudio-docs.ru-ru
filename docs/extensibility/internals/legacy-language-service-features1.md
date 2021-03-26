---
title: Устаревшая языковая служба Features1 | Документация Майкрософт
description: Сведения о функциях Visual Studio, которые поддерживаются в языковой службе для платформы управляемых пакетов (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2bb5169eeb53aa16d0827cdf50cb50d0db34d996
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074526"
---
# <a name="legacy-language-service-features-1"></a>Функции языковой службы прежних версий 1
Языковая служба управляемого пакета (MPF) может поддерживать одну или несколько [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] функций, таких как выделение синтаксиса, IntelliSense и проверка точки останова. Каждая функция может быть реализована независимо от других, но для всех требуется средство синтаксического анализа и сканер, за исключением выделения синтаксиса, для которого требуется только сканер.

## <a name="in-this-section"></a>в этом разделе
- [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки сопоставления пар языков, также известных как Парные фигурные скобки.

- [Комментирование кода синтаксиса в языковой службе прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки комментирования и комментирования выбранного кода.

- [Настраиваемые свойства документа в языковой службе прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки свойств документа, внедренных в исходный файл.

- [Структурирование в языковой службе прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки структурирования посредством реализации скрытых регионов.

- [Переформатирование кода в языковой службе прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки переформатирования кода.

- [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки фрагментов кода, которые являются частями кода, которые вставляются и могут быть изменены.

- [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Описывает, что требуется для поддержки операции со сведениями о параметрах IntelliSense для отображения сигнатуры метода при вводе метода.

- [Краткие сведения в языковой службе прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки операции быстрой информации IntelliSense для отображения сведений об идентификаторе.

- [Завершение участников в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки операции завершения элементов IntelliSense для выбора члена пространства имен из списка.

- [Завершение машинных слов в языковой службе прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки операции слова Complete в IntelliSense для завершения частично типизированных слов.

- [Поддержка окна видимых переменных в языковой службе прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Описывает, что может сделать языковая служба для поддержки окна " **видимые** " во время отладки.

- [Поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Описывает, как использовать **панель навигации** в верхней части представления редактора для быстрого перехода к любому типу или члену в файле, показанном в этом представлении.

- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки выделения синтаксиса исходного кода.

- [Проверка точек останова в языковой службе прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Описывает, что может сделать языковая служба для поддержки проверки точек останова за пределами отладчика.

## <a name="related-sections"></a>Связанные разделы
- [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Описывает средство синтаксического анализа и сканер, необходимые для реализации всех функций языковой службы, использующей платформу управляемых пакетов.

- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Описывает, что необходимо для реализации языковой службы с помощью MPF.

- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Описание действий, необходимых для регистрации службы языка на основе MPF с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Использование технологии IntelliSense](../../ide/using-intellisense.md)

 Объясняет, как IntelliSense упрощает доступ к языковой ссылке.

- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Содержит сведения об использовании платформы управляемых пакетов (MPF) для реализации полнофункциональной языковой службы в управляемом коде.
