---
title: Сопоставление фигурных скобок в языковой службе прежних версий | Документация Майкрософт
description: Сведения о сопоставлении фигурных скобок в языковой службе прежних версий, помогающем отследить элементы языка, которые должны выполняться вместе, например круглые скобки и фигурные скобки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a92a3ca34e6314463bbfecbd8c4236789f213635
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086109"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Сопоставление фигурных скобок в языковой службе прежних версий
Сопоставление фигурных скобок помогает разработчику контролировать элементы языка, которые должны выполняться вместе, например круглые скобки и фигурные скобки. Когда разработчик вводит закрывающую фигурную скобку, выделяется открывающая фигурная скобка.

 Можно сопоставить два или три элемента сосуществования, называемые парами и триадными. Тройные элементы — это наборы из трех элементов совместной работы. Например, в C# `foreach` оператор формирует тройной: `foreach()` , `{` и `}` . При вводе закрывающей фигурной скобки все три элемента выделяются.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Чтобы узнать больше о новом способе реализации сопоставления фигурных скобок, см. раздел [Пошаговое руководство. Отображение парных скобок](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>Класс поддерживает как пары, так и тройные значения с помощью <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> методов и.

## <a name="implementation"></a>Реализация
 Языковая служба должна определять все совпадающие элементы на языке, а затем находить все совпадающие пары. Обычно это реализуется путем реализации <xref:Microsoft.VisualStudio.Package.IScanner> для обнаружения соответствующего языка и последующего использования <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода для сопоставления элементов.

 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Метод вызывает сканер для маркировки строки и возврата маркера непосредственно перед курсором. Сканер указывает, что пара элементов языка найдена путем установки значения триггера маркера <xref:Microsoft.VisualStudio.Package.TokenTriggers> для текущего маркера. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Метод вызывает <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> метод, который, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> метод со значением причины синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> для поиска соответствующего языкового элемента. При обнаружении совпадающего языкового элемента выделяются оба элемента.

 Полное описание того, как ввод фигурных скобок активирует выделение фигурных скобок, см. в разделе *пример операции синтаксического анализа* статьи средство [синтаксического анализа и сканера языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Включить поддержку сопоставления фигурных скобок
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>Атрибут может задавать записи реестра **матчбрацес**, **матчбрацесаткарет** и **шовматчингбраце** , которые задают соответствующие свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Свойства предпочтений языка также могут быть заданы пользователем.

|Запись реестра|Свойство|Описание|
|--------------------|--------------|-----------------|
|матчбрацес|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Включает сопоставление фигурных скобок.|
|матчбрацесаткарет|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Включает сопоставление скобок при перемещении курсора.|
|шовматчингбраце|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Выделяет соответствующую скобку.|

## <a name="match-conditional-statements"></a>Соответствие условных операторов
 Условные операторы, такие как `if` , `else if` , и, или,,, можно сопоставлять так `else` же, как и `#if` `#elif` `#else` `#endif` совпадающие разделители. Можно <xref:Microsoft.VisualStudio.Package.AuthoringSink> создать подкласс класса и предоставить метод, который может добавлять диапазоны текста, а также разделители для внутреннего массива соответствующих элементов.

## <a name="set-the-trigger"></a>Задание триггера
 В следующем примере показано, как обнаружить парные круглые скобки, фигурные скобки и квадратные скобки, а также задать для него триггер в сканере. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Метод <xref:Microsoft.VisualStudio.Package.Source> класса обнаруживает триггер и вызывает средство синтаксического анализа для поиска соответствующей пары (см. раздел *Поиск соответствия* в этой статье). Этот пример предназначен только для демонстрационных целей. Предполагается, что сканер содержит метод `GetNextToken` , идентифицирующий и возвращающий маркеры из строки текста.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Совпадение с фигурными скобками
 Ниже приведен упрощенный пример для сопоставления элементов языка `{ }` , `( )` и и `[ ]` добавления их диапазонов в <xref:Microsoft.VisualStudio.Package.AuthoringSink> объект. Этот подход не является рекомендуемым подходом к синтаксическому анализу исходного кода. Он предназначен только для демонстрационных целей.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>См. также
- [Функции устаревшей языковой службы](../../extensibility/internals/legacy-language-service-features1.md)
- [Анализатор и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
