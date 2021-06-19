---
title: Пошаговое руководство. Отладка текстовых шаблонов, обращающихся к модели
description: Содержит сведения об отладке текстового шаблона, обращающегося к модели.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: d39b1ac72210145cc1efa1c513b7f3b76d8c2e36
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388234"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели
При изменении или добавлении текстовых шаблонов в решении доменного языка могут возникнуть ошибки, когда обработчик преобразует шаблон в исходный код или компилирует созданный код. В следующем пошаговом руководстве демонстрируются некоторые действия, которые можно выполнить для отладки текстового шаблона.

> [!NOTE]
> Дополнительные сведения о текстовых шаблонах см. в разделе [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md). Дополнительные сведения об отладке текстовых шаблонов см. [в разделе Пошаговое руководство. Отладка текстового шаблона](debugging-a-t4-text-template.md).

## <a name="creating-a-domain-specific-language-solution"></a>Создание Domain-Specific языкового решения
 В этой процедуре вы создадите решение доменного языка со следующими характеристиками:

- Имя: Дебуггингтестлангуаже

- Шаблон решения: Минимальный язык

- Расширение файла:. ddd

- Название организации: Fabrikam

  Дополнительные сведения о создании решения для доменного языка см. в разделе [как создать Domain-Specific языкового решения](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Создание текстового шаблона
 Добавьте в решение текстовый шаблон.

#### <a name="to-create-a-text-template"></a>Создание текстового шаблона

1. Создайте решение и приступите к его запуску в отладчике. (В меню **Сборка** щелкните **Перестроить решение**, а затем в меню **Отладка** выберите команду **начать отладку**.) В новом экземпляре Visual Studio откроется проект отладки.

2. Добавьте текстовый файл с именем `DebugTest.tt` в проект отладки.

3. Убедитесь, что для свойства **Custom Tool** объекта DebugTest.TT задано значение `TextTemplatingFileGenerator` .

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Директивы отладки, обращающиеся к модели из текстового шаблона
 Прежде чем можно будет получить доступ к модели из инструкций и выражений в текстовом шаблоне, необходимо сначала вызвать созданный обработчик директив. Вызов созданного обработчика директив делает классы модели доступными для кода текстового шаблона как свойства. Дополнительные сведения см. в разделе [доступ к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md).

 В следующих процедурах будет выполнено Отладка неправильного имени директивы и неправильного имени свойства.

#### <a name="to-debug-an-incorrect-directive-name"></a>Отладка неправильного имени директивы

1. Замените код в DebugTest.tt следующим кодом:

    > [!NOTE]
    > Код содержит ошибку. Вы представляете ошибку, чтобы отладить ее.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. В **Обозреватель решений** щелкните правой кнопкой мыши DebugTest.tt и выберите пункт **Запустить пользовательский инструмент**.

     В окне **Список ошибок** отображается эта ошибка:

     **Процессор с именем "Дебуггингтестлангуажедирективепроцессор" не поддерживает директиву с именем "Моделрут". Преобразование не будет выполняться.**

     В этом случае вызов директивы содержит неправильное имя директивы. Вы указали `modelRoot` имя директивы, но правильное имя директивы — `DebuggingTestLanguage` .

3. Дважды щелкните ошибку в окне **Список ошибок** , чтобы перейти к коду.

4. Чтобы исправить код, измените имя директивы на `DebuggingTestLanguage` .

     Изменение выделено.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. В **Обозреватель решений** щелкните правой кнопкой мыши DebugTest.tt и выберите пункт **Запустить пользовательский инструмент**.

     Теперь система преобразует текстовый шаблон и создает соответствующий выходной файл. В окне **Список ошибок** ошибки не отображаются.

#### <a name="to-debug-an-incorrect-property-name"></a>Отладка неправильного имени свойства

1. Замените код в DebugTest.tt следующим кодом:

    > [!NOTE]
    > Код содержит ошибку. Вы представляете ошибку, чтобы отладить ее.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. В **Обозреватель решений** щелкните правой кнопкой мыши DebugTest.tt и выберите пункт **Запустить пользовательский инструмент**.

     Появится окно **Список ошибок** , в котором отображается одна из следующих ошибок:

     C#

     **Компиляция преобразования: Microsoft. VisualStudio. TextTemplating \<GUID> . Женератедтексттрансформатион "не содержит определения для" пространстве ExampleModel "**

     (Visual Basic)

     **Компиляция преобразования: "пространстве ExampleModel" не является членом "Microsoft. VisualStudio. TextTemplating" \<GUID> . Женератедтексттрансформатион ".**

     В этом случае код текстового шаблона содержит неправильное имя свойства. Вы указали `ExampleModel` имя свойства, но правильное имя свойства — `LibraryModel` . Правильное имя свойства можно найти в параметре, как показано в следующем коде:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Дважды щелкните ошибку в окне список ошибок, чтобы перейти к коду.

4. Чтобы исправить код, измените имя свойства на `LibraryModel` в коде текстового шаблона.

     Изменения выделены.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5. В **Обозреватель решений** щелкните правой кнопкой мыши DebugTest.tt и выберите пункт **Запустить пользовательский инструмент**.

     Теперь система преобразует текстовый шаблон и создает соответствующий выходной файл. В окне **Список ошибок** ошибки не отображаются.
