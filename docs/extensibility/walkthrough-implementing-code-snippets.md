---
title: Пошаговое руководство. Реализация фрагментов кода | Документация Майкрософт
description: Вы можете создавать фрагменты кода и включать их в расширение редактора. Узнайте, как создавать и регистрировать фрагменты кода с помощью этого пошагового руководства.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: leslierichardson95
ms.author: lerich
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: d55a11f30ad8b4397dc27247410d31b0b79267b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078439"
---
# <a name="walkthrough-implement-code-snippets"></a>Пошаговое руководство. Реализация фрагментов кода
Вы можете создать фрагменты кода и включить их в расширение редактора, чтобы пользователи расширения могли добавлять их в свой собственный код.

 Фрагмент кода — это фрагмент кода или другого текста, который может быть включен в файл. Чтобы просмотреть все фрагменты кода, зарегистрированные для определенных языков программирования, в меню **Сервис** выберите пункт **Диспетчер фрагментов кода**. Чтобы вставить фрагмент в файл, щелкните правой кнопкой мыши в том месте, где должен быть фрагмент, выберите пункт Вставить фрагмент или **заключить** в область, найдите нужный фрагмент и дважды щелкните его. Нажмите клавишу **Tab** или **SHIFT** + **,** чтобы изменить соответствующие части фрагмента, а затем нажмите клавишу **Ввод** или **ESC** , чтобы принять его. Дополнительные сведения см. в разделе [фрагменты кода](../ide/code-snippets.md).

 Фрагмент кода содержится в XML-файле, содержащем расширение имени файла. snippet *. Фрагмент может содержать поля, выделенные после вставки фрагмента, чтобы пользователь мог найти и изменить их. Файл фрагмента также содержит сведения для **диспетчера фрагментов кода** , чтобы он мог отобразить имя фрагмента в правильной категории. Дополнительные сведения о схеме фрагментов см. в разделе [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md).

 В этом пошаговом руководстве объясняется, как выполнить эти задачи:

1. Создание и регистрация фрагментов кода для определенного языка.

2. Добавьте команду **Вставить фрагмент** в контекстное меню.

3. Реализуйте расширение фрагмента кода.

   Это пошаговое руководство основано на [пошаговом руководстве: завершение инструкции по отображению](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Создание и регистрация фрагментов кода
 Как правило, фрагменты кода связаны с зарегистрированной языковой службой. Однако нет необходимости реализовывать <xref:Microsoft.VisualStudio.Package.LanguageService> для регистрации фрагментов кода. Вместо этого просто укажите идентификатор GUID в файле индекса фрагмента, а затем используйте тот же идентификатор GUID в <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , который добавляется в проект.

 В следующих шагах показано, как создать фрагменты кода и связать их с конкретным идентификатором GUID.

1. Создайте следующую структуру каталогов:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    где *% installDir%* — это папка установки Visual Studio. (Хотя этот путь обычно используется для установки фрагментов кода, можно указать любой путь.)

2. В папке \ 1033 \ создайте *XML-* файл и назовите его **TestSnippets.xml**. (Хотя это имя обычно используется для файла индекса фрагмента, можно указать любое имя, если оно имеет расширение *XML* .) Добавьте следующий текст, а затем удалите идентификатор GUID заполнителя и добавьте собственный.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <SnippetCollection>
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">
           <SnippetDir>
               <OnOff>On</OnOff>
               <Installed>true</Installed>
               <Locale>1033</Locale>
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>
               <LocalizedName>Snippets</LocalizedName>
           </SnippetDir>
       </Language>
   </SnippetCollection>
   ```

3. Создайте файл в папке Snippets, назовите его **Test** `.snippet` , а затем добавьте следующий текст:

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
       <CodeSnippet Format="1.0.0">
           <Header>
               <Title>Test replacement fields</Title>
               <Shortcut>test</Shortcut>
               <Description>Code snippet for testing replacement fields</Description>
               <Author>MSIT</Author>
               <SnippetTypes>
                   <SnippetType>Expansion</SnippetType>
               </SnippetTypes>
           </Header>
           <Snippet>
               <Declarations>
                   <Literal>
                     <ID>param1</ID>
                       <ToolTip>First field</ToolTip>
                       <Default>first</Default>
                   </Literal>
                   <Literal>
                       <ID>param2</ID>
                       <ToolTip>Second field</ToolTip>
                       <Default>second</Default>
                   </Literal>
               </Declarations>
               <References>
                  <Reference>
                      <Assembly>System.Windows.Forms.dll</Assembly>
                  </Reference>
               </References>
               <Code Language="TestSnippets">
                   <![CDATA[MessageBox.Show("$param1$");
        MessageBox.Show("$param2$");]]>
               </Code>
           </Snippet>
       </CodeSnippet>
   </CodeSnippets>
   ```

   Ниже описано, как зарегистрировать фрагменты кода.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Регистрация фрагментов кода для определенного GUID

1. Откройте проект **комплетионтест** . Сведения о создании этого проекта см. в разделе [Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md).

2. В проекте добавьте ссылки на следующие сборки:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. TextManager. Interop. 8.0

    - Microsoft. MSXML

3. В проекте откройте файл **source. extension. vsixmanifest** .

4. Убедитесь, что вкладка **активы** содержит тип содержимого **VSPackage** , а для этого **проекта** задано имя проекта.

5. Выберите проект Комплетионтест и в окно свойств задать для параметра **создать pkgdef файл** **значение true**. Сохраните проект.

6. Добавьте в `SnippetUtilities` проект статический класс.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. В классе Сниппетутилитиес определите GUID и присвойте ему значение, которое использовалось в файле *SnippetsIndex.xml* .

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Добавьте в <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> `TestCompletionHandler` класс. Этот атрибут можно добавить в любой открытый или внутренний (не статический) класс в проекте. (Может потребоваться добавить `using` директиву для пространства имен Microsoft. VisualStudio. Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Постройте и запустите проект. В экспериментальном экземпляре Visual Studio, который запускается при запуске проекта, только что зарегистрированный фрагмент кода должен быть отображен в **диспетчере фрагментов программ** на языке **тестсниппетс** .

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Добавление команды Вставить фрагмент в контекстное меню
 Команда **Вставить фрагмент** не включается в контекстное меню текстового файла. Поэтому необходимо включить команду.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Добавление команды «Вставить фрагмент» в контекстное меню

1. Откройте `TestCompletionCommandHandler` файл класса.

     Поскольку этот класс реализует <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , в методе можно активировать команду **Вставить фрагмент кода** <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . Перед включением команды убедитесь, что этот метод не вызывается внутри функции автоматизации, поскольку при щелчке команды **Вставить фрагмент** отображается пользовательский интерфейс средства выбора фрагментов кода.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Постройте и запустите проект. В экспериментальном экземпляре откройте файл с расширением *ZZZ* , а затем щелкните правой кнопкой мыши в любом месте. Команда **Вставить фрагмент** должна появиться в контекстном меню.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Реализация расширения фрагментов в пользовательском интерфейсе средства выбора фрагментов кода
 В этом разделе показано, как реализовать расширение фрагмента кода, чтобы пользовательский интерфейс средства **выбора фрагментов отображался при** щелчке в контекстном меню. Фрагмент кода также разворачивается, когда пользователь вводит ярлык фрагмента кода, а затем нажимает клавишу **Tab**.

 Чтобы отобразить пользовательский интерфейс выбора фрагментов и включить прием фрагментов навигации и последующей вставки, используйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. Сама Вставка обрабатывается <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> методом.

 Реализация расширения фрагментов кода использует устаревшие <xref:Microsoft.VisualStudio.TextManager.Interop> интерфейсы. При переводе из текущих классов редактора в устаревший код Помните, что устаревшие интерфейсы используют сочетание номеров строк и номеров столбцов для указания расположений в текстовом буфере, но текущие классы используют один индекс. Таким образом, если в буфере есть три строки, каждая из которых содержит 10 символов (плюс символ новой строки, который считается одним символом), четвертый символ в третьей строке находится в позиции 27 в текущей реализации, но находится в строке 2, позиции 3 в старой реализации.

#### <a name="to-implement-snippet-expansion"></a>Реализация расширения фрагментов кода

1. В файл, содержащий `TestCompletionCommandHandler` класс, добавьте следующие `using` директивы.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Создайте `TestCompletionCommandHandler` класс, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> интерфейс.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. В `TestCompletionCommandHandlerProvider` классе импортируйте <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Добавьте некоторые закрытые поля для интерфейсов расширения кода и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. В конструкторе `TestCompletionCommandHandler` класса задайте следующие поля.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Чтобы отобразить средство выбора фрагментов кода при нажатии пользователем команды **Вставить фрагмент** , добавьте в метод следующий код <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . (Чтобы это объяснение было более удобочитаемым, `Exec()` код, используемый для завершения операторов, не отображается; вместо этого блоки кода добавляются в существующий метод.) Добавьте следующий блок кода после кода, который проверяет наличие символа.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Если в фрагменте есть поля, к которым можно перейти, сеанс расширения остается открытым до тех пор, пока расширение не будет явно принято. Если в фрагменте нет полей, сеанс закрывается и возвращается `null` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> методом. В <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> методе после кода пользовательского интерфейса средства выбора фрагментов, добавленного на предыдущем шаге, добавьте следующий код для управления навигацией по фрагментам кода (когда пользователь нажимает клавишу **Tab** или **SHIFT** +  после вставки фрагмента).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Чтобы вставить фрагмент кода, когда пользователь вводит соответствующий ярлык, а затем нажимает клавишу **Tab**, добавьте код в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. Закрытый метод, который вставляет фрагмент, будет показан на следующем шаге. Добавьте следующий код после кода навигации, добавленного на предыдущем шаге.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Реализуйте методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> интерфейса. В этой реализации единственными интересными методами являются <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Другие методы должны просто возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK> .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Выполните метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Вспомогательный метод, который фактически вставляет расширения, рассматривается на следующем шаге. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Предоставляет сведения о строках и столбцах, которые можно получить из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Следующий частный метод вставляет фрагмент кода, основанный на ярлыке или в заголовке и пути. Затем он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> метод с фрагментом кода.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Расширение фрагмента кода для сборки и тестирования
 Можно проверить, работает ли расширение фрагментов кода в проекте.

1. Создайте решение. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

2. Откройте текстовый файл и введите некоторый текст.

3. Щелкните правой кнопкой мыши где-нибудь в тексте и выберите **Вставить фрагмент**.

4. Пользовательский интерфейс выбора фрагментов кода должен отображаться с всплывающим окном, которое говорит о **полях "замена тестов**". Дважды щелкните всплывающее окно.

     Необходимо вставить следующий фрагмент кода.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Не нажимайте клавишу **Ввод** или **ESC**.

5. Нажмите клавиши **Tab** и **SHIFT** +  , чтобы переключиться между "First" и "Second".

6. Подтвердите вставку, нажав клавишу **Ввод** или **ESC**.

7. В другой части текста введите "Test" и нажмите клавишу **Tab**. Так как «Test» — это ярлык фрагмента кода, фрагмент необходимо вставить еще раз.

## <a name="next-steps"></a>Дальнейшие действия
