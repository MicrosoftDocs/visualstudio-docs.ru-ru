---
title: Анализатор и сканер языковой службы прежних версий | Документация Майкрософт
description: Сведения о средстве синтаксического анализа и сканера языковой службы прежних версий, которые выбирают сведения о отображаемом коде.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c57bd9f8b71f861fd5be4176211af6907b27e74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090841"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Средство синтаксического анализа и сканер языковой службы прежних версий
Средство синтаксического анализа является основой языковой службы. Для классов языка Managed Package Framework (MPF) требуется средство синтаксического анализа языка, чтобы выбрать сведения о отображаемом коде. Средство синтаксического анализа разделяет текст на лексические токены, а затем определяет эти токены по типу и функциональности.

## <a name="discussion"></a>Разговор
 Ниже приведен метод C#.

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 В этом примере токены являются словами и знаками препинания. Ниже приведены типы токенов.

|Имя токена|Тип маркера|
|----------------|----------------|
|пространство имен, класс, Public, void, int|ключевое слово|
|=|оператор|
|{ } ( ) ;|разделитель|
|MyNamespace, MyClass, MyFunction, arg1, var1|идентификатор|
|MyNamespace|namespace|
|MyClass|class|
|MyFunction|method|
|arg1|parameter|
|var1|локальная переменная|

 Роль средства синтаксического анализа заключается в определении токенов. Некоторые токены могут иметь более одного типа. После того как анализатор определил маркеры, языковая служба может использовать эти сведения для предоставления полезных функций, таких как выделение синтаксиса, сопоставление фигурных скобок и операции IntelliSense.

## <a name="types-of-parsers"></a>Типы средств синтаксического анализа
 Средство синтаксического анализа языковой службы отличается от синтаксического анализатора, используемого в составе компилятора. Однако этот тип синтаксического анализатора должен использовать как сканер, так и средство синтаксического анализа так же, как средство синтаксического анализа компилятора.

- Для обнаружения типов токенов используется сканер. Эти данные используется для выделения синтаксиса и для быстрого определения типов токенов, способных вызывать другие операции, например, проверку соответствия фигурных скобок. Этот сканер представлен <xref:Microsoft.VisualStudio.Package.IScanner> интерфейсом.

- Средство синтаксического анализа используется для описания функций и области токенов. Эти сведения используются в операциях IntelliSense для определения элементов языка, таких как методы, переменные, параметры и объявления, а также для предоставления списков членов и подписей методов на основе контекста. Этот синтаксический анализатор также используется для поиска соответствующих пар языковых элементов, таких как фигурные скобки и круглые скобки. Доступ к этому средству синтаксического анализа осуществляется через <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> классе.

  Способ реализации сканера и средства синтаксического анализа для языковой службы не отличается от вас. Доступно несколько ресурсов, описывающих работу средств синтаксического анализа и написание собственного средства синтаксического анализа. Кроме того, доступны несколько бесплатных и коммерческих продуктов, помогающих в создании средства синтаксического анализа.

### <a name="the-parsesource-parser"></a>Средство синтаксического анализа Парсесаурце
 В отличие от анализатора, используемого в составе компилятора (в котором маркеры преобразуются в некоторый формат исполняемого кода), средство синтаксического анализа языковой службы может вызываться по различным причинам и в различных контекстах. Способ реализации этого подхода в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> методе в <xref:Microsoft.VisualStudio.Package.LanguageService> классе подходит вам. Важно помнить, что <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод может быть вызван в фоновом потоке.

> [!CAUTION]
> <xref:Microsoft.VisualStudio.Package.ParseRequest>Структура содержит ссылку на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект. Этот <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект не может использоваться в фоновом потоке. На самом деле многие базовые классы MPF не могут использоваться в фоновом потоке. К ним относятся <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter> классы,, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> и, а также любой другой класс, который напрямую или косвенно взаимодействует с представлением.

 Этот синтаксический анализатор обычно выполняет синтаксический анализ всего исходного файла при первом его вызове или при задании значения причины синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> . Последующие вызовы <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода обрабатывают небольшую часть проанализированного кода и могут выполняться гораздо быстрее, используя результаты предыдущей полной операции синтаксического анализа. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Метод передает результаты операции синтаксического анализа через <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекты и. <xref:Microsoft.VisualStudio.Package.AuthoringSink>Объект используется для получения сведений о конкретной причине синтаксического анализа, например сведения о диапазонах парных скобок или сигнатурах методов, имеющих списки параметров. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Предоставляет коллекции объявлений и сигнатур методов, а также поддержку параметра переход к расширенному редактированию (**Переход к определению**, **Переход к объявлению**, **Переход по ссылке**).

### <a name="the-iscanner-scanner"></a>Сканер средства проверки
 Необходимо также реализовать сканер, реализующий интерфейс <xref:Microsoft.VisualStudio.Package.IScanner> . Однако, поскольку этот сканер работает построчно с помощью <xref:Microsoft.VisualStudio.Package.Colorizer> класса, обычно проще реализовать. В начале каждой строки MPF предоставляет <xref:Microsoft.VisualStudio.Package.Colorizer> классу значение, используемое в качестве переменной состояния, которая передается сканеру. В конце каждой строки сканер возвращает обновленную переменную состояния. MPF кэширует эти сведения о состоянии для каждой строки, чтобы средство проверки может начать анализ из любой строки без необходимости запуска в начале исходного файла. Это быстрое сканирование одной строки позволяет редактору обеспечить быструю обратную связь с пользователем.

## <a name="parsing-for-matching-braces"></a>Синтаксический анализ парных скобок
 В этом примере показан поток управления для сопоставления закрывающей фигурной скобки, которую пользователь ввел. В этом процессе средство проверки, используемое для выделения цветом, также используется для определения типа маркера и того, может ли маркер активировать операцию сопоставления с фигурными скобками. Если триггер найден, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> вызывается метод для поиска парной скобки. Наконец, две фигурные скобки выделены.

 Несмотря на то, что скобки используются в именах триггеров и из соображений синтаксического анализа, этот процесс не ограничивается фактическими фигурными скобками. Поддерживается любая пара символов, которая указана как соответствующая пара. Примеры: (и), \< and > и [и].

 Предположим, что языковая служба поддерживает Парные фигурные скобки.

1. Пользователь вводит закрывающую фигурную скобку (}).

2. Фигурная скобка вставляется в курсор в исходном файле, а курсор — на один.

3. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Метод в <xref:Microsoft.VisualStudio.Package.Source> классе вызывается с типизированной закрывающей фигурной скобкой.

4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Метод вызывает <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> классе для получения маркера в позиции непосредственно перед текущей позицией курсора. Этот маркер соответствует типизированной закрывающей фигурной скобке.

    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>Метод вызывает <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> метод <xref:Microsoft.VisualStudio.Package.Colorizer> объекта для получения всех токенов в текущей строке.

    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>Метод вызывает <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> метод для <xref:Microsoft.VisualStudio.Package.IScanner> объекта с текстом текущей строки.

    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>Метод многократно вызывает <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> метод для объекта, <xref:Microsoft.VisualStudio.Package.IScanner> чтобы собрать все токены из текущей строки.

    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>Метод вызывает закрытый метод в <xref:Microsoft.VisualStudio.Package.Source> классе для получения токена, содержащего нужную точку, и передает в список токенов, полученных из <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> метода.

5. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Метод выполняет поиск флага триггера маркера для <xref:Microsoft.VisualStudio.Package.TokenTriggers> токена, возвращаемого методом, <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> то есть маркера, представляющего закрывающую фигурную скобку.

6. Если найден флаг триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> , <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> <xref:Microsoft.VisualStudio.Package.Source> вызывается метод в классе.

7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>Метод запускает операцию синтаксического анализа со значением причины синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> . Эта операция в конечном итоге вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод для <xref:Microsoft.VisualStudio.Package.LanguageService> класса. Если асинхронный анализ включен, этот вызов <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода происходит в фоновом потоке.

8. По завершении операции синтаксического анализа внутренний обработчик завершения (также известный как метод обратного вызова) `HandleMatchBracesResponse` вызывается в <xref:Microsoft.VisualStudio.Package.Source> классе. Этот вызов выполняется автоматически <xref:Microsoft.VisualStudio.Package.LanguageService> базовым классом, а не синтаксическим анализатором.

9. `HandleMatchBracesResponse`Метод получает список диапазонов из <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекта, хранящегося в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекте. (Диапазон — это <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> структура, которая задает диапазон строк и символов в исходном файле.) Этот список диапазонов обычно содержит два диапазона: по одному для открывающих и закрывающих фигурных скобок.

10. `HandleBracesResponse`Метод вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> метод для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта, который хранится в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекте. Это выделяет заданные диапазоны.

11. Если <xref:Microsoft.VisualStudio.Package.LanguagePreferences> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> включено, `HandleBracesResponse` метод получает текст, охватываемый соответствующим диапазоном, и отображает первые 80 символов этого диапазона в строке состояния. Это лучше, если <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод включает элемент Language, сопровождающий совпадающую пару. Дополнительные сведения см. в описании свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Готово.

### <a name="summary"></a>Сводка
 Парная операция скобок обычно ограничена простыми парами языковых элементов. Более сложные элементы, такие как парные триадные ("", "" и "", "", "" `if(...)` `{` `}` `else` `{` и "" `}` ), могут быть выделены в рамках операции завершения слова. Например, при завершении слова «else» соответствующий `if` оператор «» может быть выделен. Если существовал ряд `if` / `else if` инструкций, все они могут быть выделены с помощью того же механизма, что и парные скобки. <xref:Microsoft.VisualStudio.Package.Source>Базовый класс уже поддерживает это, как показано ниже. сканер должен вернуть значение триггера маркера в <xref:Microsoft.VisualStudio.Package.TokenTriggers> сочетании со значением триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> для токена, который находится перед позицией курсора.

 Дополнительные сведения см. [в разделе Сопоставление фигурных скобок в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Синтаксический анализ для выделения цветом
 Выкрасить исходный код несложно, просто укажите тип маркера и возвращаемые сведения о цвете для этого типа. <xref:Microsoft.VisualStudio.Package.Colorizer>Класс выступает в качестве посредника между редактором и средством проверки, чтобы предоставить сведения о цвете для каждого маркера. <xref:Microsoft.VisualStudio.Package.Colorizer>Класс использует <xref:Microsoft.VisualStudio.Package.IScanner> объект для выделения цветом линии, а также для сбора сведений о состоянии для всех строк в исходном файле. В классах языковой службы MPF класс не требуется <xref:Microsoft.VisualStudio.Package.Colorizer> переопределять, так как он взаимодействует с сканером только через <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс. Вы предоставляете объект, реализующий <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс, переопределяя <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод для <xref:Microsoft.VisualStudio.Package.LanguageService> класса.

 <xref:Microsoft.VisualStudio.Package.IScanner>Сканеру предоставляется строка исходного кода с помощью <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> метода. Вызовы <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> метода повторяются для получения следующего токена в строке, пока строка не будет исчерпана токенов. Для выделения цветом MPF обрабатывает весь исходный код как последовательность строк. Таким образом, сканер должен иметь возможность работать с источником, находящимся в виде линий. Кроме того, любая строка может быть передана сканеру в любое время, и единственной гарантией является то, что сканер получает переменную состояния из строки до того, как строка будет просканирована.

 <xref:Microsoft.VisualStudio.Package.Colorizer>Класс также используется для обнаружения триггеров маркеров. Эти триггеры сообщают MPF, что конкретный маркер может инициировать более сложную операцию, например завершение слов или Парные фигурные скобки. Так как определение таких триггеров должно выполняться быстро и должно происходить в любом месте, сканер лучше всего подходит для этой задачи.

 Дополнительные сведения см. [в разделе тонирование синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Синтаксический анализ функциональности и области
 Синтаксический анализ функциональности и области требует больше усилий, чем просто определение типов обнаруженных маркеров. Синтаксический анализатор должен вычислить не только тип токена, но и функциональные возможности, для которых используется маркер. Например, идентификатор — это просто имя, но на вашем языке идентификатор может быть именем класса, пространства имен, метода или переменной в зависимости от контекста. Общий тип токена может быть идентификатором, но идентификатор также может иметь другие значения, в зависимости от того, что это такое и где оно определено. Эта идентификация требует, чтобы средство синтаксического анализа имело более широкие знания о языке, который анализируется. Это место, где <xref:Microsoft.VisualStudio.Package.AuthoringSink> входит класс. <xref:Microsoft.VisualStudio.Package.AuthoringSink>Класс собирает сведения об идентификаторах, методах, соответствующих парах языков (например, фигурных скобках и круглых скобках), а также тройных языках (аналогично парам языка, за исключением того, что есть три части, например " `foreach()` " " `{` и" `}` "). Кроме того, можно переопределить <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс для поддержки идентификации кода, который используется в ранних проверках точек останова, чтобы отладчик не загружался, и окно **автоматических** отладки, которое отображает локальные переменные и параметры автоматически при отладке программы, и требует, чтобы средство синтаксического анализа определяло соответствующие локальные переменные и параметры в дополнение к тем, которые представлены отладчиком.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>Объект передается в средство синтаксического анализа как часть <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта, а новый <xref:Microsoft.VisualStudio.Package.AuthoringSink> объект создается каждый раз при <xref:Microsoft.VisualStudio.Package.ParseRequest> создании нового объекта. Кроме того, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод должен возвращать <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект, который используется для управления различными операциями IntelliSense. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Объект поддерживает список для объявлений и список методов, каждый из которых заполняется в зависимости от причины синтаксического анализа. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Класс должен быть реализован.

## <a name="see-also"></a>См. также
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
