---
title: Пошаговое руководство. Отображение справки по сигнатурам | Документация Майкрософт
description: Сведения о том, как отобразить справку по сигнатурам для типа текстового содержимого с помощью этого пошагового руководства. Справка по сигнатуре отображает сигнатуру метода в подсказке.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6ffa2a0e646c11cb56d08ef91e3d7a4b9af7572
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217506"
---
# <a name="walkthrough-display-signature-help"></a>Пошаговое руководство. Отображение справки по сигнатурам
Справка по сигнатурам (также называемая *сведениями о параметрах*) отображает сигнатуру метода в подсказке, когда пользователь вводит начальный символ списка параметров (обычно это открывающая круглая скобка). При вводе разделителя параметров и параметров (обычно запятая) подсказка обновляется для отображения следующего параметра полужирным шрифтом. Справку по сигнатурам можно определить следующими способами: в контексте языковой службы определите собственное расширение имени файла и тип содержимого, а также справку по сигнатурам для этого типа или отобразите справку по сигнатуре для существующего типа содержимого (например, "Text"). В этом пошаговом руководстве показано, как отобразить справку по сигнатуре для типа содержимого text.

 Справка по сигнатуре обычно запускается путем ввода определенного символа, например "(" (открывающая скобка), и закрытия путем ввода другого символа, например ")" (закрывающей скобки). Функции IntelliSense, активируемые при вводе символа, могут быть реализованы с помощью обработчика команд для нажатий клавиш ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс) и поставщика обработчика, реализующего <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейс. Для создания источника справки сигнатур, который является списком подписей, участвующих в справке по сигнатурам, реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> интерфейс и поставщик источника, который выполняет <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> интерфейс. Поставщики — это компоненты компонентов Managed Extensibility Framework (MEF), которые отвечают за экспорт классов источников и контроллеров, а также импорт служб и брокеров, например <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ,, который позволяет перемещаться по текстовому буферу и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , который активирует сеанс справки сигнатуры.

 В этом пошаговом руководстве показано, как настроить справку по сигнатуре для жестко запрограммированного набора идентификаторов. В полной реализации язык отвечает за предоставление этого содержимого.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Создание проекта MEF

#### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `SignatureHelpTest` .

2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

4. Добавьте в проект следующие ссылки и убедитесь, что для свойства **CopyLocal** задано значение `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell.,

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Реализация подписей и параметров в справке по сигнатурам
 Источник справки по сигнатуре основан на сигнатурах, реализующих <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , каждый из которых содержит параметры, реализующие <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . В полной реализации эта информация будет получена из документации по языку, но в этом примере сигнатуры жестко запрограммированы.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Реализация сигнатур и параметров в справке по сигнатурам

1. Добавьте файл класса с именем `SignatureHelpSource`.

2. Добавьте приведенные ниже импортированные данные.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet1":::

3. Добавьте класс с именем `TestParameter` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet2":::

4. Добавьте конструктор, который задает все свойства.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet3":::

5. Добавьте свойства <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet4":::

6. Добавьте класс с именем `TestSignature` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet5":::

7. Добавьте некоторые закрытые поля.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet6":::

8. Добавьте конструктор, который задает поля и подписывается на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событие.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet7":::

9. Объявите `CurrentParameterChanged` событие. Это событие возникает при заполнении пользователем одного из параметров в сигнатуре.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet8":::

10. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> свойство таким образом, чтобы оно вызывало `CurrentParameterChanged` событие при изменении значения свойства.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet9":::

11. Добавьте метод, который вызывает `CurrentParameterChanged` событие.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet10":::

12. Добавьте метод, который выполняет вычисление текущего параметра, сравнивая количество запятый в <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> с числом запятых в сигнатуре.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet11":::

13. Добавьте обработчик событий для <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события, вызывающего `ComputeCurrentParameter()` метод.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet12":::

14. Реализуйте свойство <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Это свойство содержит объект <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , соответствующий диапазону текста в буфере, к которому применяется подпись.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet13":::

15. Реализуйте другие параметры.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet14":::

## <a name="implement-the-signature-help-source"></a>Реализация источника справки по сигнатурам
 Источник справки по подписи — это набор сигнатур, для которых предоставляются сведения.

#### <a name="to-implement-the-signature-help-source"></a>Реализация источника справки по сигнатурам

1. Добавьте класс с именем `TestSignatureHelpSource` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet15":::

2. Добавьте ссылку на текстовый буфер.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet16":::

3. Добавьте конструктор, который задает текстовый буфер и поставщик источника справки по сигнатурам.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet17":::

4. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. В этом примере сигнатуры жестко запрограммированы, но в полной реализации эти сведения можно получить из документации по языку.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet18":::

5. Вспомогательный метод `CreateSignature()` предоставляется только для иллюстрации.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet19":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet19":::

6. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. В этом примере есть только две сигнатуры, каждая из которых имеет два параметра. Поэтому этот метод не является обязательным. В более новой реализации, в которой доступно несколько источников справки сигнатур, этот метод используется для определения того, может ли источник справки сигнатуры с наивысшим приоритетом предоставлять соответствующую сигнатуру. Если это не так, метод возвращает значение null, а источнику следующего самого высокого приоритета будет предложено предоставить совпадение.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet20":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet20":::

7. Реализуйте `Dispose()` метод:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet21":::

## <a name="implement-the-signature-help-source-provider"></a>Реализация поставщика источника справки по сигнатурам
 Поставщик источника справки по подписи отвечает за экспорт части компонента Managed Extensibility Framework (MEF) и создание экземпляра справки по сигнатурам.

#### <a name="to-implement-the-signature-help-source-provider"></a>Реализация поставщика источника справки по сигнатурам

1. Добавьте класс с именем, `TestSignatureHelpSourceProvider` реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> , и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , типа <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" и объекта <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet22":::

2. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> , создав экземпляр `TestSignatureHelpSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet23":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet23":::

## <a name="implement-the-command-handler"></a>Реализация обработчика команд
 Справка по сигнатуре обычно активируется открывающей круглой скобкой "(" и закрывается закрывающей круглой скобкой ")". Эти нажатия могут быть обработаны путем запуска, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> чтобы при получении открывающей скобки с префиксом известного имени метода он запустил сеанс справки сигнатуры и закрывает сеанс при получении закрывающей скобки.

#### <a name="to-implement-the-command-handler"></a>Реализация обработчика команд

1. Добавьте класс с именем `TestSignatureHelpCommand` , реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet24":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet24":::

2. Добавьте частные поля для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> адаптера (который позволяет добавить обработчик команд в цепочку обработчиков команд), представление текста, брокер справки и сеанс, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> а также следующий объект <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet25":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet25":::

3. Добавьте конструктор для инициализации этих полей и добавьте фильтр команд в цепочку фильтров команд.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet26":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet26":::

4. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для активации сеанса справки сигнатуры, когда фильтр команд получает открывающую скобку "(" после одного из известных имен методов, а также для закрытия сеанса при получении закрывающей скобки ")", пока сеанс остается активным. Во всех случаях команда пересылается.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet27":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet27":::

5. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод таким образом, чтобы он всегда направлял команду.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet28":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet28":::

## <a name="implement-the-signature-help-command-provider"></a>Реализация поставщика команд справки по сигнатурам
 Можно предоставить команду справки сигнатуры, реализовав <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> для создания экземпляра обработчика команд при создании текстового представления.

### <a name="to-implement-the-signature-help-command-provider"></a>Реализация поставщика команды справки по сигнатуре

1. Добавьте класс с именем `TestSignatureHelpController` , реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> и экспортирующий его с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet29":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet29":::

2. Импортируйте объект <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (используемый для получения <xref:Microsoft.VisualStudio.Text.Editor.ITextView> объекта, задавая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (используемый для поиска текущего слова) и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (для активации сеанса справки сигнатуры).

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet30":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet30":::

3. Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод, создав экземпляр `TestSignatureCommandHandler` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet31":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet31":::

## <a name="build-and-test-the-code"></a>Сборка и тестирование кода
 Чтобы протестировать этот код, создайте решение Сигнатурехелптест и запустите его в экспериментальном экземпляре.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Создание и тестирование решения Сигнатурехелптест

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, содержащий слово "Добавить", и открывающую круглую скобку.

4. После ввода открывающей скобки вы увидите подсказку, которая отображает список двух сигнатур для `add()` метода.

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Связывание типа содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
