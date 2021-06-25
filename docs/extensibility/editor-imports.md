---
title: Редактор импортирует | Документация Майкрософт
description: Узнайте, как импортировать службы редактора, фабрики и брокеры, которые предоставляют расширение с различными видами доступа к основному редактору.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f2fa91b41017512b3f38ad61b800b293e0abaa1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898348"
---
# <a name="editor-imports"></a>Импорт в редактор
Можно импортировать несколько служб редактора, фабрик и брокеров, которые предоставляют расширение с разными видами доступа к основному редактору. Например, можно импортировать, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> чтобы предоставить <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> для определенного типа содержимого. (Этот Навигатор позволяет выполнять различные виды поиска в текстовом буфере.)

 Чтобы использовать импорт редактора, импортируйте его как поле или свойство класса, который экспортирует компонент Managed Extensibility Framework компонента.

> [!NOTE]
> Дополнительные сведения о Managed Extensibility Framework см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Синтаксис импорта
 В следующем примере показано, как импортировать службу фабрики параметров редактора.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Если вы хотите импортировать службу как поле, а не свойство, следует задать для него значение `null` в объявлении, чтобы избежать предупреждений компилятора о неназначении переменной.

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Дополнительные примеры использования импортов см. в следующих пошаговых руководствах.

- [Пошаговое руководство. Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Пошаговое руководство. Настройка представления текста](../extensibility/walkthrough-customizing-the-text-view.md)

- [Пошаговое руководство. выделение текста](../extensibility/walkthrough-highlighting-text.md)

- [Пошаговое руководство. Отображение подсказок краткие сведения](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Пошаговое руководство. Отображение справки по сигнатурам](../extensibility/walkthrough-displaying-signature-help.md)

- [Пошаговое руководство: отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)

- [Пошаговое руководство. Отображение предложений лампочки](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Импорт поставщика услуг
 Чтобы <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> получить доступ к службам Visual Studio, можно также импортировать (в сборке Microsoft. VisualStudio. Shell. неизменяемый. 10.0).

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Дополнительные сведения см. [в разделе Пошаговое руководство. доступ к объекту DTE из расширения редактора](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) .

## <a name="services"></a>Службы
 Службы редактора обычно являются отдельными сущностями, которые предоставляют службу и являются общими для нескольких компонентов.

|Используя режим Import|Предоставляет|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Отношение между расширениями файлов и <xref:Microsoft.VisualStudio.Utilities.IContentType> объектами.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Коллекция объектов <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> объект.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Многие объекты адаптера редактора:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>Объект для заданного текстового представления.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>Различия между ними.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>Различия между ними.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> или <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Для набора <xref:Microsoft.VisualStudio.Text.ITextBuffer> объектов.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Для <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Поддерживает коллекцию <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> объектов.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> для текстового буфера.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Для текстового представления.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>Для указанной области.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>Для текстового представления.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Возвращает автоматический отступ через <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> объекты.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Управляет <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> для <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Создает текст в формате RTF из набора диапазонов снимка.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Объект <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> для форматирования строк текста в представлении.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>Объект для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Выполняет поиск моментального снимка текста.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Объект <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> для <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>Для текстового представления.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Стандартный набор глифов.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Отслеживает обработку клавиатуры.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Стандартные <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> объекты.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Поддерживает связь между текстовыми буферами и  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> объектами.|

## <a name="other-imports"></a>Другие операции импорта
 Фабрики поставщиков и брокеры — это обычно сущности, которые могут иметь несколько экземпляров в нескольких компонентах.

|Используя режим Import|Предоставляет|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Объект <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ) для заданного буфера.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Средство создания тегов текстовых меток ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>Для заданного объекта <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Объект <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Объект <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Объект <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>См. также
- [Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)
