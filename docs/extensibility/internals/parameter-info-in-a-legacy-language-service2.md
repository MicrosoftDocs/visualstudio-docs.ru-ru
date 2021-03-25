---
title: Сведения о параметре в устаревшем языке S2 | Документация Майкрософт
description: Узнайте, как поддерживать операцию со сведениями о параметрах IntelliSense для отображения сигнатуры метода при вводе метода в устаревшей языковой службе.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0488c9d6570d9ed127c5b021ddfcf7d74f0dd856
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062932"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Сведения о параметрах в устаревшей языковой службе 2
Сведения о параметрах IntelliSense — это подсказка, которая отображает сигнатуру метода, когда пользователь вводит в список параметров метода начальный символ списка параметров (обычно это открывающая скобка). После ввода каждого параметра и ввода разделителя параметров (обычно это запятая) подсказка обновляется для отображения следующего параметра полужирным шрифтом.

 Классы Managed Package Framework (MPF) обеспечивают поддержку управления подсказкой сведений о параметрах. Средство синтаксического анализа должно обнаруживать символы начала, параметры и окончания параметров, а также должен предоставлять список сигнатур методов и связанные с ними параметры.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="implementation"></a>Реализация
 Средство синтаксического анализа должно установить значение триггера, <xref:Microsoft.VisualStudio.Package.TokenTriggers> если оно находит начальный символ списка параметров (часто это открывающая скобка). Он должен задать <xref:Microsoft.VisualStudio.Package.TokenTriggers> триггер при обнаружении разделителя параметров (часто это запятая). Это приводит к обновлению всплывающей подсказки с сведениями о параметрах и отображению следующего параметра полужирным шрифтом. Синтаксический анализатор должен задать значение триггера, если <xref:Microsoft.VisualStudio.Package.TokenTriggers> если находит символ конца списка параметров (часто это закрывающая круглая скобка).

 <xref:Microsoft.VisualStudio.Package.TokenTriggers>Значение триггера инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> метода, который, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> средство синтаксического анализа метода с причиной синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> . Если средство синтаксического анализа определяет, что идентификатор перед начальным символом списка параметров является распознаваемым именем метода, он возвращает список совпадающих сигнатур методов в <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекте. При обнаружении подписей методов подсказка сведений о параметрах отображается с первой подписью в списке. Затем эта подсказка обновляется по мере ввода подписи. Если введен конечный символ списка параметров, подсказка сведений о параметрах удаляется из представления.

> [!NOTE]
> Чтобы убедиться, что подсказка сведений о параметрах правильно отформатирована, необходимо переопределить свойства <xref:Microsoft.VisualStudio.Package.Methods> класса для предоставления соответствующих символов. Базовый <xref:Microsoft.VisualStudio.Package.Methods> класс принимает сигнатуру метода в стиле C#. Сведения о <xref:Microsoft.VisualStudio.Package.Methods> том, как это можно сделать, см. в классе.

## <a name="enabling-support-for-the-parameter-info"></a>Включение поддержки сведений о параметрах
 Для поддержки подсказок сведений о параметрах необходимо задать `ShowCompletion` именованный параметр <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> для `true` . Языковая служба считывает значение этой записи реестра из <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Свойства.

 Кроме того, для <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> `true` отображения всплывающей подсказки о параметрах для свойства необходимо задать значение.

### <a name="example"></a>Пример
 Ниже приведен упрощенный пример обнаружения символов в списке параметров и настройки соответствующих триггеров. Этот пример предназначен только для демонстрационных целей. Предполагается, что сканер содержит метод `GetNextToken` , идентифицирующий и возвращающий маркеры из строки текста. Пример кода просто устанавливает триггеры каждый раз, когда он видит правильный тип символа.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Поддержка всплывающей подсказки о параметрах в средстве синтаксического анализа
 <xref:Microsoft.VisualStudio.Package.Source>Класс делает некоторые предположения о содержимом <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> классов и при отображении и обновлении всплывающей подсказки о параметрах.

- Средство синтаксического анализа задается <xref:Microsoft.VisualStudio.Package.ParseReason> при вводе начального символа списка параметров.

- Расположение, заданное в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекте, находится сразу после начального символа списка параметров. Синтаксический анализатор должен собрать сигнатуры всех объявлений методов, доступных в этой позиции, и сохранить их в списке в вашей версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта. Этот список включает имя метода, тип метода (тип возвращаемого значения) и список возможных параметров. В этом списке в дальнейшем выполняется поиск сигнатуры метода или сигнатур для их вывода в подсказке сведений о параметрах.

  Синтаксический анализатор должен проанализировать строку, указанную <xref:Microsoft.VisualStudio.Package.ParseRequest> объектом, чтобы получить имя введенного метода, а также расстояние от пользователя до ввода параметров. Это достигается путем передачи имени метода в <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> метод <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекта и последующего вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> метода при синтаксическом анализе начального символа списка параметров, вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> метода при синтаксическом анализе следующего символа списка параметров и, наконец, вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> метода при синтаксическом анализе конечного символа списка параметров. Результаты этих вызовов методов используются <xref:Microsoft.VisualStudio.Package.Source> классом для обновления подсказки сведений о параметрах соответствующим образом.

### <a name="example"></a>Пример
 Вот строка текста, которую может ввести пользователь. Числа под строкой указывают, какой шаг выполняется синтаксическим анализатором в этой позиции в строке (при условии, что синтаксический анализ перемещается слева направо). Предполагается, что все, что перед строкой уже проанализировано для сигнатур методов, включая сигнатуру метода "тестфунк".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Ниже описаны действия, которые выполняет синтаксический анализатор.

1. Средство синтаксического анализа вызывается <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> с текстом «тестфунк».

2. Средство синтаксического анализа вызывает <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. Средство синтаксического анализа вызывает <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. Средство синтаксического анализа вызывает <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
