---
title: Создание текста во время выполнения с помощью текстовых шаблонов T4
description: Узнайте, как можно создавать текстовые строки в приложении во время выполнения с помощью текстовых шаблонов среды выполнения Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96d37bc586f9e8d6134377244c3181a52ec11a84
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387558"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Создание текста во время выполнения с помощью текстовых шаблонов T4

Текстовые строки в приложении можно создавать во время выполнения с помощью текстовых шаблонов среды выполнения Visual Studio. Компьютер, на котором выполняется приложение, не обязательно должен иметь Visual Studio. Шаблоны среды выполнения иногда называются «предварительно обработанные текстовые шаблоны», так как во время компиляции шаблон создает код, выполняемый во время выполнения.

Каждый шаблон представляет собой сочетание текста, которое будет отображаться в сформированной строке, и фрагменты программного кода. Фрагменты программы предоставляют значения для переменных частей строки, а также управляют условными и повторяющимися частями.

Например, следующий шаблон можно использовать в приложении, которое создает HTML-отчет.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Обратите внимание, что шаблон — это HTML-страница, в которой переменные части были заменены программным кодом. Вы можете приступить к созданию такой страницы, записав статический прототип страницы HTML. Затем можно заменить таблицу и другие переменные части программным кодом, который создает содержимое, которое может меняться от одного способа к другому.

Использование шаблона в приложении упрощает просмотр окончательной формы выходных данных, чем в, например, длинной серии инструкций Write. Внесение изменений в форму выходных данных стало проще и надежнее.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Создание Run-Time текстового шаблона в любом приложении

### <a name="to-create-a-run-time-text-template"></a>Создание текстового шаблона времени выполнения

1. В Обозреватель решений в контекстном меню проекта выберите команду **Добавить**  >  **новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите **шаблон текста среды выполнения**. (В Visual Basic поищите **Общие элементы**  >  **Общие**.)

3. Введите имя для файла шаблона.

    > [!NOTE]
    > Имя файла шаблона будет использоваться в качестве имени класса в созданном коде. Поэтому в нем не должно быть пробелов или знаков препинания.

4. Нажмите кнопку **Добавить**.

    Будет создан новый файл с расширением **. TT**. Его свойство **Custom Tool** имеет значение **тексттемплатингфилепрепроцессор**. Он содержит следующие строки:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Преобразование существующего файла в шаблон Run-Time

Хорошим способом создания шаблона является преобразование существующего примера выходных данных. Например, если приложение будет создавать HTML-файлы, можно начать с создания обычного HTML-файла. Убедитесь, что он работает правильно и его внешний вид правильный. Затем добавьте его в проект Visual Studio и преобразуйте в шаблон.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Преобразование существующего текстового файла в шаблон времени выполнения

1. Включите файл в проект Visual Studio. В Обозреватель решений в контекстном меню проекта выберите команду **Добавить**  >  **существующий элемент**.

2. Задайте для свойства файла **Custom Tools** значение **тексттемплатингфилепрепроцессор**. В обозреватель решений в контекстном меню файла выберите пункт **Свойства**.

    > [!NOTE]
    > Если свойство уже задано, убедитесь, что оно имеет значение **тексттемплатингфилепрепроцессор** , а не **тексттемплатингфилеженератор**. Это может произойти, если включить файл, уже имеющий расширение **. TT**.

3. Измените расширение имени файла на **TT**. Хотя этот шаг является необязательным, он позволяет избежать открытия файла в неправильном редакторе.

4. Удалите все пробелы или знаки препинания из основной части имени файла. Например, "My Web Page.tt" будет неправильным, но "MyWebPage.tt" будет правильным. Имя файла будет использоваться в качестве имени класса в созданном коде.

5. Вставьте следующую строку в начало файла. При работе в проекте Visual Basic замените "C#" на "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Содержимое шаблона Run-Time

### <a name="template-directive"></a>Директива template

Сохраняет первую строку шаблона в том виде, в котором он был создан при создании файла:

`<#@ template language="C#" #>`

Параметр Language будет зависеть от языка вашего проекта.

### <a name="plain-content"></a>Простое содержимое

Измените **TT** файл, чтобы он содержал текст, который должен быть создан приложением. Пример.

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Встроенный код программы

Программный код можно вставлять между `<#` и `#>` . Пример.

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Обратите внимание, что операторы вставляются между `<# ... #>` выражениями и вставляются между ними `<#= ... #>` . Дополнительные сведения см. [в разделе Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Использование шаблона

### <a name="the-code-built-from-the-template"></a>Код, созданный на основе шаблона

При сохранении **TT** -файла создается файл дочернего файла **. CS** или **. vb** . Чтобы просмотреть этот файл в **Обозреватель решений**, разверните **TT** узел файла. В Visual Basic проекте сначала выберите пункт **Показывать все файлы** на панели инструментов **Обозреватель решений** .

Обратите внимание, что дочерний файл содержит разделяемый класс, содержащий метод с именем `TransformText()` . Этот метод можно вызвать из приложения.

### <a name="generating-text-at-run-time"></a>Формирование текста во время выполнения

В коде приложения можно создать содержимое шаблона с помощью следующего вызова:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Чтобы поместить созданный класс в определенное пространство имен, задайте свойство **пространство имен пользовательского инструмента** для файла текстового шаблона.

### <a name="debugging-runtime-text-templates"></a>Отладка текстовых шаблонов среды выполнения

Текстовые шаблоны отладки и тестового времени выполнения точно так же, как и обычный код.

Точку останова можно задать в текстовом шаблоне. При запуске приложения в режиме отладки из Visual Studio можно пошагово выполнить код и оценить выражения контрольных значений обычным образом.

### <a name="passing-parameters-in-the-constructor"></a>Передача параметров в конструкторе

Обычно шаблон должен импортировать некоторые данные из других частей приложения. Чтобы сделать это простым, код, созданный с помощью шаблона, является разделяемым классом. Можно создать другую часть того же класса в другом файле в проекте. Этот файл может включать конструктор с параметрами, свойствами и функциями, доступ к которым можно получить с помощью кода, внедренного в шаблон, и остальной части приложения.

Например, можно создать отдельный файл **мивебпажекоде. CS**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

В файле шаблона **MyWebPage.TT** можно написать:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Чтобы использовать этот шаблон в приложении, сделайте следующее:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Параметры конструктора в Visual Basic

В Visual Basic отдельный файл **мивебпажекоде. vb** содержит:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Файл шаблона может содержать:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Для вызова шаблона можно передать параметр в конструкторе:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Передача данных в свойствах шаблона

Другой способ передачи данных в шаблон — добавить открытые свойства в класс шаблона в определении разделяемого класса. Приложение может задать свойства перед вызовом `TransformText()` .

Кроме того, можно добавлять поля в класс шаблона в частичном определении. Это позволяет передавать данные между последовательными выполнениями шаблона.

### <a name="use-partial-classes-for-code"></a>Использование разделяемых классов для кода

Многие разработчики предпочитают не писать большие тексты кода в шаблонах. Вместо этого можно определить методы в разделяемом классе, имя которого совпадает с именем файла шаблона. Вызывайте эти методы из шаблона. Таким образом, шаблон наглядно показывает, как будет выглядеть целевая выходная строка. Обсуждения внешнего вида результата можно отделять от логики создания отображаемых данных.

### <a name="assemblies-and-references"></a>Сборки и ссылки

Если вы хотите, чтобы код шаблона ссылался на .NET или другую сборку, например **System.Xml.dll**, добавьте ее в **ссылки** проекта обычным способом.

Если вы хотите импортировать пространство имен так же `using` , как оператор, это можно сделать с помощью `import` директивы:

```
<#@ import namespace="System.Xml" #>
```

Эти директивы должны располагаться в начале файла сразу после `<#@template` директивы.

### <a name="shared-content"></a>Общая папка.

Если имеется текст, совместно используемый несколькими шаблонами, его можно поместить в отдельный файл и включить в каждый файл, в котором он должен отображаться:

```
<#@include file="CommonHeader.txt" #>
```

Включенное содержимое может содержать любое сочетание программного кода и обычного текста, а также может содержать другие директивы include и другие директивы.

Директиву include можно использовать в любом месте текста файла шаблона или включенного файла.

### <a name="inheritance-between-run-time-text-templates"></a>Наследование между Run-Time текстовыми шаблонами

Вы можете обмениваться содержимым между шаблонами времени выполнения, записав шаблон базового класса, который может быть абстрактным. Используйте `inherits` параметр `<@#template#>` директивы для ссылки на другой класс шаблона среды выполнения.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Шаблон наследования: фрагменты в базовых методах

В шаблоне, используемом в приведенном ниже примере, обратите внимание на следующие моменты.

- Базовый класс `SharedFragments` определяет методы внутри блоков функций класса `<#+ ... #>` .

- Базовый класс не содержит свободного текста. Вместо этого все его текстовые блоки встречаются в методах функций класса.

- Производный класс вызывает методы, определенные в `SharedFragments` .

- Приложение вызывает `TextTransform()` метод производного класса, но не преобразует базовый класс `SharedFragments` .

- Базовый и производные классы являются текстовыми шаблонами среды выполнения; Это значит, что для свойства **Custom Tool** задано значение **тексттемплатингфилепрепроцессор**.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram. cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Итоговый результат:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Шаблон наследования: текст в основном тексте

В этом альтернативном подходе к использованию наследования шаблонов основная часть текста определяется в базовом шаблоне. Производные шаблоны предоставляют фрагменты данных и текста, соответствующие базовому содержимому.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Код приложения:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Полученные выходные данные:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>См. также

Шаблоны времени разработки. Если вы хотите использовать шаблон для создания кода, который станет частью приложения, см. статью [Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Шаблоны времени выполнения можно использовать в любом приложении, где шаблоны и их содержимое определяются во время компиляции. Но если вы хотите написать расширение Visual Studio, которое создает текст из шаблонов, которые изменяются во время выполнения, см. раздел [вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>См. также

- [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md)
- [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)
- [Панель элементов T4](http://olegsych.com/T4Toolbox/)
