---
title: Завершение элементов в языковой службе прежних версий | Документация Майкрософт
description: Узнайте, как подсказка средства IntelliSense для завершения членов работает в языковой службе прежних версий и как она поддерживается платформой управляемого пакета (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5279b3a96cb9658b968a5d51bbd8b1c2a41862b6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095138"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Завершение участников в языковой службе прежних версий

Завершение элемента IntelliSense — это всплывающая подсказка, на которой отображается список возможных элементов определенной области, таких как класс, структура, перечисление или пространство имен. Например, в C#, если пользователь вводит "this", за которым следует точка, список всех членов класса или структуры в текущей области представлен в списке, из которого пользователь может выбрать.

Платформа управляемого пакета (MPF) обеспечивает поддержку подсказки и управление списком в подсказке; все, что требуется, — это совместная работа от средства синтаксического анализа для предоставления данных, отображаемых в списке.

Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="how-it-works"></a>Как это работает

Ниже приведены два способа отображения списка членов с помощью классов MPF:

- Размещение курсора на идентификаторе или после символа завершения элемента и выбор **списка членов** в меню **IntelliSense** .

- <xref:Microsoft.VisualStudio.Package.IScanner>Средство проверки обнаруживает символ завершения элемента и задает для этого символа триггер маркера [Токентригжерс. мемберселект](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) .

Символ завершения элемента указывает, что необходимо следовать члену класса, структуры или перечисления. Например, в C# или Visual Basic символом завершения элемента является `.` , а в C++ символом является либо `.` `->` . Значение триггера задается при сканировании символа выбора элемента.

### <a name="the-intellisense-member-list-command"></a>Команда IntelliSense member list

<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>Команда инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метода <xref:Microsoft.VisualStudio.Package.Source> класса, а <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> средство синтаксического анализа метода с причиной синтаксического анализа [парсереасон. дисплаймемберлист](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Средство синтаксического анализа определяет контекст текущей точки, а также маркер в или непосредственно перед текущей позицией. На основе этого маркера представлен список объявлений. Например, в C# при размещении курсора на члене класса и выборе **списка членов** вы получаете список всех членов класса. Если курсор находится после точки, следующей за объектной переменной, вы получаете список всех членов класса, представляемого объектом. Обратите внимание, что если курсор располагается на элементе при отображении списка элементов, выбор элемента из списка заменяет элемент курсора на тот, который находится в списке.

### <a name="the-token-trigger"></a>Триггер токена

Триггер [токентригжерс. мемберселект](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метода <xref:Microsoft.VisualStudio.Package.Source> класса, а <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод, в свою очередь, вызывает средство синтаксического анализа с причиной синтаксического анализа [парсереасон. мемберселект](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Если триггер маркера также включает флаг [токентригжерс. матчбрацес](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) , то причина синтаксического анализа — [парсереасон. мемберселектандхигхлигхтбрацес](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), который сочетает выделение элементов и выделение фигурных скобок.

Средство синтаксического анализа определяет контекст текущей позиции, а также то, что было введено до символа выбора элемента. На основе этих сведений средство синтаксического анализа создает список всех членов запрошенной области. Этот список объявлений хранится в <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекте, возвращаемом <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> методом. Если возвращаются какие-либо объявления, отображается подсказка для завершения элемента. Всплывающая подсказка управляется экземпляром <xref:Microsoft.VisualStudio.Package.CompletionSet> класса.

## <a name="enable-support-for-member-completion"></a>Включить поддержку для завершения элементов

Для `CodeSense` поддержки любой операции IntelliSense необходимо, чтобы для записи реестра было задано значение 1. Эту запись реестра можно задать с помощью именованного параметра, передаваемого в <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибут пользователя, связанный с языковым пакетом. Классы языковой службы считывают значение этой записи реестра из <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.

Если сканер возвращает триггер маркера [токентригжерс. мемберселект](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>), а синтаксический анализатор возвращает список объявлений, то отображается список завершения элементов.

## <a name="support-member-completion-in-the-scanner"></a>Поддержка завершения элементов в сканере

Сканер должен иметь возможность обнаружить символ завершения элемента и установить триггер токена [токентригжерс. мемберселект](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) при синтаксическом анализе этого символа.

### <a name="scanner-example"></a>Пример сканера

Ниже приведен упрощенный пример обнаружения символа завершения элемента и установки соответствующего <xref:Microsoft.VisualStudio.Package.TokenTriggers> флага. Этот пример предназначен только для демонстрационных целей. Предполагается, что сканер содержит метод `GetNextToken` , идентифицирующий и возвращающий маркеры из строки текста. Пример кода просто задает триггер, когда он видит правильный тип символа.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char memberSelectChar = '.';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (c == memberSelectChar)
                {
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;
                }
            }
            return foundToken;
        }
    }
}
```

## <a name="support-member-completion-in-the-parser"></a>Поддержка завершения элементов в средстве синтаксического анализа

Для завершения элемента <xref:Microsoft.VisualStudio.Package.Source> класс вызывает <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> метод. Необходимо реализовать список в классе, производном от <xref:Microsoft.VisualStudio.Package.Declarations> класса. Дополнительные <xref:Microsoft.VisualStudio.Package.Declarations> сведения о методах, которые необходимо реализовать, см. в разделе класс.

Средство синтаксического анализа вызывается с помощью [парсереасон. мемберселект](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) или [парсереасон. мемберселектандхигхлигхтбрацес](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) при вводе символа выделения элемента. Расположение, указанное в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекте, сразу после символа выбора элемента. Средство синтаксического анализа должно состоять из имен всех элементов, которые могут присутствовать в списке членов в этой конкретной точке исходного кода. Затем синтаксический анализатор должен проанализировать текущую строку, чтобы определить область, которую пользователь хочет связать с символом выбора элемента.

Эта область основана на типе идентификатора до того, как элемент выберет символ. Например, в C# при наличии переменной `languageService` -члена, имеющей тип, введите `LanguageService` **лангуажесервице.** создает список всех членов `LanguageService` класса. Кроме того, в C# введите **this.** создает список всех членов класса в текущей области.

### <a name="parser-example"></a>Пример средства синтаксического анализа

В следующем примере показан один из способов заполнения <xref:Microsoft.VisualStudio.Package.Declarations> списка. В этом коде предполагается, что средство синтаксического анализа создает объявление и добавляет его в список, вызывая `AddDeclaration` метод для `TestAuthoringScope` класса.

```csharp
using System.Collections;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclaration
    {
        public string Name;            // Name of declaration
        public int     TypeImageIndex; // Glyph index
        public string Description;     // Description of declaration

        public TestDeclaration(string name, int typeImageIndex, string description)
        {
            this.Name = name;
            this.TypeImageIndex = typeImageIndex;
            this.Description = description;
        }
    }

    //===================================================
    internal class TestDeclarations : Declarations
    {
        private ArrayList declarations;

        public TestDeclarations()
            : base()
        {
            declarations = new ArrayList();
        }

        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        //////////////////////////////////////////////////////////////////////
        // Declarations of class methods that must be implemented.
        public override int GetCount()
        {
            // Return the number of declarations to show.
            return declarations.Count;
        }

        public override string GetDescription(int index)
        {
            // Return the description of the specified item.
            string description = "";
            if (index >= 0 && index < declarations.Count)
            {
                description = ((TestDeclaration)declarations[index]).Description;
            }
            return description;
        }

        public override string GetDisplayText(int index)
        {
            // Determine what is displayed in the tool tip list.
            string text = null;
            if (index >= 0 && index < declarations.Count)
            {
                text = ((TestDeclaration)declarations[index]).Name;
            }
            return text;
        }

        public override int GetGlyph(int index)
        {
            // Return index of image to display next to the display text.
            int imageIndex = -1;
            if (index >= 0 && index < declarations.Count)
            {
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;
            }
            return imageIndex;
        }

        public override string GetName(int index)
        {
            string name = null;
            if (index >= 0 && index < declarations.Count)
            {
                name = ((TestDeclaration)declarations[index]).Name;
            }
            return name;
        }
    }

    //===================================================
    public class TestAuthoringScope : AuthoringScope
    {
        private TestDeclarations declarationsList;

        public void AddDeclaration(TestDeclaration declaration)
        {
            if (declaration != null)
            {
                if (declarationsList == null)
                {
                    declarationsList = new TestDeclarations();
                }
                declarationsList.AddDeclaration(declaration);
            }
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return declarationsList;
        }

        /////////////////////////////////////////////////
        // Remainder of AuthoringScope methods not shown.
        /////////////////////////////////////////////////
    }

    //===================================================
    class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            TestAuthoringScope scope = new TestAuthoringScope();
            if (req.Reason == ParseReason.MemberSelect ||
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)
            {
                // Gather list of declarations based on what the user
                // has typed so far. In this example, this list is an array of
                // MemberDeclaration objects (a helper class you might implement
                // to hold member declarations).
                // How this list is gathered is dependent on the parser
                // and is not shown here.
                MemberDeclarations memberDeclarations;
                memberDeclarations = GetDeclarationsForScope();

                // Now populate the Declarations list in the authoring scope.
                // GetImageIndexBasedOnType() is a helper method you
                // might implement to convert a member type to an index into
                // the image list returned from the language service.
                foreach (MemberDeclaration dec in memberDeclarations)
                {
                    scope.AddDeclaration(new TestDeclaration(
                                             dec.Name,
                                             GetImageIndexBasedOnType(dec.Type),
                                             dec.Description));
                }
            }
            return scope;
        }
    }
}
```
