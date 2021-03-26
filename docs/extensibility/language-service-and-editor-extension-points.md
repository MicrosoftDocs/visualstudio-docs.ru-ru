---
title: Точки расширения языковой службы и редактора | Документация Майкрософт
description: Узнайте о точках расширения в редакторе кода Visual Studio, которые можно расширить, включая большинство функций языковой службы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a8d71e6c7cd7569c9e73134345584a8237337bc7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073304"
---
# <a name="language-service-and-editor-extension-points"></a>Точки расширения языковой службы и редактора
Редактор предоставляет точки расширения, которые можно расширять как компоненты Managed Extensibility Framework (MEF), включая большинство функций языковой службы. Ниже приведены основные категории точек расширения.

- Типы содержимого

- Типы классификации и форматы классификации

- Поля и полосы прокрутки

- Теги

- Элементов оформления

- Обработчики мыши

- Удалить обработчики

- Варианты

- IntelliSense

## <a name="extend-content-types"></a>Расширение типов содержимого
 Типы содержимого — это определения типов текста, обрабатываемых редактором, например "Text", "Code" или "CSharp". Новый тип содержимого определяется путем объявления переменной типа <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> и присвоения новому типу уникального имени. Чтобы зарегистрировать тип содержимого в редакторе, экспортируйте его вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> имя типа содержимого.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> имя типа содержимого, производным от которого является этот тип содержимого. Тип содержимого может наследовать от нескольких других типов содержимого.

  Поскольку <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> класс запечатан, его можно экспортировать без параметра типа.

  В следующем примере показаны атрибуты экспорта для определения типа содержимого.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Типы содержимого могут быть основаны на уже существующих типах содержимого (ноль или более). Это встроенные типы:

- Any: основной тип содержимого. Родительский объект для всех других типов содержимого.

- Text: базовый тип для содержимого, не относящегося к проекции. Наследуется от any.

- Обычный текст: для текста, отличного от кода. Наследуется от "Text".

- Код: для кода всех типов. Наследуется от "Text".

- Инерт: исключает текст из любого вида обработки. К тексту этого типа содержимого никогда не применялись никакие расширения.

- Проекция: для содержимого буферов проекции. Наследуется от any.

- IntelliSense: для содержимого IntelliSense. Наследуется от "Text".

- Сигхелп: Справка по сигнатурам. Наследует от IntelliSense.

- Сигхелп-doc: Справочная документация по сигнатурам. Наследует от IntelliSense.

  Это некоторые типы содержимого, определяемые Visual Studio, и некоторые языки, размещенные в Visual Studio:

- Basic

- C/C++

- консолеаутпут

- CSharp

- CSS

- ENC

- финдресултс

- F#

- HTML

- Язык JScript

- XAML

- XML

  Чтобы обнаружить список доступных типов содержимого, импортируйте объект <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> , который поддерживает коллекцию типов содержимого для редактора. Следующий код импортирует эту службу как свойство.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Чтобы связать тип содержимого с расширением имени файла, используйте <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> В Visual Studio расширения имен файлов регистрируются с помощью <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> пакета языковой службы. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>Связывает тип содержимого MEF с расширением имени файла, зарегистрированным таким образом.

 Чтобы экспортировать расширение имени файла в определение типа содержимого, необходимо включить следующие атрибуты:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Указывает расширение имени файла.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: указывает тип содержимого.

  Поскольку <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> класс запечатан, его можно экспортировать без параметра типа.

  В следующем примере показано, как экспортировать атрибуты для расширения имени файла в определение типа содержимого.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>Управляет связями между расширениями имен файлов и типами содержимого.

## <a name="extend-classification-types-and-classification-formats"></a>Расширение типов классификации и форматов классификации
 Типы классификации можно использовать для определения типов текста, для которых требуется обеспечить разную обработку (например, цвет «ключевое слово» синего цвета и зеленый текст «комментарий»). Определите новый тип классификации, объявляя переменную типа <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> и присвоив ей уникальное имя.

 Чтобы зарегистрировать тип классификации в редакторе, экспортируйте его вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя типа классификации.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: имя типа классификации, от которого наследует данный тип классификации. Все типы классификации наследуются от "Text", и тип классификации может наследовать от нескольких других типов классификации.

  Поскольку <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> класс запечатан, его можно экспортировать без параметра типа.

  В следующем примере показаны атрибуты экспорта для определения типа классификации.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>Предоставляет доступ к стандартным классификациям. К встроенным типам классификации относятся:

- "text"

- "естественный язык" (является производным от "Text")

- "формальный язык" (является производным от "Text")

- "String" (является производным от "Literal")

- "символ" (является производным от "Literal")

- "числовое" (является производным от "Literal")

  Набор различных типов ошибок наследуется от <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Они включают следующие типы ошибок:

- "Синтаксическая ошибка"

- "Ошибка компилятора"

- "другая ошибка"

- !

  Чтобы обнаружить список доступных типов классификации, импортируйте объект <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> , который поддерживает коллекцию типов классификации для редактора. Следующий код импортирует эту службу как свойство.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Можно определить определение формата классификации для нового типа классификации. Создайте производный класс от <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> и экспортируйте его с типом <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя формата.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: отображаемое имя формата.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: указывает, отображается ли формат на странице " **шрифты и цвета** " диалогового окна " **Параметры** ".

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: приоритет формата. Допустимые значения: из <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: имя типа классификации, с которым сопоставлен этот формат.

  В следующем примере показаны атрибуты экспорта в определении формата классификации.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Чтобы обнаружить список доступных форматов, импортируйте объект <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> , который поддерживает коллекцию форматов для редактора. Следующий код импортирует эту службу как свойство.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Расширение полей и полос прокрутки
 Поля и полосы прокрутки — это основные элементы представления редактора в дополнение к самому представлению текста. Помимо стандартных полей, отображаемых вокруг текстового представления, можно указать любое количество полей.

 Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> интерфейс для определения поля. Также необходимо реализовать <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> интерфейс для создания поля.

 Чтобы зарегистрировать поставщик полей в редакторе, необходимо экспортировать поставщик вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя поля.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в котором поле отображается относительно других полей.

   Это встроенные поля:

  - "Горизонтальная полоса прокрутки WPF"

  - "Вертикальная полоса прокрутки WPF"

  - "Поле номера строки WPF"

    Горизонтальные поля, для которых атрибут order имеет `After="Wpf Horizontal Scrollbar"` значение, отображаются под встроенным полем, а горизонтальные поля с атрибутом Order элемента `Before ="Wpf Horizontal Scrollbar"` отображаются над встроенным полем. Правая вертикальные поля, для которых атрибут order имеет значение, `After="Wpf Vertical Scrollbar"` отображаются справа от полосы прокрутки. Левые вертикальные поля, для которых атрибут order имеет значение, `After="Wpf Line Number Margin"` отображаются слева от поля номера строки (если оно отображается).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: тип поля (слева, справа, сверху или снизу).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, "Text" или "Code"), для которого действует поле.

  В следующем примере показаны атрибуты экспорта в поставщике полей для поля, расположенного справа от поля номера строки.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Расширение тегов
 Теги — это способ связывания данных с различными видами текста. Во многих случаях связанные данные отображаются в виде визуальных эффектов, но не все теги имеют визуальную презентацию. Можно определить собственный тип тега, реализовав <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Кроме того, необходимо реализовать, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> чтобы предоставить теги для заданного набора текстовых диапазонов, а также <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> для предоставления средства создания тегов. Поставщик тегов необходимо экспортировать вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, "Text" или "Code"), для которого тег является допустимым.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: тип тега.

  В следующем примере показаны атрибуты экспорта для поставщика тегов.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> следующие типы тегов являются встроенными:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: связан с <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: связан с типами ошибок.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: связан с элементом оформления.

  > [!NOTE]
  > Пример см. в описании <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> определения хигхлигхтвордтаг в разделе [Пошаговое руководство. выделение текста](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: связан с регионами, которые можно развернуть или свернуть в структурировании.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: определяет пространство, занимаемое элементом оформления в текстовом представлении. Дополнительные сведения о оформлении, посвященном согласованию пространства, см. в следующем разделе.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: предоставляет автоматические промежутки и размеры для оформления.

  Чтобы найти и использовать теги для буферов и представлений, импортируйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> или <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> , чтобы предоставить <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> запрошенный тип. Следующий код импортирует эту службу как свойство.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Теги и Маркерформатдефинитионс
 Можно расширить класс, <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> чтобы определить внешний вид тега. Необходимо экспортировать класс (как <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя, используемое для ссылки на этот формат

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: это приводит к тому, что формат отображается в пользовательском интерфейсе

  В конструкторе определяется отображаемое имя и внешний вид тега. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Определяет цвет заливки и <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> определяет цвет границы. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>— Это Локализуемое имя определения формата.

  Ниже приведен пример определения формата.

```
[Export(typeof(EditorFormatDefinition))]
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
[UserVisible(true)]
internal class HighlightWordFormatDefinition : MarkerFormatDefinition
{
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
}

```

 Чтобы применить это определение формата к тегу, сослаться на имя, заданное в атрибуте Name класса (не отображаемое имя).

> [!NOTE]
> Пример см <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> . в разделе класс хигхлигхтвордформатдефинитион в [разделе Пошаговое руководство. выделение текста](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Расширить декоративные элементы
 Декоративные элементы определяют визуальные эффекты, которые могут быть добавлены к тексту, отображаемому в текстовом представлении, или к самому текстовому представлению. Можно определить собственное оформление как любой тип <xref:System.Windows.UIElement> .

 В классе оформления необходимо объявить <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Чтобы зарегистрировать слой оформления, экспортируйте его вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя оформления.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: упорядоченность оформления по отношению к другим слоям оформления. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> определяет четыре слоя по умолчанию: выделение, структуризацию, курсор и текст.

  В следующем примере показаны атрибуты экспорта для определения слоя оформления.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Необходимо создать второй класс, который реализует <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> и обрабатывает его <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> событие, создавая экземпляр оформления. Этот класс необходимо экспортировать вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, "Text" или "Code"), для которого допустимо автооформление.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: вид текстового представления, для которого является допустимым данное оформление. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например, в <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> основном используется для текстовых представлений файлов. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> используется для текстовых представлений, которые пользователь может изменять или перемещать с помощью мыши и клавиатуры. Примерами <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представлений являются текстовое представление редактора и окно **вывода** .

  В следующем примере показаны атрибуты экспорта для поставщика оформлений.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Элемент оформления, ориентированный на пробелы, занимает место на том же уровне, что и текст. Чтобы создать этот тип оформления, необходимо определить класс тегов, который наследует от <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , который определяет объем пространства, занимаемого декоративным элементом.

 Как и во всех оформлениях, необходимо экспортировать определение слоя оформления.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Чтобы создать экземпляр элемента оформления уровня пространства, необходимо создать класс, реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , в дополнение к классу, реализующему <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (как и другие виды оформлений).

 Для регистрации поставщика тегов необходимо экспортировать его вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, "Text" или "Code"), для которого допустимо ваше Оформление.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: вид текстового представления, для которого является допустимым этот тег или декоративный элемент. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например, в <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> основном используется для текстовых представлений файлов. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> используется для текстовых представлений, которые пользователь может изменять или перемещать с помощью мыши и клавиатуры. Примерами <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представлений являются текстовое представление редактора и окно **вывода** .

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: тип определенного тега или оформленного обрамления. Необходимо добавить секунды <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> для <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  В следующем примере показаны атрибуты экспорта в поставщике тегов для тега оформления, используемого в качестве пространства.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Расширение обработчиков мыши
 Можно добавить специальную обработку для ввода с помощью мыши. Создайте класс, который наследует от <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> и переопределяет события мыши для входных данных, которые требуется обойти. Также необходимо реализовать <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> во втором классе и экспортировать его вместе с параметром <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , который указывает тип содержимого (например, "Text" или "Code"), для которого обработчик мыши является допустимым.

 В следующем примере показаны атрибуты экспорта для поставщика обработчика мыши.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Расширение обработчиков Drop
 Можно настроить поведение обработчиков Drop для определенных типов текста, создав класс, реализующий, <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> и второй класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> для создания обработчика перетаскивания. Необходимо экспортировать обработчик перетаскивания вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: формат текста, для которого этот обработчик перетаскивания является допустимым. Следующие форматы обрабатываются в порядке приоритета от самого высокого до самого низкого:

  1. Любой пользовательский формат

  2. филедроп

  3. енханцедметафиле

  4. вавеаудио

  5. Metallica

  6. DIF

  7. Locale

  8. Палитра

  9. пендата

  10. Упорядочиваемый уровень изоляции

  11. SymbolicLink

  12. Кода

  13. ксамлпаккаже

  14. Tiff

  15. Bitmap

  16. Рисунок

  17. метафилепиктуре

  18. CSV

  19. System.String

  20. Формат HTML

  21. уникодетекст

  22. оемтекст

  23. Текст

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя обработчика перетаскивания.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: упорядочение обработчика перетаскивания до или после обработчика перетаскивания по умолчанию. Обработчик удаления по умолчанию для Visual Studio называется "Дефаултфиледрофандлер".

  В следующем примере показаны атрибуты экспорта для поставщика обработчика перетаскивания.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Расширение параметров редактора
 Можно определить допустимые параметры только в определенной области, например в текстовом представлении. Редактор предоставляет этот набор предопределенных параметров: параметры редактора, параметры представления и параметры представления Windows Presentation Foundation (WPF). Эти параметры можно найти в <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> и <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Чтобы добавить новый параметр, сделайте класс производным от одного из следующих классов определения параметров:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  В следующем примере показано, как экспортировать определение параметра, имеющее логическое значение.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Расширение IntelliSense
 Технология IntelliSense является общим термином для группы функций, предоставляющих сведения о структурированном тексте и завершении операторов для нее. К таким функциям относятся завершение операторов, Справка по сигнатурам, краткие сведения и лампочки. Завершение операторов помогает пользователям правильно ввести ключевое слово языка или имя члена. Справка по сигнатуре отображает сигнатуру или подписи для метода, который только что ввел пользователь. Краткие сведения отображает полную сигнатуру для имени типа или члена при наведении на нее курсора мыши. Лампочка предоставляет дополнительные действия для определенных идентификаторов в определенных контекстах, например переименование всех вхождений переменной после того, как одно вхождение было переименовано.

 Структура функции IntelliSense во всех случаях очень одинакова:

- Для общего процесса отвечает *брокер* IntelliSense.

- *Сеанс* IntelliSense представляет последовательность событий между триггерами выступающего и фиксацией или отменой выбора. Сеанс обычно запускается некоторым жестом пользователя.

- *Контроллер* IntelliSense отвечает за принятие решения о начале и завершении сеанса. Также принимает решение о том, следует ли зафиксировать информацию и время отмены сеанса.

- *Источник* IntelliSense предоставляет содержимое и определяет лучшее соответствие.

- Модуль отображения *IntelliSense отвечает* за отображение содержимого.

  В большинстве случаев рекомендуется предоставлять по крайней мере источник и контроллер. Кроме того, можно предоставить выступающий, если требуется настроить отображение.

### <a name="implement-an-intellisense-source"></a>Реализация источника IntelliSense
 Для настройки источника необходимо реализовать один (или несколько) следующих исходных интерфейсов:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> является нерекомендуемым в пользу <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 Кроме того, необходимо реализовать поставщик такого же типа:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> является нерекомендуемым в пользу <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 Необходимо экспортировать поставщик вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя источника.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, "Text" или "Code"), к которому применяется источник.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в котором должен отображаться источник (по отношению к другим источникам).

- В следующем примере показаны атрибуты экспорта для поставщика источника завершения.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Дополнительные сведения о реализации источников IntelliSense см. в следующих пошаговых руководствах.

- [Пошаговое руководство. Отображение подсказок краткие сведения](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Пошаговое руководство. Отображение справки по сигнатурам](../extensibility/walkthrough-displaying-signature-help.md)

- [Пошаговое руководство: отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Реализация контроллера IntelliSense
 Чтобы настроить контроллер, необходимо реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> интерфейс. Кроме того, необходимо реализовать поставщик контроллера вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>— имя контроллера.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, "Text" или "Code"), к которому применяется контроллер.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в котором должен отображаться контроллер (по отношению к другим контроллерам).

  В следующем примере показаны атрибуты экспорта в поставщике контроллера завершения.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Дополнительные сведения об использовании контроллеров IntelliSense см. в следующих пошаговых руководствах.

- [Пошаговое руководство. Отображение подсказок краткие сведения](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
