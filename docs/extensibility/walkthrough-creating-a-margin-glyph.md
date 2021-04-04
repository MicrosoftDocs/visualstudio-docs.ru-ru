---
title: Пошаговое руководство. Создание глифа поля | Документация Майкрософт
description: Узнайте, как настроить внешний вид полей редактора с помощью расширений пользовательского редактора с помощью этого пошагового руководства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec5eecef40220c2cf2d4e3f1ece8eb5eb763bdeb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217415"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Пошаговое руководство. Создание глифа поля
Внешний вид полей редактора можно настроить с помощью пользовательских расширений редактора. Это пошаговое руководство помещает пользовательский глиф на поле индикатора каждый раз, когда слово «TODO» появляется в комментарии к коду.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Создание проекта MEF

1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `TodoGlyphTest` .

2. Добавьте элемент проекта классификатора редактора. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="define-the-glyph"></a>Определение глифа
 Определите глиф, запустив <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> интерфейс.

### <a name="to-define-the-glyph"></a>Определение глифа

1. Добавьте файл класса с именем `TodoGlyphFactory`.

2. Добавьте следующий код с помощью объявлений.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. Добавьте класс с именем `TodoGlyphFactory` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. Добавьте закрытое поле, определяющее размеры глифа.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. Реализуйте `GenerateGlyph` , определив элемент пользовательского интерфейса глифа. `TodoTag` задается далее в этом пошаговом руководстве.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. Добавьте класс с именем `TodoGlyphFactoryProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Экспортируйте этот класс с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "тодоглиф", объекта <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> после встекстмаркер, a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> из "Code" и объекта <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> тодотаг.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> метод, создав экземпляр `TodoGlyphFactory` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>Определить тег TODO и средство создания тегов
 Определите связь между элементом пользовательского интерфейса, определенным в предыдущих шагах, и полем индикатора. Создайте тип тега и средство создания тегов и экспортируйте его с помощью поставщика тегов.

### <a name="to-define-a-todo-tag-and-tagger"></a>Определение тега TODO и создания его тегов

1. Добавьте в проект новый файл класса и присвойте ему имя `TodoTagger` .

2. Добавьте приведенные ниже импортированные данные.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. Добавьте класс с именем `TodoTag`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. Измените класс с именем `TodoTagger` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> тип `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. К `TodoTagger` классу Добавьте закрытые поля для <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> и для текста, который необходимо найти в области классификации.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. Добавьте конструктор, который задает классификатор.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод, находя все диапазоны классификации, имена которых содержат слово "Comment", а текст, содержащий искомый текст. При обнаружении искомого текста возвращает новый <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> тип `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. Объявите `TagsChanged` событие.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. Добавьте класс с именем `TodoTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> тодотаг.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. Импортируйте <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод, создав экземпляр `TodoTagger` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>Сборка и тестирование кода
 Чтобы протестировать этот код, создайте решение Тодоглифтест и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Создание и тестирование решения Тодоглифтест

1. Создайте решение.

2. Запустите проект, нажав клавишу **F5**. Запускается второй экземпляр Visual Studio.

3. Убедитесь, что поле индикатора отображается. (В меню **Сервис** выберите пункт **Параметры**. На странице **текстовый редактор** убедитесь, что **поле индикатор** выбрано.)

4. Откройте файл кода с комментариями. Добавьте слово «TODO» в один из разделов комментариев.

5. Светло-синий круг с темно-синей структурой отображается в поле индикатора слева от окна кода.
