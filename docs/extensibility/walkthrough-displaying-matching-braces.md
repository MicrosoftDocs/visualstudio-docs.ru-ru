---
title: Пошаговое руководство. Отображение парных скобок | Документация Майкрософт
description: Узнайте, как определять фигурные скобки в контексте языка, применяя Теги сопоставления фигурных скобок к типу содержимого text с помощью этого пошагового руководства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f89c6303dc8ca9e48fb212a3ae889251b34ece91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961733"
---
# <a name="walkthrough-display-matching-braces"></a>Пошаговое руководство. Отображение парных скобок
Реализуйте языковые функции, такие как Парные фигурные скобки, путем определения фигурных скобок, которые необходимо сопоставить, и добавления тега текстового маркера к парным фигурным скобкам, если курсор находится на одной из фигурных скобок. Можно определить фигурные скобки в контексте языка, определить собственное расширение имени файла и тип содержимого, применить теги только к этому типу или применить теги к существующему типу содержимого (например, "Text"). В следующем пошаговом руководстве показано, как применить теги сопоставления фигурных скобок к типу содержимого text.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект классификатора редактора. Назовите решение `BraceMatchingTest`.

2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="implement-a-brace-matching-tagger"></a>Реализация тегов для сопоставления фигурных скобок
 Чтобы получить маркер выделения фигурных скобок, похожий на тот, который используется в Visual Studio, можно реализовать средство создания тегов типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . В следующем коде показано, как определить средство создания тегов для пар скобок на любом уровне вложенности. В этом примере пары фигурных скобок [] и {} определены в конструкторе тегов, но в полной реализации языка соответствующие пары фигурных скобок будут определены в спецификации языка.

### <a name="to-implement-a-brace-matching-tagger"></a>Реализация тегов для сопоставления фигурных скобок

1. Добавьте файл класса и назовите его цветность.

2. Импортируйте следующие пространства имен.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Определите класс `BraceMatchingTagger` , наследующий от <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Добавление свойств для текстового представления, исходного буфера, текущей точки моментального снимка, а также набора пар фигурных скобок.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. В конструкторе тегов укажите свойства и подпишитесь на события изменения представления <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . В этом примере для демонстрационных целей в конструкторе также определяются совпадающие пары.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. В рамках <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> реализации объявите событие тагсчанжед.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Обработчики событий обновляют текущую позиции курсора `CurrentChar` Свойства и вызывают событие тагсчанжед.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод для сопоставления фигурных скобок, если текущий символ является открывающей фигурной скобкой или если предыдущий символ является закрывающей фигурной скобкой, как в Visual Studio. При обнаружении совпадения этот метод создает два тега: один для открывающей фигурной скобки, а другой — для закрывающей.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Следующие закрытые методы находят парную фигурную скобку на любом уровне вложенности. Первый метод находит символ закрытия, соответствующий открывающему символу:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Следующий вспомогательный метод находит открытый символ, соответствующий закрывающему символу:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Реализация поставщика тегов для сопоставления фигурных скобок
 Помимо реализации средства создания тегов, необходимо также реализовать и экспортировать поставщик тегов. В этом случае тип содержимого поставщика — Text. Таким образом, сопоставление фигурных скобок будет отображаться во всех типах текстовых файлов, но более полное применение применяет сопоставление фигурных скобок только к конкретному типу содержимого.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Реализация поставщика тегов для сопоставления фигурных скобок

1. Объявите поставщик тегов, наследующий от <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , назовите его брацематчингтагжерпровидер и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" и объекта <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метод для создания экземпляра брацематчингтагжер.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Сборка и тестирование кода
 Чтобы протестировать этот код, создайте решение Брацематчингтест и запустите его в экспериментальном экземпляре.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Создание и тестирование решения Брацематчингтест

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, содержащий Парные фигурные скобки.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. При размещении курсора перед открывающей фигурной скобкой следует выделить обе фигурные скобки и соответствующую закрывающую фигурную скобку. При размещении курсора сразу после закрывающей скобки должны быть выделены как фигурные скобки, так и парные открывающие скобки.

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Связывание типа содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
