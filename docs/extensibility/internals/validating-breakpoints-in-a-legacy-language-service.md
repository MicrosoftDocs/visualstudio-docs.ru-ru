---
title: Проверка точек останова в языковой службе прежних версий | Документация Майкрософт
description: Узнайте, как можно переопределить метод Валидатебреакпоинтлокатион в языковой службе прежних версий для проверки точек останова перед запуском отладчика.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 86029300c34e111344157bf39a15dceab8c1b77a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085797"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Проверка точек останова в языковой службе прежних версий
Точка останова указывает, что выполнение программы должно останавливаться в определенной точке во время ее выполнения в отладчике. Пользователь может поместить точку останова в любую строку исходного файла, так как редактор не имеет сведений о том, что представляет собой допустимое расположение для точки останова. При запуске отладчика все отмеченные точки останова (называемые ожидающими точками останова) привязываются к соответствующему расположению в выполняющейся программе. В то же время проверка точек останова выполняется, чтобы убедиться, что они помечают допустимые расположения кода. Например, точка останова в комментарии является недопустимой, так как в исходном коде отсутствует код в этом месте. Отладчик отключает недопустимые точки останова.

 Поскольку языковая служба знает о отображаемом исходном коде, она может проверить точки останова перед запуском отладчика. Можно переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> метод, чтобы он возвращал диапазон, указывающий допустимое расположение точки останова. Расположение точки останова по-прежнему проверяется при запуске отладчика, но пользователь получает уведомления о недопустимых точках останова, не дожидаясь загрузки отладчика.

## <a name="implementing-support-for-validating-breakpoints"></a>Реализация поддержки для проверки точек останова

- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>Методу присваивается расположение точки останова. Ваша реализация должна решить, является ли расположение допустимым, и указать это путем возвращения текстового диапазона, определяющего код, связанный с положением точки останова в строке.

- Возвращает значение <xref:Microsoft.VisualStudio.VSConstants.S_OK> , если расположение является допустимым, или <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> значение, если оно является недопустимым.

- Если точка останова является допустимой, то текстовый диапазон выделяется вместе с точкой останова.

- Если точка останова недопустима, в строке состояния появится сообщение об ошибке.

### <a name="example"></a>Пример
 В этом примере показана реализация <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> метода, который вызывает средство синтаксического анализа для получения диапазона кода (если есть) в указанном расположении.

 В этом примере предполагается, что вы добавили `GetCodeSpan` в <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс метод, который проверяет текстовый диапазон и возвращает, `true` если это допустимое расположение точки останова.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```

## <a name="see-also"></a>См. также
- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)
