---
title: Пошаговое руководство. Отображение завершения операторов | Документация Майкрософт
description: Узнайте, как реализовать выполнение инструкций на основе языка для содержимого с открытым текстом с помощью этого пошагового руководства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: leslierichardson95
ms.author: lerich
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 33ef62a1d2df4b426d76bd294d00a21f1629174b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078478"
---
# <a name="walkthrough-display-statement-completion"></a>Пошаговое руководство: отображение завершения операторов
Можно реализовать завершение операторов на основе языка, определив идентификаторы, для которых необходимо предоставить завершение, а затем активировать сеанс завершения. Можно определить завершение операторов в контексте языковой службы, определить собственное расширение имени файла и тип содержимого, а затем отобразить сведения о завершении только для этого типа. Или можно активировать завершение для существующего типа содержимого, например "обычный текст". В этом пошаговом руководстве показано, как активировать завершение операторов для типа содержимого "обычный текст", который является типом содержимого текстовых файлов. Тип содержимого text является предком всех других типов содержимого, включая код и XML-файлы.

 Завершение операторов обычно запускается путем ввода определенных символов (например, при вводе начала идентификатора, например «using»). Обычно он закрывается нажатием клавиши **пробел**, **Tab** или **Ввод** для фиксации выделенного фрагмента. Можно реализовать функции IntelliSense, которые запускаются при вводе символа с помощью обработчика команд для нажатий клавиш ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс) и поставщика обработчика, реализующего <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейс. Для создания источника завершения, который представляет собой список идентификаторов, участвующих в завершении, реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> интерфейс и поставщик источника завершения ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> интерфейс). Поставщики являются компонентами компонентов Managed Extensibility Framework (MEF). Они отвечают за экспорт классов источника и контроллера, а также импорт служб и брокеров <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , например,, который позволяет переходить в текстовом буфере, и <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , который запускает сеанс завершения.

 В этом пошаговом руководстве показано, как реализовать завершение операторов для жестко запрограммированного набора идентификаторов. В полной реализации языковая служба и документация по языку отвечают за предоставление этого содержимого.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Создание проекта MEF

#### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `CompletionTest` .

2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

4. Добавьте в проект следующие ссылки и убедитесь, что для свойства **CopyLocal** задано значение `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 15,0

     Microsoft. VisualStudio. Shell. неизменяемый. 10.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-the-completion-source"></a>Реализация источника завершения
 Источник завершения отвечает за сбор набора идентификаторов и добавление содержимого в окно завершения, когда пользователь вводит триггер завершения, например первые буквы идентификатора. В этом примере идентификаторы и их описания жестко запрограммированы в <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> методе. В большинстве реальных целей используется средство синтаксического анализа вашего языка, чтобы получить токены для заполнения списка завершения.

### <a name="to-implement-the-completion-source"></a>Реализация источника завершения

1. Добавьте файл класса с именем `TestCompletionSource`.

2. Добавьте следующие импорты:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Измените объявление класса для `TestCompletionSource` так, чтобы оно реализовало <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Добавьте закрытые поля для поставщика источника, текстового буфера и списка <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> объектов (которые соответствуют идентификаторам, которые будут участвовать в сеансе завершения):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Добавьте конструктор, который задает поставщик источника и буфер. `TestCompletionSourceProvider`Класс определяется в последующих шагах:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод, добавив набор завершения, содержащий завершения, которые необходимо предоставить в контексте. Каждый набор завершения содержит набор <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> завершений и соответствует вкладке окна завершения. (В Visual Basic проектах вкладки окна завершения именуются как **Общие** и **все**.) `FindTokenSpanAtPosition` Метод определяется на следующем шаге.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Следующий метод используется для поиска текущего слова в позиции курсора:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Реализуйте `Dispose()` метод:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Реализация поставщика источника завершения
 Поставщик источника завершения — это часть компонента MEF, которая создает экземпляр источника завершения.

### <a name="to-implement-the-completion-source-provider"></a>Реализация поставщика источника завершения

1. Добавьте класс с именем `TestCompletionSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Экспортируйте этот класс с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "обычным текстом" и <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "завершением теста".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Импорт <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , который находит текущее слово в источнике завершения.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> метод для создания экземпляра источника завершения.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Реализация поставщика обработчика команд завершения
 Поставщик обработчика команд завершения является производным от класса <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , который прослушивает событие создания текстового представления и преобразует его из элемента <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , который позволяет добавить команду в цепочку команд Visual Studio Shell в <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Поскольку этот класс является экспортом MEF, его также можно использовать для импорта служб, необходимых обработчику команды.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Реализация поставщика обработчика команд завершения

1. Добавьте файл с именем `TestCompletionCommandHandler` .

2. Добавьте следующие директивы using:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Добавьте класс с именем `TestCompletionHandlerProvider` , реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Экспортируйте этот класс с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> обработчика завершения токенов, типа <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "обычный текст" и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> объекта <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Импортируйте объект <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , который обеспечивает преобразование из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , и, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> а также <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> предоставляет доступ к стандартным службам Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод для создания экземпляра обработчика команд.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Реализация обработчика команд завершения
 Поскольку завершение операторов активируется нажатиями клавиш, необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для получения и обработки нажатий клавиш, которые инициируют, фиксируют и отменяют сеанс завершения.

#### <a name="to-implement-the-completion-command-handler"></a>Реализация обработчика команд завершения

1. Добавьте класс с именем `TestCompletionCommandHandler` , реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Добавьте закрытые поля для следующего обработчика команды (для передачи команды), представления текста, поставщика обработчика команд (который обеспечивает доступ к различным службам) и сеанса завершения:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Добавьте конструктор, который задает поля "текстовое представление" и "поставщик", и добавляет команду в цепочку команд:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, передав команду:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Выполните метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Когда этот метод получает нажатие клавиши, он должен выполнить одно из следующих действий:

   - Разрешить запись символа в буфер, а затем запустить или завершить фильтрацию. (Печать символов.)

   - Зафиксируйте завершение, но не разрешите запись символа в буфер. (Пробел, **Tab** и **Enter** это сделать при отображении сеанса завершения.)

   - Разрешить передачу команды следующему обработчику. (Все остальные команды.)

     Так как этот метод может отображать пользовательский интерфейс, вызовите, <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> чтобы убедиться, что он не вызывается в контексте автоматизации:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Этот код является закрытым методом, который запускает сеанс завершения:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Следующий пример является закрытым методом, который отменяет подписывание на <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> событие:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Сборка и тестирование кода
 Чтобы протестировать этот код, создайте решение Комплетионтест и запустите его в экспериментальном экземпляре.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Создание и тестирование решения Комплетионтест

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, содержащий слово "Добавить".

4. При вводе первого "a" и затем "d" должен появиться список, содержащий "Сложение" и "Адаптация". Обратите внимание, что выбрано сложение. При вводе другого "d" список должен содержать только "Сложение", которое теперь выбрано. Можно применить "Сложение", нажав клавиши **пробел**, **Tab** или клавишу **Ввод** или отклонить список, введя ESC или любой другой ключ.

## <a name="see-also"></a>См. также
- [Пошаговое руководство. Связывание типа содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
