---
title: Пользовательские свойства документа в устаревших языковых службах
description: Узнайте, как создавать настраиваемые свойства документов, отображаемые в окно свойств Visual Studio в рамках языковой службы прежних версий.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e154ba5e6ce4c85f597957b1d6704ca341b3c4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091153"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Пользовательские свойства документа в языковой службе прежних версий
Свойства документа можно отобразить в окне " [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **свойства** ". Языки программирования обычно не имеют свойств, связанных с отдельными файлами исходного кода. Однако XML поддерживает свойства документа, которые влияют на кодировку, схему и таблицу стилей.

## <a name="discussion"></a>Разговор
 Если языку требуются пользовательские свойства документа, необходимо создать класс, производный от <xref:Microsoft.VisualStudio.Package.DocumentProperties> класса, и реализовать необходимые свойства в производном классе.

 Кроме того, свойства документа обычно хранятся в самом исходном файле. Для этого необходимо, чтобы языковая служба проанализировала сведения о свойствах из исходного файла, чтобы они отображались в окне **Свойства** , и обновить исходный файл при внесении изменений в свойства документа в окне **свойства** .

## <a name="customize-the-documentproperties-class"></a>Настройка класса DocumentProperties
 Для поддержки пользовательских свойств документа необходимо создать класс, производный от класса, <xref:Microsoft.VisualStudio.Package.DocumentProperties> и добавить столько свойств, сколько требуется. Кроме того, необходимо предоставить атрибуты пользователя, чтобы упорядочить их в окне **свойств** . Если свойство имеет только `get` метод доступа, оно отображается в окне **свойств** как доступное только для чтения. Если свойство имеет `get` `set` методы доступа и, свойство также может быть Обновлено в окне **Свойства** .

### <a name="example"></a>Пример
 Ниже приведен пример класса, производного от <xref:Microsoft.VisualStudio.Package.DocumentProperties> , в котором показаны два свойства `Filename` и `Description` . При обновлении свойства <xref:Microsoft.VisualStudio.Package.LanguageService> вызывается пользовательский метод класса для записи свойства в исходный файл.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestDocumentProperties : DocumentProperties
    {
        private string m_filename;
        private string m_description;

        public TestDocumentProperties(CodeWindowManager mgr)
            : base(mgr)
        {
        }

        // Helper function to initialize this property without
        // going through the FileName property (which does a lot
        // more than we need when the filename is set).
        public void SetFileName(string filename)
        {
            m_filename = filename;
        }

        // Helper function to initialize this property without
        // going through the Description property (which does a lot
        // more than we need when the description is set).
        public void SetDescription(string description)
        {
            m_description = description;
        }

        ////////////////////////////////////////////////////////////
        // The document properties

        [CategoryAttribute("General")]
        [DescriptionAttribute("Name of the file")]
        [DisplayNameAttribute("Filename")]
        public string FileName
        {
            get { return m_filename; }
            set
            {
               if (value != m_filename)
               {
                    m_filename = value;
                    SetPropertyValue("Filename", m_filename);
               }
            }
        }

        [CategoryAttribute("General")]
        [DescriptionAttribute("Description of the file")]
        [DisplayNameAttribute("Description")]
        public string Description
        {
            get { return m_description; }
            set
            {
                if (value != m_description)
                {
                    m_description = value;
                    SetPropertyValue("Description", m_description);
                }
            }
        }

        ///////////////////////////////////////////////////////////
        // Private methods.

        private void SetPropertyValue(string propertyName, string propertyValue)
        {
            Source src = this.GetSource();
            if (src != null)
            {
                TestLanguageService service = src.LanguageService as TestLanguageService;
                if (service != null)
                {
                    // Set the property in to the source file.
                    service.SetPropertyValue(src, propertyName, propertyValue);
                }
            }
        }
    }
}
```

## <a name="instantiate-the-custom-documentproperties-class"></a>Создание экземпляра пользовательского класса DocumentProperties
 Чтобы создать экземпляр класса пользовательских свойств документа, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> метод в версии <xref:Microsoft.VisualStudio.Package.LanguageService> класса, чтобы он возвращал единственный экземпляр <xref:Microsoft.VisualStudio.Package.DocumentProperties> класса.

### <a name="example"></a>Пример

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        private TestDocumentProperties m_documentProperties;

        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)
        {
            if (m_documentProperties == null)
            {
                m_documentProperties = new TestDocumentProperties(mgr);
            }
            return m_documentProperties;
        }
    }
}
```

## <a name="properties-in-the-source-file"></a>Свойства в исходном файле
 Так как свойства документа обычно относятся к исходному файлу, значения хранятся в самом исходном файле. Для этого требуется поддержка синтаксического анализатора или сканера языка для определения этих свойств. Например, свойства XML-документа хранятся в корневом узле. Значения в корневом узле изменяются при изменении значений окна **свойств** , а корневой узел обновляется в редакторе.

### <a name="example"></a>Пример
 В этом примере сохраняются свойства `Filename` и `Description` в первых двух строках исходного файла, внедренных в специальный заголовок комментария:

```
//!Filename = file.testext
//!Description = A sample file
```

 В этом примере показаны два метода, необходимые для получения и задания свойств документа из первых двух строк исходного файла, а также сведения об обновлении свойств, если пользователь изменяет исходный файл напрямую. `SetPropertyValue`Метод в приведенном ниже примере является тем же, который вызывался из `TestDocumentProperties` класса, как показано в разделе *Настройка класса DocumentProperties* .

 В этом примере сканер используется для определения типа маркеров в первых двух строках. Этот пример предназначен только для демонстрационных целей. Более типичный подход к такой ситуации заключается в анализе исходного файла в том, что называется деревом синтаксического анализа, где каждый узел дерева содержит сведения об определенном токене. Корневой узел будет содержать свойства документа.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    // TokenType.Comment is the last item in that enumeration.
    public enum TestTokenTypes
    {
        DocPropertyLine = TokenType.Comment + 1,
        DocPropertyName,
        DocPropertyAssign,
        DocPropertyValue
    }

    class TestLanguageService : LanguageService
    {
        // Search this many lines from the beginning for properties.
        private static int maxLinesToSearch = 2;

        private TestDocumentProperties m_documentProperties;

        // Called whenever a full parsing operation has completed.
        public override void OnParseComplete(ParseRequest req)
        {
            if (m_documentProperties != null)
            {
                Source src = GetSource(req.View);
                if (src != null)
                {
                    string value = GetPropertyValue(src, "Filename");
                    m_documentProperties.SetFileName(value);

                    value = GetPropertyValue(src, "Description");
                    m_documentProperties.SetDescription(value);

                    // Update the Properties Window.
                    m_documentProperties.Refresh();
                }
            }
        }

        // Retrieves the specified property value from the given source.
        public string GetPropertyValue(Source src, string propertyName)
        {
            string propertyValue = "";

            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    string      line;
                    TokenInfo[] lineInfo = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line.
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                for ( ;
                                     tokenIndex < lineInfo.Length;
                                     tokenIndex++)
                                {
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)
                                    {
                                        break;
                                    }
                                }
                                if (tokenIndex < lineInfo.Length)
                                {
                                    propertyValue = src.GetText(i,
                                                          lineInfo[tokenIndex].StartIndex,
                                                          i,
                                                          lineInfo[tokenIndex].EndIndex + 1);
                                }
                                break;
                            }
                        }
                    }
                }
            }
            return propertyValue;
        }

        // Sets the specified property into the given source file.
        // Called from the TestDocumentProperties class.
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)
        {
            string newLine;

            if (propertyName == null || propertyName == "")
            {
                // No property name, so nothing to do
                return;
            }
            if (propertyValue == null)
            {
                propertyValue = "";
            }
            // This is the line to be inserted.
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);

            // First, find the line on which the property belongs.
            // If line is found, replace it.
            // Otherwise, insert the line at the beginning of the file.
            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    int         lineNumber = -1;
                    string      line;
                    TokenInfo[] lineInfo   = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                lineNumber = i;
                                break;
                            }
                        }
                    }

                    // Set up an undo context that also handles the insert/replace.
                    EditArray editArray = new EditArray(src,
                                                        true,
                                                        "Update Property");
                    if (editArray != null)
                    {
                        TextSpan span = new TextSpan();
                        if (lineNumber != -1)
                        {
                            // Replace line.
                            int lineLength = 0;
                            src.GetTextLines().GetLengthOfLine(lineNumber,
                                                               out lineLength);
                            span.iStartLine  = lineNumber;
                            span.iStartIndex = 0;
                            span.iEndLine    = lineNumber;
                            span.iEndIndex   = lineLength;
                        }
                        else
                        {
                            // Insert new line.
                            span.iStartLine  = 0;
                            span.iStartIndex = 0;
                            span.iEndLine    = 0;
                            span.iEndIndex   = 0;
                            newLine += "\n";
                        }
                        editArray.Add(new EditSpan(span, newLine));
                        editArray.ApplyEdits();
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>См. также
- [Функции устаревшей языковой службы](../../extensibility/internals/legacy-language-service-features1.md)
