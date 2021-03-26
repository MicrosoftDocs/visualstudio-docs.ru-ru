---
title: Реализация устаревшего языка S2 | Документация Майкрософт
description: Узнайте, как реализовать устаревшую языковую службу, поддерживающую функции расширенной языковой службы, с помощью платформы управляемых пакетов (MPF). Часть 2 из 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9bdb0d05faaa139b808d8d117125c5208da470e9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085823"
---
# <a name="implementing-a-legacy-language-service-2"></a>Реализация языковой службы версии 2
Чтобы реализовать языковую службу с помощью управляемой платформы пакетов (MPF), необходимо создать класс из <xref:Microsoft.VisualStudio.Package.LanguageService> класса и реализовать следующие абстрактные методы и свойства:

- метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> ;

- метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> ;

- метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ;

- Свойство <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>.

  Дополнительные сведения о реализации этих методов и свойств см. в соответствующих разделах ниже.

  Для поддержки дополнительных функций языковой службе может потребоваться создать производный класс от одного из классов языковой службы MPF. Например, для поддержки дополнительных команд меню необходимо создать класс, производный от <xref:Microsoft.VisualStudio.Package.ViewFilter> класса, и переопределить несколько методов обработки команд (см <xref:Microsoft.VisualStudio.Package.ViewFilter> . Дополнительные сведения). <xref:Microsoft.VisualStudio.Package.LanguageService>Класс предоставляет ряд методов, которые вызываются для создания новых экземпляров различных классов, и вы переопределяете соответствующий метод создания, чтобы предоставить экземпляр класса. Например, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> классе, чтобы он возвращал экземпляр вашего собственного <xref:Microsoft.VisualStudio.Package.ViewFilter> класса. Дополнительные сведения см. в разделе "создание экземпляров пользовательских классов".

  Языковая служба также может предоставлять собственные значки, которые используются во многих местах. Например, при отображении списка завершения IntelliSense каждый элемент в списке может иметь связанный с ним значок, помечая элемент как метод, класс, пространство имен, свойство или любое необходимое для вашего языка. Эти значки используются во всех списках IntelliSense, в **панели навигации** и в окне **Список ошибок** задач. Дополнительные сведения см. в разделе "образы языковой службы" ниже.

## <a name="getlanguagepreferences-method"></a>Метод Жетлангуажепреференцес
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>Метод всегда возвращает один и тот же экземпляр <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Базовый класс можно использовать, <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Если для языковой службы не требуются дополнительные параметры. Классы языковой службы MPF предполагают наличие по крайней мере базового <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.

### <a name="example"></a>Пример
 В этом примере показана типичная реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> метода. В этом примере используется базовый <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класс.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>Метод Scanner
 Этот метод возвращает экземпляр <xref:Microsoft.VisualStudio.Package.IScanner> объекта, который реализует синтаксический анализатор или сканер, используемый для получения маркеров и их типов и триггеров. Этот сканер используется в <xref:Microsoft.VisualStudio.Package.Colorizer> классе для выделения цветом, хотя сканер также можно использовать для получения типов токенов и триггеров в качестве версионного к более сложной операции синтаксического анализа. Необходимо предоставить класс, реализующий интерфейс, <xref:Microsoft.VisualStudio.Package.IScanner> и необходимо реализовать все методы <xref:Microsoft.VisualStudio.Package.IScanner> интерфейса.

### <a name="example"></a>Пример
 В этом примере показана типичная реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метода. `TestScanner`Класс реализует <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс (не показан).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>Метод Парсесаурце
 Анализирует исходный файл по ряду различных причин. Этому методу предоставляется <xref:Microsoft.VisualStudio.Package.ParseRequest> объект, который описывает, что ожидается из определенной операции синтаксического анализа. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Метод вызывает более сложное средство синтаксического анализа, определяющее функциональность и область действия токена. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Метод используется для поддержки операций IntelliSense, а также для сопоставления фигурных скобок. Даже если вы не поддерживаете такие расширенные операции, по-прежнему необходимо возвращать допустимый <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект, который требует создания класса, реализующего <xref:Microsoft.VisualStudio.Package.AuthoringScope> интерфейс, и реализации всех методов в этом интерфейсе. Можно вернуть значения NULL из всех методов, но <xref:Microsoft.VisualStudio.Package.AuthoringScope> сам объект не должен иметь значение null.

### <a name="example"></a>Пример
 В этом примере показана минимальная реализация <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода и <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса, достаточная для того, чтобы языковая служба была скомпилирована и функционировать без поддержки каких-либо дополнительных функций.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Свойство Name
 Это свойство возвращает имя языковой службы. Это имя должно совпадать с именем, заданным при регистрации языковой службы. Это имя используется в нескольких местах, самым заметным является класс, в котором <xref:Microsoft.VisualStudio.Package.LanguagePreferences> имя используется для доступа к реестру. Имя, возвращаемое этим свойством, не должно быть локализовано, так как оно используется в реестре для записи реестра и имен ключей.

### <a name="example"></a>Пример
 В этом примере показана одна возможная реализация <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Свойства. Обратите внимание, что имя здесь жестко запрограммировано: фактическое имя должно быть получено из файла ресурсов, чтобы его можно было использовать при регистрации языковой службы (см. раздел [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service1.md)).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>Создание экземпляров пользовательских классов
 Следующие методы в указанных классах могут быть переопределены для предоставления экземпляров собственных версий каждого класса.

### <a name="in-the-languageservice-class"></a>В классе Лангуажесервице

|Метод|Возвращаемый класс|Описание|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Для поддержки пользовательских дополнений к текстовому представлению.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Для поддержки пользовательских свойств документа.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Для поддержки **панели навигации**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Для поддержки функций в шаблонах фрагментов кода.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Для поддержки фрагментов кода (этот метод обычно не переопределен).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Для поддержки настройки <xref:Microsoft.VisualStudio.Package.ParseRequest> структуры (этот метод обычно не переопределен).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Для поддержки форматирования исходного кода, указания символов комментария и настройки сигнатур методов.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Для поддержки дополнительных команд меню.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Для поддержки выделения синтаксиса (этот метод обычно не переопределен).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Для поддержки доступа к параметрам языка. Этот метод должен быть реализован, но может возвращать экземпляр базового класса.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Для предоставления синтаксического анализатора, используемого для идентификации типов токенов в строке. Этот метод должен быть реализован и <xref:Microsoft.VisualStudio.Package.IScanner> должен быть производным от.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Для предоставления средства синтаксического анализа, используемого для определения функциональности и области действия во всем исходном файле. Этот метод должен быть реализован и должен возвращать экземпляр версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса. Если все, что требуется поддерживать, — выделение синтаксиса (для которого требуется <xref:Microsoft.VisualStudio.Package.IScanner> средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> , возвращаемое методом), вы можете не выполнять никаких действий в этом методе, кроме возврата версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса, методы которого возвращают значения NULL.|

### <a name="in-the-source-class"></a>В классе исходного кода

|Метод|Возвращаемый класс|Описание|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Для настройки вывода списков завершения IntelliSense (этот метод обычно не переопределен).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Для поддержки маркеров в списке задач список ошибок; в частности, поддержка функций перед открытием файла и переходом к строке, вызвавшей ошибку.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Для настройки вывода всплывающих подсказок параметров IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Для поддержки комментирования кода.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Для сбора сведений во время операции синтаксического анализа.|

### <a name="in-the-authoringscope-class"></a>В классе Аусорингскопе

|Метод|Возвращаемый класс|Описание|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Предоставляет список объявлений, таких как члены или типы. Этот метод должен быть реализован, но может возвращать значение null. Если этот метод возвращает допустимый объект, то объект должен быть экземпляром вашей версии <xref:Microsoft.VisualStudio.Package.Declarations> класса.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Предоставляет список сигнатур методов для данного контекста. Этот метод должен быть реализован, но может возвращать значение null. Если этот метод возвращает допустимый объект, то объект должен быть экземпляром вашей версии <xref:Microsoft.VisualStudio.Package.Methods> класса.|

## <a name="language-service-images"></a>Образы языковой службы
 Чтобы предоставить список значков, используемых в языковой службе, переопределите <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> классе и возвратите значение, <xref:System.Windows.Forms.ImageList> содержащее значки. Базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс загружает набор значков по умолчанию. Так как вы указываете точный индекс изображения в тех местах, которым требуются значки, способ организации собственного списка изображений полностью зависит от вас.

### <a name="images-used-in-intellisense-completion-lists"></a>Изображения, используемые в списках завершения IntelliSense
 Для списков завершения IntelliSense для каждого элемента в <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> методе класса указывается индекс изображения <xref:Microsoft.VisualStudio.Package.Declarations> , который необходимо переопределить, если необходимо указать индекс изображения. Значение, возвращаемое <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> методом, является индексом в списке изображений, предоставленным <xref:Microsoft.VisualStudio.Package.CompletionSet> конструктору класса, который является тем же списком изображений, возвращенным <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> методом в <xref:Microsoft.VisualStudio.Package.LanguageService> классе (вы можете изменить, какой список изображений следует использовать для, <xref:Microsoft.VisualStudio.Package.CompletionSet> Если Переопределите <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> метод в классе, <xref:Microsoft.VisualStudio.Package.Source> чтобы предоставить другой список изображений).

### <a name="images-used-in-the-navigation-bar"></a>Изображения, используемые на панели навигации
 На **панели навигации** отображаются списки типов и членов, которые используются для быстрой навигации, а также для отображения значков. Эти значки получаются из <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метода в <xref:Microsoft.VisualStudio.Package.LanguageService> классе и не могут быть переопределены специально для **панели навигации**. Индексы, используемые для каждого элемента в полях со списком, задаются, когда списки, представляющие поля со списком, заполняются в <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> методе <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса (см. раздел [Поддержка панели навигации в устаревшей языковой службе](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Эти индексы изображений получаются каким-либо образом из средства синтаксического анализа, как правило, через вашу версию <xref:Microsoft.VisualStudio.Package.Declarations> класса. Способ получения индексов полностью зависит от вас.

### <a name="images-used-in-the-error-list-task-window"></a>Изображения, используемые в окне задачи список ошибок
 Всякий раз, когда <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> средство синтаксического анализа методов (см. сведения об [анализаторе и сканере языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) обнаруживает ошибку и передает эту ошибку <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> методу в <xref:Microsoft.VisualStudio.Package.AuthoringSink> классе, в окне **Список ошибок** задачи отображается сообщение об ошибке. Значок может быть связан с каждым элементом, отображаемым в окне задачи, и этот значок поступает из того же списка изображений, который возвращается из <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метода в <xref:Microsoft.VisualStudio.Package.LanguageService> классе. Поведение по умолчанию для классов MPF — не показывать изображение с сообщением об ошибке. Однако это поведение можно переопределить, производя класс от <xref:Microsoft.VisualStudio.Package.Source> класса и переопределив <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> метод. В этом методе создается новый <xref:Microsoft.VisualStudio.Package.DocumentTask> объект. Перед возвратом этого объекта можно использовать <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> свойство <xref:Microsoft.VisualStudio.Package.DocumentTask> объекта для задания индекса изображения. Это будет выглядеть примерно так, как показано в следующем примере. Обратите внимание, что `TestIconImageIndex` является перечислением, в котором перечислены все значки, и оно относится только к этому примеру. У вас может быть другой способ идентификации значков в языковой службе.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>Список изображений по умолчанию для языковой службы
 Список изображений по умолчанию, поставляемый с базовыми классами языковой службы MPF, содержит несколько значков, связанных с более распространенными элементами языка. Основная часть этих значков упорядочена в наборах из шести вариантов, соответствующих концепциям доступа Public, internal, Friend, protected, private и shortcut. Например, можно иметь разные значки для метода в зависимости от того, является ли он открытым, защищенным или закрытым.

 Следующее перечисление указывает типичные имена для каждого набора значков и указывает связанный индекс. Например, на основе перечисления можно указать индекс изображения для защищенного метода в виде `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . При необходимости можно изменить имена в этом перечислении.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>См. также
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
