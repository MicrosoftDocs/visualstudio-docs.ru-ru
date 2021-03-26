---
title: Комментирование кода в языковой службе прежних версий | Документация Майкрософт
description: Сведения о классах управляемых пакетов Framework (MPF), которые обеспечивают поддержку комментирования кода в языковой службе прежних версий в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c712f1458aa182abcf9e10bee6c6cf90e11b194d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057108"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Код комментария в языковой службе прежних версий
Языки программирования обычно предоставляют средства для добавления заметок или комментирования кода. Комментарий — это раздел текста, содержащий дополнительные сведения о коде, но пропускаемый во время компиляции или интерпретации.

 Классы Managed Package Framework (MPF) обеспечивают поддержку комментирования и раскомментирования выделенного текста.

## <a name="comment-styles"></a>Стили комментариев
Существует два общих стиля комментариев:

1. Комментарии строки, где комментарий находится в одной строке.

2. Блокировать комментарии, в которых комментарий может включать несколько строк.

Комментарии в строках обычно имеют начальный символ (или символы), а в комментариях к блокам — начальные и конечные символы. Например, в C# строчный комментарий начинается с `//` , а блок комментария начинается с `/*` и заканчивается на `*/` .

Когда пользователь выбирает командный **Комментарий** в меню **Правка**  >  **Дополнительно** , команда направляется к <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> методу <xref:Microsoft.VisualStudio.Package.Source> класса. Когда пользователь выбирает команду **раскомментировать выделенный фрагмент**, команда направляется в <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> метод.

## <a name="support-code-comments"></a>Комментарии к коду поддержки
 Языковая служба может поддерживать комментарии кода с помощью `EnableCommenting` именованного параметра <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . При этом задается <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Дополнительные сведения о настройке функций языковой службы см. [в статье регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Также необходимо переопределить метод, <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> чтобы он возвращал <xref:Microsoft.VisualStudio.Package.CommentInfo> структуру с символами комментария для вашего языка. Символы комментария строки в стиле C# используются по умолчанию.

### <a name="example"></a>Пример
 Ниже приведен пример реализации <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> метода.

```csharp
using Microsoft.VisualStudio.Package;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override CommentInfo GetCommentFormat() {
            CommentInfo info = new CommentInfo();
            info.LineStart       = "//";
            info.BlockStart      = "/*";
            info.BlockEnd        = "*/";
            info.UseLineComments = true;
            return info;
        }
    }
}
```

## <a name="see-also"></a>См. также
- [Функции устаревшей языковой службы](../../extensibility/internals/legacy-language-service-features1.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
