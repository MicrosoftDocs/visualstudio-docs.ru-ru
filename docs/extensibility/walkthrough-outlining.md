---
title: Пошаговое руководство. структурирование | Документация Майкрософт
description: Узнайте, как определять и отображать области структуры в контексте языковой службы или для собственного расширения имени файла и типа содержимого.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7bf4c0cc8757ea4f034da2ac17d6c76971f86305
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217233"
---
# <a name="walkthrough-outlining"></a>Пошаговое руководство. Структурирование
Настройте языковые функции, такие как структурирование, определив типы текстовых областей, которые необходимо развернуть или свернуть. Можно определить регионы в контексте языковой службы или определить собственное расширение имени файла и тип содержимого и применить определение региона только к этому типу или применить определения областей к существующему типу содержимого (например, "Text"). В этом пошаговом руководстве показано, как определить и отобразить области структуры.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект VSIX. Назовите решение `OutlineRegionTest`.

2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="implement-an-outlining-tagger"></a>Реализация средства создания тегов структуры
 Регионы структурирования помечены видом тега ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Этот тег обеспечивает стандартное поведение структурирования. Контурный регион можно развернуть или свернуть. Контурный регион помечается знаком «плюс» ( **+** ), если он свернут, или знаком «минус» ( **-** ), если он развернут, а развернутая область демаркатед вертикальной линией.

 В следующих шагах показано, как определить средство создания тегов, которое создает области структуры для всех регионов, разделенных квадратными скобками (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Реализация средства создания тегов структуры

1. Добавьте файл класса с именем `OutliningTagger`.

2. Импортируйте следующие пространства имен.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet1":::

3. Создайте класс с именем `OutliningTagger` и реализуйте его <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet2":::

4. Добавьте некоторые поля для трассировки текстового буфера и моментального снимка, а также для накопления наборов строк, которые должны быть помечены как регионы структурирования. Этот код включает список объектов Region (которые будут определены позже), представляющих регионы структуры.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet3":::

5. Добавьте конструктор средства создания тегов, который инициализирует поля, анализирует буфер и добавляет обработчик событий в <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событие.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet4":::

6. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод, который создает экземпляры диапазона тегов. В этом примере предполагается, что диапазоны в <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> переданном методе являются непрерывными, хотя это не всегда может быть так. Этот метод создает новый диапазон тегов для каждой из областей структуры.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet5":::

7. Объявите `TagsChanged` обработчик событий.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet6":::

8. Добавьте `BufferChanged` обработчик событий, реагирующий на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события путем синтаксического анализа текстового буфера.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet7":::

9. Добавьте метод, который анализирует буфер. Пример, приведенный здесь, предназначен только для иллюстрации. Он синхронно анализирует буфер во вложенные области структуры.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet8":::

10. Следующий вспомогательный метод получает целое число, представляющее уровень структуры, таким, что 1 — это левая пара фигурных скобок.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet9":::

11. Следующий вспомогательный метод преобразует область (определенную далее в этой статье) в диапазон SnapshotSpan.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet10":::

12. Следующий код предназначен только для иллюстрации. Он определяет класс Партиалрегион, который содержит номер строки и смещение начала области структуры, а также ссылку на родительскую область (если она есть). Этот код позволяет средству синтаксического анализа настраивать вложенные области структуры. Производный класс Region содержит ссылку на номер строки конца области структуры.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet11":::

## <a name="implement-a-tagger-provider"></a>Реализация поставщика тегов
 Экспортируйте поставщик тегов для создания тегов. Поставщик тегов создает `OutliningTagger` для буфера типа содержимого text, или Else возвращает, `OutliningTagger` если буфер уже имеет такой тип.

### <a name="to-implement-a-tagger-provider"></a>Реализация поставщика тегов

1. Создайте класс с именем `OutliningTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , и экспортируйте его с атрибутами ContentType и тагтипе.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet12":::

2. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод, добавив `OutliningTagger` в свойства буфера.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet13":::

## <a name="build-and-test-the-code"></a>Сборка и тестирование кода
 Чтобы протестировать этот код, создайте решение Аутлинерегионтест и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Создание и тестирование решения Аутлинерегионтест

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создание текстового файла. Введите текст, содержащий как открывающие квадратные скобки, так и закрывающие квадратные скобки.

    ```
    [
       Hello
    ]
    ```

4. Должна существовать область структуры, включающая обе скобки. Чтобы свернуть область структуры, щелкните знак "минус" слева от открывающей скобки. Если область свернута, то символ многоточия (..*.*) должен отображаться слева от свернутой области, а всплывающее окно, содержащее текст, нарисованный при **наведении** указателя на многоточие, должно отобразиться.

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Связывание типа содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
