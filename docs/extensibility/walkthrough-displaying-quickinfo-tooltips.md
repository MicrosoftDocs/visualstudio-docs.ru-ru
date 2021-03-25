---
title: Пошаговое руководство. Отображение подсказок краткие сведения | Документация Майкрософт
description: Сведения о том, как отобразить краткие сведения для текстового содержимого с помощью этого пошагового руководства. Краткие сведения отображает сигнатуры и описания методов для имени метода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: acda716c72d10f35bf8c89978956f62a6d3754dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078608"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Пошаговое руководство. Отображение подсказок краткие сведения
Краткие сведения — это функция IntelliSense, которая отображает сигнатуры и описания методов, когда пользователь наводит указатель мыши на имя метода. Вы можете реализовать такие функции на основе языка, как краткие сведения, определив идентификаторы, для которых необходимо предоставить описания краткие сведения, а затем создав подсказку, в которой будет отображаться содержимое. Можно определить краткие сведения в контексте языковой службы или определить собственное расширение имени файла и тип содержимого и отобразить краткие сведения только для этого типа. Кроме того, можно отобразить краткие сведения для существующего типа содержимого (например, "Text"). В этом пошаговом руководстве показано, как отобразить краткие сведения для типа содержимого text.

 Пример краткие сведения в этом пошаговом руководстве отображает подсказки, когда пользователь наводит указатель мыши на имя метода. Эта схема требует реализации следующих четырех интерфейсов:

- исходный интерфейс

- исходный интерфейс поставщика

- интерфейс контроллера

- интерфейс поставщика контроллера

  Поставщики источников и контроллеров Managed Extensibility Framework (MEF). они отвечают за экспорт классов источников и контроллеров, а также импорт служб и брокеров <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , например,, который создает текстовый буфер подсказки, и <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> , который запускает сеанс краткие сведения.

  В этом примере источник краткие сведения использует жестко закодированный список имен и описаний методов, но в полной реализации языковая служба и документация по языку отвечают за предоставление этого содержимого.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015 вам не нужно устанавливать пакет SDK для Visual Studio из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Создание проекта MEF

### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `QuickInfoTest` .

2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="implement-the-quickinfo-source"></a>Реализация источника краткие сведения
 Источник краткие сведения отвечает за сбор набора идентификаторов и их описаний, а также добавление содержимого в текстовый буфер подсказки при обнаружении одного из идентификаторов. В этом примере идентификаторы и их описания просто добавляются в конструктор исходного кода.

#### <a name="to-implement-the-quickinfo-source"></a>Реализация источника краткие сведения

1. Добавьте файл класса с именем `TestQuickInfoSource`.

2. Добавьте ссылку на *Microsoft. VisualStudio. Language. IntelliSense*.

3. Добавьте приведенные ниже импортированные данные.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Объявите класс, реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> , и назовите его `TestQuickInfoSource` .

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Добавьте поля для поставщика источника краткие сведения, текстового буфера и набора имен методов и сигнатур методов. В этом примере имена и подписи методов инициализируются в `TestQuickInfoSource` конструкторе.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Добавьте конструктор, который задает поставщик источника краткие сведения и текстовый буфер, и заполняет набор имен методов, а также сигнатуры и описания методов.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. В этом примере метод находит текущее слово или предыдущее слово, если курсор находится в конце строки или в текстовом буфере. Если слово является одним из имен методов, описание этого имени метода добавляется в содержимое краткие сведения.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Также необходимо реализовать метод Dispose (), поскольку <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> реализуется <xref:System.IDisposable> :

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Реализация поставщика источника краткие сведения
 Поставщик источника краткие сведения служит главным образом для экспорта самого себя в качестве части компонента MEF и создания экземпляра источника краткие сведения. Поскольку это часть компонента MEF, она может импортировать другие компоненты MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Реализация поставщика источника краткие сведения

1. Объявите поставщик источника краткие сведения с именем `TestQuickInfoSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> , и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> элемента "ToolTip краткие сведения Source", объекта <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default" и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> объекта "Text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Импортируйте две службы редактора, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> и <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , как свойства `TestQuickInfoSourceProvider` .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> , чтобы вернуть новый объект `TestQuickInfoSource` .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Реализация контроллера краткие сведения
 Контроллеры краткие сведения определяют, когда отображается краткие сведения. В этом примере краткие сведения появляется, когда указатель наведен на слово, соответствующее одному из имен методов. Контроллер краткие сведения реализует обработчик событий наведения указателя мыши, который запускает сеанс краткие сведения.

### <a name="to-implement-a-quickinfo-controller"></a>Реализация контроллера краткие сведения

1. Объявите класс, реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> , и назовите его `TestQuickInfoController` .

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Добавьте закрытые поля для текстового представления, текстовые буферы, представленные в текстовом представлении, сеанс краткие сведения и поставщик контроллера краткие сведения.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Добавьте конструктор, который задает поля и добавляет обработчик событий наведения указателя мыши.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Добавьте обработчик событий наведения указателя мыши, который запускает сеанс краткие сведения.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> метод таким образом, чтобы он удаляет обработчик событий наведения указателя мыши при отсоединении контроллера от текстового представления.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> метод и <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> метод как пустые методы в этом примере.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Реализация поставщика контроллера краткие сведения
 Поставщик контроллера краткие сведения в основном служит для экспорта самого себя в составе компонента MEF и создания экземпляра контроллера краткие сведения. Поскольку это часть компонента MEF, она может импортировать другие компоненты MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Реализация поставщика контроллера краткие сведения

1. Объявите класс с именем `TestQuickInfoControllerProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> , и экспортируйте его с помощью элемента <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "краткие сведения Controller" и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> объекта "Text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Импортируйте <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> как свойство.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> метод, создав экземпляр контроллера краткие сведения.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Сборка и тестирование кода
 Чтобы протестировать этот код, создайте решение Куиккинфотест и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Создание и тестирование решения Куиккинфотест

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, содержащий слова "Добавить" и "Subtract".

4. Наведите указатель мыши на одно из вхождений "Добавить". Должна отобразиться подпись и описание `add` метода.

## <a name="see-also"></a>См. также
- [Пошаговое руководство. Связывание типа содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
