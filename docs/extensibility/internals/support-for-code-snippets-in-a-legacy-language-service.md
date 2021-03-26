---
title: Поддержка фрагментов кода в языковой службе прежних версий | Документация Майкрософт
description: Узнайте, как устаревшая языковая служба поддерживает фрагменты кода. Фрагмент кода — это фрагмент кода, который вставляется в исходный файл.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9578159554f77a9ad7553a56c054a863b3b63fd5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080766"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Поддержка фрагментов кода в языковой службе прежних версий
Фрагмент кода — это фрагмент кода, который вставляется в исходный файл. Сам фрагмент кода является шаблоном на основе XML с набором полей. Эти поля выделяются после вставки фрагмента и могут иметь различные значения в зависимости от контекста, в котором вставляется фрагмент. Сразу после вставки фрагмента кода языковая служба может отформатировать фрагмент.

 Фрагмент кода вставляется в Специальный режим редактирования, который позволяет переходить к полям фрагмента кода с помощью клавиши TAB. Поля могут поддерживать раскрывающиеся меню в стиле IntelliSense. Пользователь фиксирует фрагмент кода в исходном файле, вводя клавишу ВВОД или ESC. Дополнительные сведения о фрагментах см. в разделе [фрагменты кода](../../ide/code-snippets.md).

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [Пошаговое руководство. Реализация фрагментов кода](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="managed-package-framework-support-for-code-snippets"></a>Поддержка платформ управляемых пакетов для фрагментов кода
 Платформа управляемого пакета (MPF) поддерживает большинство функций фрагментов кода, от чтения шаблона до вставки фрагмента и включения специального режима редактирования. Управление поддержкой осуществляется через <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класс.

 При <xref:Microsoft.VisualStudio.Package.Source> создании экземпляра класса <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> вызывается метод класса для получения <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта (Обратите внимание, что базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс всегда возвращает новый <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объект для каждого <xref:Microsoft.VisualStudio.Package.Source> объекта).

 MPF не поддерживает функции расширения. Функция расширения — это именованная функция, внедренная в шаблон фрагмента и возвращающая одно или несколько значений, помещаемых в поле. Значения возвращаются языковой службой через <xref:Microsoft.VisualStudio.Package.ExpansionFunction> объект. <xref:Microsoft.VisualStudio.Package.ExpansionFunction>Объект должен быть реализован языковой службой для поддержки функций расширения.

## <a name="providing-support-for-code-snippets"></a>Предоставление поддержки фрагментов кода
 Чтобы включить поддержку фрагментов кода, необходимо предоставить или установить фрагменты, и необходимо предоставить пользователям средства для вставки этих фрагментов. Включить поддержку фрагментов кода можно тремя шагами:

1. Установка файлов фрагментов кода.

2. Включение фрагментов кода для языковой службы.

3. Вызов <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта.

### <a name="installing-the-snippet-files"></a>Установка файлов фрагментов кода
 Все фрагменты кода для языка хранятся в виде шаблонов в XML-файлах, обычно по одному шаблону фрагментов для каждого файла. Дополнительные сведения о схеме XML, используемой для шаблонов фрагментов кода, см. в разделе [Справочник по схеме фрагментов кода](../../ide/code-snippets-schema-reference.md). Каждый шаблон фрагмента идентифицируется с помощью идентификатора языка. Этот идентификатор языка указан в реестре и помещается в `Language` атрибут \<Code> тега в шаблоне.

 Обычно существуют два расположения, где хранятся файлы шаблонов фрагментов: 1), где установлен язык, и 2) в папке пользователя. Эти расположения добавляются в реестр, чтобы **Диспетчер фрагментов кода** Visual Studio мог найти фрагменты. Папка пользователя — это место, где хранятся фрагменты кода, созданные пользователем.

 Типичный макет папки для установленных файлов шаблона фрагментов выглядит следующим образом: *[InstallRoot]* \\ *[тестлангуаже]* \snippets код \\ *[LCID]* \сниппетс.

 *[InstallRoot]* — папка, в которой установлен язык.

 *[Тестлангуаже]* — имя вашего языка в виде имени папки.

 *[LCID]* — это код локали. Вот как хранятся локализованные версии фрагментов кода. Например, код локали для английского языка — 1033, поэтому *[LCID]* заменяется на 1033.

 Необходимо указать один дополнительный файл, который является файлом индекса, обычно именуемым SnippetsIndex.xml или ExpansionsIndex.xml (можно использовать любое допустимое имя файла, завершающее. XML). Этот файл обычно хранится в папке *[InstallRoot]* \\ *[тестлангуаже]* и указывает точное расположение папки фрагментов, а также идентификатор языка и идентификатор GUID языковой службы, которая использует фрагменты кода. Точный путь к файлу индекса помещается в реестр, как описано далее в разделе "Установка записей реестра". Ниже приведен пример файла SnippetsIndex.xml.

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 \<Language>Тег указывает идентификатор языка ( `Lang` атрибут) и GUID языковой службы.

 В этом примере предполагается, что вы установили языковую службу в папку установки Visual Studio. % LCID% заменяется текущим ИДЕНТИФИКАТОРом локали пользователя. \<SnippetDir>Можно добавить несколько тегов, по одному для каждого другого каталога и языкового стандарта. Кроме того, папка фрагментов может содержать вложенные папки, каждый из которых определен в файле индекса с \<SnippetSubDir> тегом, внедренным в \<SnippetDir> тег.

 Пользователи также могут создавать собственные фрагменты кода для вашего языка. Обычно они хранятся в папке параметров пользователя, например *[тестдокс]* фрагменты \Коде \\ *[тестлангуаже]* \тест фрагменты кода, где *[тестдокс]* — это расположение папки параметров пользователя для Visual Studio.

 Следующие элементы подстановки могут быть помещены в путь, хранящийся в \<DirPath> теге в файле индекса.

|Элемент|Описание|
|-------------|-----------------|
|НАМНОГО|Код языка.|
|InstallRoot|Корневая папка установки Visual Studio, например C:\Program Files\Microsoft Visual Studio 8.|
|% Прождир%|Папка, содержащая текущий проект.|
|% Прожитем%|Папка, содержащая текущий элемент проекта.|
|% Тестдокс%|В папке параметров пользователя, например C:\Documents и Settings \\ *[username]* \ Documents\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Включение фрагментов кода для языковой службы
 Вы можете включить фрагменты кода для языковой службы, добавив <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> атрибут в VSPackage (Дополнительные сведения см. в разделе [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service1.md) ). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A>Параметры и <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> являются необязательными, но необходимо включить `SearchPaths` именованный параметр, чтобы информировать **Диспетчер фрагментов кода** о расположении фрагментов.

 Ниже приведен пример использования этого атрибута.

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Вызов поставщика расширения
 Языковая служба управляет вставкой фрагмента кода, а также способом вызова вставки.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Вызов поставщика расширения для фрагментов кода
 Существует два способа вызвать поставщик расширения: с помощью команды меню или с помощью ярлыка из списка завершения.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Вставка фрагмента кода с помощью команды меню
 Чтобы использовать команду меню для просмотра браузера фрагментов кода, добавьте команду меню, а затем вызовите <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> метод в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> интерфейсе в ответ на эту команду меню.

1. Добавьте команду и кнопку в vsct-файл. Вы можете найти инструкции по [созданию расширения с помощью команды меню](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Создайте класс, производный от <xref:Microsoft.VisualStudio.Package.ViewFilter> класса, и переопределите <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> метод, чтобы указать поддержку для новой команды меню. В этом примере всегда включается команда меню.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. Переопределите <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> метод в <xref:Microsoft.VisualStudio.Package.ViewFilter> классе, чтобы получить <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объект и вызвать <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> метод для этого объекта.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     Следующие методы <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса вызываются Visual Studio в заданном порядке во время вставки фрагмента кода:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     После <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> вызова метода фрагмент был вставлен, а <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объект находится в специальном режиме редактирования, используемом для изменения только что вставленного фрагмента.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Вставка фрагмента кода с помощью ярлыка
 Реализация ярлыка из списка завершения является гораздо более сложной, чем реализация команды меню. Сначала необходимо добавить ярлыки фрагментов кода в список завершения слов IntelliSense. Затем необходимо обнаружить, что имя ярлыка фрагмента было вставлено в результате завершения. Наконец, необходимо получить заголовок фрагмента и путь, используя имя ярлыка, и передать эти сведения в <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> метод <xref:Microsoft.VisualStudio.Package.ExpansionProvider> метода.

 Чтобы добавить ярлыки фрагментов кода в список завершения слов, добавьте их в <xref:Microsoft.VisualStudio.Package.Declarations> объект <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса. Необходимо убедиться в том, что ярлык можно найти в виде имени фрагмента. Пример см. в разделе [Пошаговое руководство. Получение списка установленных фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Можно обнаружить вставку ярлыка фрагмента кода в <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> методе <xref:Microsoft.VisualStudio.Package.Declarations> класса. Поскольку имя фрагмента уже вставлено в исходный файл, оно должно быть удалено при вставке расширения. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>Метод принимает диапазон, описывающий точку вставки фрагмента. Если диапазон включает в исходный файл все имя фрагмента, это имя заменяется фрагментом.

 Ниже приведена версия <xref:Microsoft.VisualStudio.Package.Declarations> класса, который обрабатывает вставку фрагментов по имени ярлыка. Другие методы <xref:Microsoft.VisualStudio.Package.Declarations> класса были опущены для ясности. Обратите внимание, что конструктор этого класса принимает <xref:Microsoft.VisualStudio.Package.LanguageService> объект. Это может быть передано из версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта (например, ваша реализация <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса может взять <xref:Microsoft.VisualStudio.Package.LanguageService> объект в своем конструкторе и передать этот объект в `TestDeclarations` конструктор класса).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 Когда языковая служба получает имя ярлыка, она вызывает <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> метод для получения имени файла и заголовка фрагмента кода. Затем языковая служба вызывает <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> метод в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> классе для вставки фрагмента кода. Следующие методы вызываются Visual Studio в заданном порядке в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> классе в процессе вставки фрагмента кода:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Дополнительные сведения о получении списка установленных фрагментов кода для языковой службы см. в разделе [Пошаговое руководство. Получение списка установленных фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Реализация класса Експансионфунктион
 Функция расширения — это именованная функция, внедренная в шаблон фрагмента и возвращающая одно или несколько значений, помещаемых в поле. Для поддержки функций расширения в языковой службе необходимо создать класс, производный от <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класса, и реализовать <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> метод. Затем необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> классе, чтобы он возвращал новый экземпляр <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класса для каждой поддерживаемой функции расширения. Если поддерживается список возможных значений из функции расширения, необходимо также переопределить <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> метод в <xref:Microsoft.VisualStudio.Package.ExpansionFunction> классе, чтобы он возвращал список этих значений.

 Функция расширения, которая принимает аргументы или требует доступа к другим полям, не должна быть связана с изменяемым полем, так как поставщик расширения может быть не полностью инициализирован на момент вызова функции расширения. В результате функция расширения не может получить значение своих аргументов или любое другое поле.

### <a name="example"></a>Пример
 Ниже приведен пример того, как `GetName` может быть реализована простая функция расширения. Эта функция расширения добавляет число к имени базового класса каждый раз при создании экземпляра функции расширения (которая соответствует каждому вставленному фрагменту кода).

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>См. также
- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Фрагменты кода](../../ide/code-snippets.md)
- [Пошаговое руководство. Получение списка установленных фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
