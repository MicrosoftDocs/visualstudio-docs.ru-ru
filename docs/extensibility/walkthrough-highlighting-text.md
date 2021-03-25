---
title: Пошаговое руководство. выделение текста | Документация Майкрософт
description: Узнайте, как выделить каждое вхождение текущего слова в текстовом файле, добавив визуальные эффекты в редактор в этом пошаговом руководстве.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a500d63eb497ce6d2b23860cd3793cbc2632b819
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078465"
---
# <a name="walkthrough-highlight-text"></a>Пошаговое руководство. выделение текста
Можно добавить различные визуальные эффекты в редактор, создав компоненты компонентов Managed Extensibility Framework (MEF). В этом пошаговом руководстве показано, как выделить каждое вхождение текущего слова в текстовом файле. Если слово встречается в текстовом файле более одного раза и курсор находится в одном месте, выделяется каждое вхождение.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Создание проекта MEF

1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `HighlightWordTest` .

2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="define-a-textmarkertag"></a>Определение Текстмаркертаг
 Первым шагом при выделении текста является подкласс <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> и определение его внешнего вида.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Определение Текстмаркертаг и Маркерформатдефинитион

1. Добавьте файл класса и назовите его **хигхлигхтвордтаг**.

2. Добавьте следующие ссылки.

    1. Microsoft. VisualStudio. Кореутилити

    2. Microsoft. VisualStudio. Text. Data

    3. Microsoft. VisualStudio. Text. Logic

    4. Microsoft. VisualStudio. Text. UI

    5. Microsoft. VisualStudio. Text. UI. WPF

    6. System.ComponentModel.Composition

    7. Presentation. Core

    8. Presentation. Framework

3. Импортируйте следующие пространства имен.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. Создайте класс, наследующий от <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> и назовите его `HighlightWordTag` .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Создайте второй класс, наследующий от <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , и назовите его `HighlightWordFormatDefinition` . Чтобы использовать это определение формата для тега, необходимо экспортировать его со следующими атрибутами:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Теги используются для ссылки на этот формат

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: это приводит к тому, что формат отображается в пользовательском интерфейсе

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. В конструкторе для Хигхлигхтвордформатдефинитион определите его отображаемое имя и внешний вид. Свойство Background определяет цвет заливки, а свойство «передний план» определяет цвет границы.

    ```csharp
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. В конструкторе для Хигхлигхтвордтаг передайте имя созданного определения формата.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Реализация Итагжер
 Следующим шагом является реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> интерфейса. Этот интерфейс Присваивает заданному текстовому буферу теги, которые обеспечивают выделение текста и другие визуальные эффекты.

### <a name="to-implement-a-tagger"></a>Реализация средства создания тегов

1. Создайте класс, реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> тип `HighlightWordTag` , и назовите его `HighlightWordTagger` .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Добавьте следующие закрытые поля и свойства в класс:

    - Объект <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , который соответствует текущему текстовому представлению.

    - Объект <xref:Microsoft.VisualStudio.Text.ITextBuffer> , который соответствует текстовому буферу, который зависит от текстового представления.

    - Объект <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> , который используется для поиска текста.

    - Объект <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> , который содержит методы для навигации внутри текстовых диапазонов.

    - Объект <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> , содержащий набор слов для выделения.

    - Объект <xref:Microsoft.VisualStudio.Text.SnapshotSpan> , который соответствует текущему слову.

    - Объект <xref:Microsoft.VisualStudio.Text.SnapshotPoint> , который соответствует текущей позиции курсора.

    - Объект блокировки.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Добавьте конструктор, который инициализирует перечисленные выше свойства и добавляет <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> обработчики событий и.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. Обработчики событий вызывают `UpdateAtCaretPosition` метод.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. Также необходимо добавить `TagsChanged` событие, вызываемое методом Update.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. `UpdateAtCaretPosition()`Метод находит каждое слово в текстовом буфере, идентичное слову, где расположен курсор, и конструирует список <xref:Microsoft.VisualStudio.Text.SnapshotSpan> объектов, соответствующих вхождениям слова. Затем вызывается метод `SynchronousUpdate` , который вызывает `TagsChanged` событие.

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. `SynchronousUpdate`Выполняет синхронное обновление `WordSpans` `CurrentWord` свойств и и вызывает `TagsChanged` событие.

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. Необходимо реализовать <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод. Этот метод принимает коллекцию <xref:Microsoft.VisualStudio.Text.SnapshotSpan> объектов и возвращает перечисление диапазонов тегов.

     В C# Реализуйте этот метод в качестве итератора yield, который включает отложенное вычисление (т. е. вычисление набора только при обращении к отдельным элементам) тегов. В Visual Basic добавьте теги в список и возвратите список.

     Здесь метод возвращает объект с синим <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> фоном, который предоставляет синий фон.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Создание поставщика тегов
 Чтобы создать средство создания тегов, необходимо реализовать <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Этот класс является частью компонента MEF, поэтому необходимо задать правильные атрибуты, чтобы это расширение было распознано.

> [!NOTE]
> Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Создание поставщика тегов

1. Создайте класс с именем `HighlightWordTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> объекта <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> Чтобы создать экземпляр создания тегов, необходимо импортировать две службы редактора, и.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метод для возврата экземпляра `HighlightWordTagger` .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Сборка и тестирование кода
 Чтобы протестировать этот код, создайте решение Хигхлигхтвордтест и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Создание и тестирование решения Хигхлигхтвордтест

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, в котором слова повторяются, например "Hello Hello Hello".

4. Поместите курсор в одно из вхождений "Hello". Каждое вхождение должно быть выделено синим цветом.

## <a name="see-also"></a>См. также
- [Пошаговое руководство. Связывание типа содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
