---
title: Переформатирование кода в языковой службе прежних версий | Документация Майкрософт
description: Сведения о включении поддержки для повторного форматирования исходного кода для языковой службы Visual Studio прежних версий.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e8dc10e4def3e4725bb4f64041cdb17146b9d84d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060865"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Переформатирование кода в языковой службе прежних версий

В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] исходном коде можно переформатировать путем нормализации использования отступов и пробелов. Это может быть Вставка или удаление пробелов или табуляций в начале каждой строки, добавление новых линий между строками или замена пробелов символами табуляции или табуляции пробелами.

> [!NOTE]
> Вставка или удаление символов новой строки может повлиять на маркеры, такие как точки останова и закладки, но добавление или удаление пробелов или символов табуляции не влияет на маркеры.

Пользователи могут начать операцию переформатирования, выбрав **Формат выбор** или **Формат документа** в меню " **Дополнительно** " в меню " **Правка** ". Операция переформатирования может также запускаться при вставке фрагмента кода или определенного символа. Например, при вводе закрывающей фигурной скобки в C# все между соответствующей открывающей фигурной скобкой и закрывающей фигурной скобкой автоматически смещается на соответствующий уровень.

При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отправке команды **Форматировать фрагмент** или **Формат документа** в языковую службу <xref:Microsoft.VisualStudio.Package.ViewFilter> класс вызывает <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> классе. Для поддержки форматирования необходимо переопределить <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> метод и указать собственный код форматирования.

## <a name="enabling-support-for-reformatting"></a>Включение поддержки переформатирования

Для поддержки форматирования `EnableFormatSelection` параметр <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> должен быть установлен в значение `true` при регистрации пакета VSPackage. При этом свойству присваивается значение <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> `true` . <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>Метод возвращает значение этого свойства. Если он возвращает значение true, <xref:Microsoft.VisualStudio.Package.ViewFilter> класс вызывает <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

## <a name="implementing-reformatting"></a>Реализация переформатирования

Чтобы реализовать переформатирование, необходимо создать класс, производный от <xref:Microsoft.VisualStudio.Package.Source> класса, и переопределить <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> метод. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Объект описывает диапазон для форматирования, а <xref:Microsoft.VisualStudio.Package.EditArray> объект содержит изменения, внесенные в диапазон. Обратите внимание, что этот диапазон может быть документом целиком. Однако, поскольку, вероятно, будет несколько изменений, внесенных в диапазон, все изменения должны быть обратимыми в одном действии. Чтобы сделать это, заключите все изменения в <xref:Microsoft.VisualStudio.Package.CompoundAction> объект (см. раздел "использование класса компаундактион" этой статьи).

### <a name="example"></a>Пример

В следующем примере проверяется наличие одного пробела после каждой запятой в выделенном фрагменте, если только запятая не содержит знак табуляции или не находится в конце строки. Конечные пробелы после последней запятой в строке удаляются. Сведения о вызове этого метода из метода см. в подразделе "использование класса Компаундактион" этого раздела <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        private void DoFormatting(EditArray mgr, TextSpan span)
        {
            // Make sure there is one space after every comma unless followed
            // by a tab or comma is at end of line.
            IVsTextLines pBuffer = GetTextLines();
            if (pBuffer != null)
            {
                int    startIndex = span.iStartIndex;
                int    endIndex   = 0;
                string line       = "";
                // Loop over all lines in span
                for (int i = span.iStartLine; i <= span.iEndLine; i++)
                {
                    if (i < span.iEndLine)
                    {
                        pBuffer.GetLengthOfLine(i, out endIndex);
                    }
                    else
                    {
                        endIndex = span.iEndIndex;
                    }
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);

                    if (line.Length > 0)
                    {
                        int index = 0;
                        // Loop over all commas in line
                        while ((index = line.IndexOf(',', index)) != -1)
                        {
                            int spaceIndex = index + 1;
                            // Determine how many spaces after comma
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')
                            {
                                ++spaceIndex;
                            }

                            int      spaceCount      = spaceIndex - (index + 1);
                            string   replacementText = " ";
                            bool     fDoEdit         = true;
                            TextSpan editTextSpan    = new TextSpan();

                            editTextSpan.iStartLine  = i;
                            editTextSpan.iEndLine    = i;
                            editTextSpan.iStartIndex = index + 1;

                            if (spaceIndex == line.Length)
                            {
                                if (spaceCount > 0)
                                {
                                    // Delete spaces after a comma at end of line
                                    editTextSpan.iEndIndex = spaceIndex;
                                    replacementText = "";
                                }
                                else
                                {
                                    // Otherwise, do not add spaces if comma is
                                    // at end of line.
                                    fDoEdit = false;
                                }
                            }
                            else if (spaceCount == 0)
                            {
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')
                                {
                                    // Do not insert space if a tab follows
                                    // a comma.
                                    fDoEdit = false;
                                }
                                else
                                {
                                    // No space after comma so add a space.
                                    editTextSpan.iEndIndex = index + 1;
                                }
                            }
                            else if (spaceCount > 1)
                            {
                                // More than one space after comma, replace
                                // with a single space.
                                editTextSpan.iEndIndex = spaceIndex;
                            }
                            else
                            {
                                // Single space after a comma and not at end
                                // of the line, leave it alone.
                                fDoEdit = false;
                            }
                            if (fDoEdit)
                            {
                                // Add edit operation
                                mgr.Add(new EditSpan(editTextSpan, replacementText));
                            }
                            index = spaceIndex;
                        }
                    }
                    startIndex = 0; // All subsequent lines start at 0
                }
                // Apply all edits
                mgr.ApplyEdits();
            }
        }
    }
}
```

## <a name="using-the-compoundaction-class"></a>Использование класса Компаундактион

Все переформатирование, выполненное в разделе кода, должно быть обратимым в одном действии. Это можно сделать с помощью <xref:Microsoft.VisualStudio.Package.CompoundAction> класса. Этот класс служит оболочкой для набора операций редактирования текстового буфера в одну операцию редактирования.

### <a name="example"></a>Пример

Ниже приведен пример использования <xref:Microsoft.VisualStudio.Package.CompoundAction> класса. Пример метода см. в примере в разделе "реализация поддержки форматирования" этого раздела `DoFormatting` .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override void ReformatSpan(EditArray mgr, TextSpan span)
        {
            string description = "Reformat code";
            CompoundAction ca = new CompoundAction(this, description);
            using (ca)
            {
                ca.FlushEditActions();      // Flush any pending edits
                DoFormatting(mgr, span);    // Format the span
            }
        }
    }
}
```

## <a name="see-also"></a>См. также

- [Функции языковой службы прежних версий](legacy-language-service-features1.md)
