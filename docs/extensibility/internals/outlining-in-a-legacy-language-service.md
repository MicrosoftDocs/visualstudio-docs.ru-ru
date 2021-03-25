---
title: Структурирование в языковой службе прежних версий | Документация Майкрософт
description: Узнайте, как реализовать структуризацию с помощью реализации скрытых регионов в языковой службе прежних версий.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a56d755341aa611f0e2762f6bae8940778fe0864
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062958"
---
# <a name="outlining-in-a-legacy-language-service"></a>Структурирование в языковой службе прежних версий
Структура позволяет сворачивать сложную программу в обзор или структуру. Например, в C# все методы можно сворачивать в одну строку, отображая только сигнатуру метода. Кроме того, структуры и классы можно сворачивать, чтобы отображались только имена структур и классов. Внутри одного метода можно свернуть сложную логику, чтобы показать общий поток, отображая только первую строку инструкций `foreach` , например, `if` и `while` .

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [Пошаговое руководство. структурирование](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="enabling-support-for-outlining"></a>Включение поддержки структурирования
 Параметр `AutoOutlining` реестра имеет значение 1, чтобы включить автоматическую структуризацию. Автоматическое структурирование устанавливает синтаксический анализ всего источника при загрузке или изменении файла для обнаружения скрытых областей и отображения глифов структуры. Структурирование может также управляться пользователем вручную.

 Значение `AutoOutlining` записи реестра можно получить с помощью <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. `AutoOutlining`Запись реестра может быть инициализирована с помощью именованного параметра для <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибута (Дополнительные сведения см. в разделе [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service1.md) ).

## <a name="the-hidden-region"></a>Скрытая область
 Чтобы обеспечить структуризацию, языковая служба должна поддерживать скрытые регионы. Они охватывают текст, который можно развернуть или свернуть. Скрытые области могут быть разделены стандартными символами языка, например фигурными скобками, или пользовательскими символами. Например, в C# есть `#region` / `#endregion` пара, которая отделяет скрытую область.

 Скрытые области управляются скрытым диспетчером областей, который предоставляется в качестве <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> интерфейса.

 При структурировании используются скрытые области <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> интерфейса, которые содержат диапазон скрытой области, текущее видимое состояние и баннер, отображаемый при свертывании диапазона.

 Средство синтаксического анализа языковой службы использует <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> метод для добавления новой скрытой области с поведением по умолчанию для скрытых регионов, в то время как <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> метод позволяет настраивать внешний вид и поведение структуры. После того как скрытые регионы передаются в сеанс скрытой области, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] управляет скрытыми областями языковой службы.

 Если необходимо определить время уничтожения сеанса скрытой области, изменяется скрытая область или необходимо убедиться в том, что конкретная скрытая область видима. необходимо создать класс, производный от <xref:Microsoft.VisualStudio.Package.Source> класса, и переопределить соответствующие методы,, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> и <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> соответственно.

### <a name="example"></a>Пример
 Ниже приведен упрощенный пример создания скрытых областей для всех пар фигурных скобок. Предполагается, что язык содержит парные скобки, а фигурные скобки — как минимум фигурные скобки ({и}). Этот подход предназначен только для наглядных целей. Полная реализация будет иметь полную обработку вариантов в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . В этом примере также показано, как задать для параметра значение « <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> `true` временно». В качестве альтернативы можно указать `AutoOutlining` именованный параметр в `ProvideLanguageServiceAttribute` атрибуте языкового пакета.

 В этом примере предполагается, что правила C# для комментариев, строк и литералов.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>См. также
- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
