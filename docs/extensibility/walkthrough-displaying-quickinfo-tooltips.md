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
ms.openlocfilehash: d374aa41d85b1d64b6623cb99f6183787a2afc53
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217259"
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

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet1":::

4. Объявите класс, реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> , и назовите его `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet2":::

5. Добавьте поля для поставщика источника краткие сведения, текстового буфера и набора имен методов и сигнатур методов. В этом примере имена и подписи методов инициализируются в `TestQuickInfoSource` конструкторе.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet3":::

6. Добавьте конструктор, который задает поставщик источника краткие сведения и текстовый буфер, и заполняет набор имен методов, а также сигнатуры и описания методов.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet4":::

7. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. В этом примере метод находит текущее слово или предыдущее слово, если курсор находится в конце строки или в текстовом буфере. Если слово является одним из имен методов, описание этого имени метода добавляется в содержимое краткие сведения.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet5":::

8. Также необходимо реализовать метод Dispose (), поскольку <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> реализуется <xref:System.IDisposable> :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet6":::

## <a name="implement-a-quickinfo-source-provider"></a>Реализация поставщика источника краткие сведения
 Поставщик источника краткие сведения служит главным образом для экспорта самого себя в качестве части компонента MEF и создания экземпляра источника краткие сведения. Поскольку это часть компонента MEF, она может импортировать другие компоненты MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Реализация поставщика источника краткие сведения

1. Объявите поставщик источника краткие сведения с именем `TestQuickInfoSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> , и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> элемента "ToolTip краткие сведения Source", объекта <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default" и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> объекта "Text".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet7":::

2. Импортируйте две службы редактора, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> и <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , как свойства `TestQuickInfoSourceProvider` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet8":::

3. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> , чтобы вернуть новый объект `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet9":::

## <a name="implement-a-quickinfo-controller"></a>Реализация контроллера краткие сведения
 Контроллеры краткие сведения определяют, когда отображается краткие сведения. В этом примере краткие сведения появляется, когда указатель наведен на слово, соответствующее одному из имен методов. Контроллер краткие сведения реализует обработчик событий наведения указателя мыши, который запускает сеанс краткие сведения.

### <a name="to-implement-a-quickinfo-controller"></a>Реализация контроллера краткие сведения

1. Объявите класс, реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> , и назовите его `TestQuickInfoController` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet10":::

2. Добавьте закрытые поля для текстового представления, текстовые буферы, представленные в текстовом представлении, сеанс краткие сведения и поставщик контроллера краткие сведения.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet11":::

3. Добавьте конструктор, который задает поля и добавляет обработчик событий наведения указателя мыши.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet12":::

4. Добавьте обработчик событий наведения указателя мыши, который запускает сеанс краткие сведения.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet13":::

5. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> метод таким образом, чтобы он удаляет обработчик событий наведения указателя мыши при отсоединении контроллера от текстового представления.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet14":::

6. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> метод и <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> метод как пустые методы в этом примере.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet15":::

## <a name="implementing-the-quickinfo-controller-provider"></a>Реализация поставщика контроллера краткие сведения
 Поставщик контроллера краткие сведения в основном служит для экспорта самого себя в составе компонента MEF и создания экземпляра контроллера краткие сведения. Поскольку это часть компонента MEF, она может импортировать другие компоненты MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Реализация поставщика контроллера краткие сведения

1. Объявите класс с именем `TestQuickInfoControllerProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> , и экспортируйте его с помощью элемента <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "краткие сведения Controller" и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> объекта "Text":

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet16":::

2. Импортируйте <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> как свойство.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet17":::

3. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> метод, создав экземпляр контроллера краткие сведения.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet18":::

## <a name="build-and-test-the-code"></a>Сборка и тестирование кода
 Чтобы протестировать этот код, создайте решение Куиккинфотест и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Создание и тестирование решения Куиккинфотест

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, содержащий слова "Добавить" и "Subtract".

4. Наведите указатель мыши на одно из вхождений "Добавить". Должна отобразиться подпись и описание `add` метода.

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Связывание типа содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
