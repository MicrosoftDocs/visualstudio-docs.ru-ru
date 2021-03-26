---
title: Разтонирование синтаксиса в языковой службе прежних версий | Документация Майкрософт
description: Узнайте, как обеспечить раскраску синтаксиса в языковой службе прежних версий, предоставив средство синтаксического анализа или проверки, которое может обозначать типы лексических элементов или маркеров.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 627c0b5184588f77188928b6355a9034a3a3465e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080548"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Цветовая маркировка синтаксиса в языковой службе прежних версий
Раскраска синтаксиса — это функция, которая заставляет различные элементы языка программирования отображаться в исходном файле в различных цветах и стилях. Для поддержки этой функции необходимо предоставить средство синтаксического анализа или сканер, который может обозначать типы лексических элементов или маркеров в файле. Многие языки различают ключевые слова, разделители (например, круглые или фигурные скобки) и комментарии, размечая их различными способами.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="implementation"></a>Реализация
 Для поддержки цветовой раскраски платформа управляемого пакета (MPF) включает <xref:Microsoft.VisualStudio.Package.Colorizer> класс, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс. Этот класс взаимодействует с, <xref:Microsoft.VisualStudio.Package.IScanner> чтобы определить маркер и цвета. Дополнительные сведения о сканерах см. в разделе [анализатор и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer>Затем класс помечает каждый символ маркера сведениями о цвете и возвращает эту информацию в редактор, отображающий исходный файл.

 Информация о цвете, возвращаемая редактору, является индексом в списке цветовых элементов. Каждый цветовой элемент задает значение цвета и набор атрибутов шрифта, например полужирный или Зачеркнутый. Редактор предоставляет набор цветовых элементов по умолчанию, которые может использовать служба языка. Все, что нужно сделать, — это указать соответствующий цветовой индекс для каждого типа токена. Однако можно предоставить набор настраиваемых цветовых элементов и индексов, предоставляемых для маркеров, и ссылаться на собственный список цветовых элементов вместо списка по умолчанию. `RequestStockColors`Для поддержки пользовательских цветов необходимо также задать для записи реестра значение 0 (или вообще не указывать `RequestStockColors` запись). Эту запись реестра можно задать с помощью именованного параметра для <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> определяемого пользователем атрибута. Дополнительные сведения о регистрации языковой службы и настройке ее параметров см. в разделе [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Настраиваемые цветные элементы
 Чтобы предоставить собственные настраиваемые цветовые элементы, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> метод и для <xref:Microsoft.VisualStudio.Package.LanguageService> класса. Первый метод возвращает число пользовательских цветовых элементов, поддерживаемых языковой службой, а второй — пользовательский цветовой элемент по индексу. Вы создаете список пользовательских цветовых элементов по умолчанию. В конструкторе языковой службы все, что вам нужно сделать, — это предоставить каждый цветовой элемент с именем. Visual Studio автоматически обрабатывает случай, когда пользователь выбирает другой набор цветовых элементов. Это имя отображается на странице свойств **шрифты и цвета** диалогового окна **Параметры** (доступно в меню **инструменты** Visual Studio), а это имя определяет цвет, который пользователь переопределил. Варианты выбора пользователя хранятся в кэше в реестре и доступны по имени цвета. На странице свойств **шрифты и цвета** перечислены все имена цветов в алфавитном порядке, поэтому вы можете сгруппировать пользовательские цвета, выполнив каждое имя цвета, указав имя своего языка. Например, "**тестлангуаже-Comment**" и "**тестлангуаже-keyword**". Можно также сгруппировать цветные элементы по типу, "**comment (тестлангуаже)**" и "**keyword (тестлангуаже)**". Рекомендуется группировать по имени языка.

> [!CAUTION]
> Настоятельно рекомендуется включать название языка в имя цветового элемента, чтобы избежать конфликтов с существующими цветовыми именами элементов.

> [!NOTE]
> При изменении имени одного из цветов во время разработки необходимо сбросить кэш, созданный Visual Studio при первом обращении к вашим цветам. Это можно сделать, запустив команду **сбросить экспериментальный куст** в меню программы Visual Studio SDK.

 Обратите внимание, что первый элемент в списке цветовых элементов никогда не упоминается. Visual Studio всегда предоставляет цвета и атрибуты текста по умолчанию для этого элемента. Самый простой способ работы с этим заключается в предоставлении заполнителя цветового элемента в качестве первого элемента.

### <a name="high-color-colorable-items"></a>Цветные элементы с высоким цветом
 Цветные элементы также могут поддерживать 24-разрядные или высокие значения цвета через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс. Класс MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> поддерживает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс, а 24-разрядные цвета указываются в конструкторе вместе с обычными цветами. Дополнительные сведения см. в описании класса <xref:Microsoft.VisualStudio.Package.ColorableItem>. В приведенном ниже примере показано, как задать 24-разрядные цвета для ключевых слов и комментариев. 24-разрядные цвета используются, когда 24-разрядный цвет поддерживается на рабочем столе пользователя. в противном случае используются обычные цвета текста.

 Помните, что это цвета по умолчанию для вашего языка; пользователь может изменить эти цвета в соответствии с любыми нужными.

### <a name="example"></a>Пример
 В этом примере показан один из способов объявления и заполнения массива настраиваемых цветовых элементов с помощью <xref:Microsoft.VisualStudio.Package.ColorableItem> класса. В этом примере задаются ключевые слова и цвета комментариев, использующие 24-разрядные цвета.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>Класс тонирования и сканер
 Базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс содержит <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> метод, инстантиантес <xref:Microsoft.VisualStudio.Package.Colorizer> класс. Сканер, возвращаемый <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> методом, передается <xref:Microsoft.VisualStudio.Package.Colorizer> конструктору класса.

 Необходимо реализовать <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод в собственной версии <xref:Microsoft.VisualStudio.Package.LanguageService> класса. <xref:Microsoft.VisualStudio.Package.Colorizer>Класс использует сканер для получения всех сведений о цвете маркера.

 Сканеру необходимо заполнить <xref:Microsoft.VisualStudio.Package.TokenInfo> структуру для каждого найденного маркера. Эта структура содержит такие сведения, как диапазон, занимаемый маркером, используемый цветовой индекс, тип, который является маркером, и триггеры маркеров (см <xref:Microsoft.VisualStudio.Package.TokenTriggers> .). Для выделения цветом с помощью класса требуются только индексы диапазона и цвета <xref:Microsoft.VisualStudio.Package.Colorizer> .

 Цветовой индекс, хранящийся в <xref:Microsoft.VisualStudio.Package.TokenInfo> структуре, обычно является значением из <xref:Microsoft.VisualStudio.Package.TokenColor> перечисления, которое предоставляет несколько именованных индексов, соответствующих различным элементам языка, таким как ключевые слова и операторы. Если список пользовательских цветовых элементов соответствует элементам, представленным в <xref:Microsoft.VisualStudio.Package.TokenColor> перечислении, то можно просто использовать перечисление в качестве цвета для каждого маркера. Однако если у вас есть дополнительные цветовые элементы или вы не хотите использовать существующие значения в этом порядке, можно упорядочить список пользовательских цветовых элементов в соответствии с вашими потребностями и вернуть соответствующий индекс в этот список. Просто не забудьте привести индекс к элементу <xref:Microsoft.VisualStudio.Package.TokenColor> при его сохранении в <xref:Microsoft.VisualStudio.Package.TokenInfo> структуре; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] видит только индекс.

### <a name="example"></a>Пример
 В следующем примере показано, как средство проверки может обозначать три типа токенов: числа, знаки препинания и идентификаторы (все, что не является числом или знаками препинания). Этот пример предназначен только для наглядных целей и не представляет исчерпывающую реализацию средства синтаксического анализа и проверки. Предполагается, что существует `Lexer` класс с `GetNextToken()` методом, который возвращает строку.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>См. также
- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)
- [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
