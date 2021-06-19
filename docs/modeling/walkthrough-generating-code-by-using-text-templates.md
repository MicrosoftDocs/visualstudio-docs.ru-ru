---
title: Пошаговое руководство. Создание кода с помощью текстовых шаблонов
description: Узнайте, что создание кода позволяет создавать строго типизированный программный код, но при изменении исходной модели его можно легко изменить.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22940fb86ab0cfd7262a3ca7845521847add2dff
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388130"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>Пошаговое руководство. Формирование кода с помощью текстовых шаблонов

Создание кода позволяет создавать программный код, который является строго типизированным, но при этом может быть легко изменен при изменении исходной модели. Сравните это с альтернативным методом написания полностью универсальной программы, принимающей файл конфигурации. Он является более гибким, однако в результате получается код, который труден для чтения и редактирования, а также не отличается высокой производительностью. Данное преимущество рассматривается в этом пошаговом руководстве.

## <a name="typed-code-for-reading-xml"></a>Типизированный код для чтения XML-файла

Пространство имен System.Xml предоставляет комплексные средства для загрузки XML-документа и последующего свободного просмотра его в памяти. К сожалению, все эти узлы имеют одинаковый тип — XmlNode. Поэтому очень легко допустить ошибки программирования, например, ожидая неверный тип дочернего узла или неверные атрибуты.

В данном примере проекта шаблон считывает пример файла XML и создает классы, соответствующие каждому типу узла. В написанном вручную коде эти классы можно использовать для перехода по XML-файлу. Можно также запустить приложение для любых других файлов, использующих те же типы узлов. Пример XML-файла служит для предоставления примеров всех типов узлов, с которыми должно работать ваше приложение.

> [!NOTE]
> Приложение [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe), которое входит в состав Visual Studio, может создавать строго типизированные классы из XML-файлов. Показанный здесь шаблон представлен в качестве примера.

Ниже приведен пример файла:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<catalog>
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>
  </artist>
  <artist id ="Euan%20Garden" name="Euan Garden">
    <song id ="GardenScottishCountry">Scottish Country Garden</song>
  </artist>
</catalog>
```

В проекте, создаваемом в данном пошаговом руководстве, можно написать следующий код, при этом IntelliSense будет предлагать правильные имена атрибутов и дочерних элементов:

```csharp
Catalog catalog = new Catalog(xmlDocument);
foreach (Artist artist in catalog.Artist)
{
  Console.WriteLine(artist.name);
  foreach (Song song in artist.Song)
  {
    Console.WriteLine("   " + song.Text);
  }
}
```

Сравните это с нетипизированным кодом, который можно написать без шаблона:

```csharp
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");
foreach (XmlNode artist in catalog.SelectNodes("artist"))
{
    Console.WriteLine(artist.Attributes["name"].Value);
    foreach (XmlNode song in artist.SelectNodes("song"))
    {
         Console.WriteLine("   " + song.InnerText);
     }
}
```

В строго типизированной версии изменение схемы XML приводит к изменению классов. Компилятор выделяет части кода приложения, которые необходимо изменить. В нетипизированной версии, использующей универсальный XML-код, такая поддержка отсутствует.

В этом проекте применяется один файл шаблона для создания классов, которые делают типизированную версию возможной.

## <a name="set-up-the-project"></a>Настройка проекта

### <a name="create-or-open-a-c-project"></a>Создание или открытие проекта C#

Эту методику можно применить к любому проекту кода. В этом пошаговом руководстве используется проект C#, а в целях тестирования применяется консольное приложение.

1. В меню **файл** выберите пункт **создать** , а затем выберите пункт **проект**.

2. Выберите узел **Visual C#** а затем в области **Шаблоны** щелкните **Консольное приложение**.

### <a name="add-a-prototype-xml-file-to-the-project"></a>Добавление XML-файла прототипа в проект

Этот файл служит для предоставления примеров всех типов узлов XML, которые ваше приложение должно уметь считывать. Это может быть файл, который будет использоваться для тестирования приложения. Шаблон создаст класс C# для каждого типа узла в этом файле.

Файл должен быть частью проекта, чтобы шаблон мог считать его, однако он не будет встроен в скомпилированное приложение.

1. В **Обозреватель решений** щелкните правой кнопкой мыши проект, выберите **Добавить** , а затем щелкните **новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите в области **Шаблоны** элемент **XML-файл**.

3. Добавьте образец содержимого в файл.

4. В рамках данного пошагового руководства назовите файл `exampleXml.xml`. Используйте в качестве содержимого файла XML-код, приведенный в предыдущем разделе.

### <a name="add-a-test-code-file"></a>Добавление файла кода тестирования

Добавьте в проект файл C# и напишите в нем пример кода, который вы хотите иметь возможность записать. Пример.

```csharp
using System;
namespace MyProject
{
  class CodeGeneratorTest
  {
    public void TestMethod()
    {
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");
      foreach (Artist artist in catalog.Artist)
      {
        Console.WriteLine(artist.name);
        foreach (Song song in artist.Song)
        {
          Console.WriteLine("   " + song.Text);
} } } } }
```

На этом этапе скомпилировать код не удастся. При написании шаблона вы создадите классы, позволяющие успешно скомпилировать код.

Более полный тест позволит проверить выходные данные этой тестовой функции на соответствие известному содержимому из примера XML-файла. Однако в данном пошаговом руководстве нам достаточно успешной компиляции тестового метода.

### <a name="add-a-text-template-file"></a>Добавление файла текстового шаблона

Добавьте файл текстового шаблона и задайте для расширения Output значение *. CS*.

1. В **обозревателе решений** щелкните проект правой кнопкой мыши, выберите пункт **Добавить**, а затем щелкните **Новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите в области **Шаблоны** элемент **Текстовый шаблон**.

    > [!NOTE]
    > Убедитесь, что добавляется именно текстовый шаблон, а не предварительно преобразованный текстовый шаблон.

3. В директиве template файла измените значение атрибута `hostspecific` на `true`.

     Это изменение позволит коду шаблона получить доступ к службам Visual Studio.

4. В директиве output измените значение атрибута расширения на ".cs", чтобы шаблон создал файл C#. В проекте Visual Basic следовало бы изменить его на ".vb".

5. Сохраните файл. На данном этапе файл текстового шаблона должен содержать следующие строки:

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

Обратите внимание, что CS-файл отображается в обозревателе решений как дочерний элемент файла шаблона. Его можно просмотреть, нажав кнопку [+] рядом с именем файла шаблона. Этот файл создается из файла шаблона при каждом сохранении или перемещении фокуса с файла шаблона. Созданный файл компилируется как часть проекта.

Для удобства в процессе разработки файла шаблона расположите окна файла шаблона и созданный файл рядом друг с другом. Это позволит сразу просматривать выходные данные шаблона. Также можно заметить, что когда шаблон создает недопустимый код C#, в окне сообщений об ошибке отображаются ошибки.

Любые изменения, вносимые непосредственно в созданный файл, будут теряться при каждом сохранении файла шаблона. Поэтому следует либо избегать изменения созданного файла, либо редактировать его лишь для кратковременных экспериментов. Иногда бывает удобно проверить небольшой фрагмент кода в созданном файле, где работает технология IntelliSense, и затем скопировать его в файл шаблона.

## <a name="develop-the-text-template"></a>Разработка текстового шаблона

Следуя рекомендациям в отношении гибкой разработки, мы будем разрабатывать шаблон небольшими этапами, устраняя ошибки на каждом шаге, пока тестовый код не будет компилироваться и выполняться правильно.

### <a name="prototype-the-code-to-be-generated"></a>Прототип для создаваемого кода

Тестовый код требует класс для каждого узла в файле. Таким образом, некоторые ошибки компиляции исчезнут, если добавить в шаблон следующие строки и сохранить его:

```csharp
class Catalog {}
class Artist {}
class Song {}
```

Это поможет увидеть, что именно требуется, но объявления должны создаваться из типов узлов в образце XML-файла. Удалите эти экспериментальные строки из шаблона.

### <a name="generate-application-code-from-the-model-xml-file"></a>Создание кода приложения из модели XML-файла

Чтобы прочитать XML-файл и создать объявления классов, замените содержимое шаблона следующим кодом:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#
 XmlDocument doc = new XmlDocument();
 // Replace this file path with yours:
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
#>
  public partial class <#= node.Name #> {}
<#
 }
#>
```

Замените путь к файлу правильным путем для проекта.

Обратите внимание на разделители блока кода `<#...#>`. Эти разделители обозначают фрагмент кода программы, создающий текст. Разделители блока выражения `<#=...#>` обозначают выражение, которое может быть вычислено в строку.

При создании шаблона, формирующего исходный код для приложения, вы работаете с двумя отдельными текстами программ. Программа внутри разделителей блока кода выполняется каждый раз, когда вы сохраняете шаблон или перемещаете фокус на другое окно. Создаваемый ею текст, который отображается вне разделителей, копируется в создаваемый файл и становится частью кода приложения.

Директива `<#@assembly#>` ведет себя как ссылка, предоставляя коду шаблона доступ к сборке. Список сборок, видимых шаблоном, отличается от списка ссылок в проекте приложения.

Директива `<#@import#>` действует как оператор `using`, позволяя использовать короткие имена классов в импортированном пространстве имен.

К сожалению, хотя этот шаблон и формирует код, он создает объявление класса для каждого узла в примере XML-файла, так что если существует несколько экземпляров узла `<song>`, появится несколько объявлений класса song.

### <a name="read-the-model-file-then-generate-the-code"></a>Чтение файла модели и последующее создание кода

Многие текстовые шаблоны следуют общему правилу, где первая часть шаблона считывает исходный файл, а вторая — создает шаблон. Необходимо считать весь пример файла, чтобы подвести итоги по содержащимся в нем типам узлов, а затем создать объявления классов. Другой `<#@import#>` необходим, чтобы мы могли использовать `Dictionary<>:`

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
<#
 // Read the model file
 XmlDocument doc = new XmlDocument();
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 Dictionary <string, string> nodeTypes =
        new Dictionary<string, string>();
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   nodeTypes[node.Name] = "";
 }
 // Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= nodeName #> {}
<#
 }
#>
```

### <a name="add-an-auxiliary-method"></a>Добавление вспомогательного метода

Блок управления возможностями класса — это блок, в котором можно определить вспомогательные методы. Блок разделяется с помощью `<#+...#>` и должен быть последним блоком в файле.

Если вы предпочитаете, чтобы имена классов начинались с прописной буквы, замените последнюю часть шаблона следующим кодом:

```
// Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= UpperInitial(nodeName) #> {}
<#
 }
#>
<#+
 private string UpperInitial(string name)
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }
#>
```

На этом этапе созданный *CS* файл содержит следующие объявления:

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

Аналогичным образом можно добавить дополнительные сведения, такие как свойства дочерних узлов, атрибуты и внутренний текст.

### <a name="access-the-visual-studio-api"></a>Доступ к API Visual Studio

Установка `hostspecific` атрибута `<#@template#>` директивы позволяет шаблону получить доступ к API Visual Studio. Благодаря этому шаблон может получить сведения о расположении файлов проекта, чтобы избежать использования абсолютного пути к файлу в коде шаблона.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
...
<#@ assembly name="EnvDTE" #>
...
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
// Open the prototype document.
XmlDocument doc = new XmlDocument();
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
```

## <a name="complete-the-text-template"></a>Завершение работы с текстовым шаблоном

Следующее содержимое шаблона создает код, позволяющий скомпилировать и запустить тестовый код.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{
<#
 // Map node name --> child name --> child node type
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();

 // The Visual Studio host, to get the local file path.
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
 // Open the prototype document.
 XmlDocument doc = new XmlDocument();
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
 // Inspect all the nodes in the document.
 // The example might contain many nodes of the same type,
 // so make a dictionary of node types and their children.
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   Dictionary<string, XmlNodeType> subs = null;
   if (!nodeTypes.TryGetValue(node.Name, out subs))
   {
     subs = new Dictionary<string, XmlNodeType>();
     nodeTypes.Add(node.Name, subs);
   }
   foreach (XmlNode child in node.ChildNodes)
   {
     subs[child.Name] = child.NodeType;
   }
   foreach (XmlNode child in node.Attributes)
   {
     subs[child.Name] = child.NodeType;
   }
 }
 // Generate a class for each node type.
 foreach (string className in nodeTypes.Keys)
 {
    // Capitalize the first character of the name.
#>
    partial class <#= UpperInitial(className) #>
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }

<#
    // Generate a property for each child.
    foreach (string childName in nodeTypes[className].Keys)
    {
      // Allow for different types of child.
      switch (nodeTypes[className][childName])
      {
         // Child nodes:
         case XmlNodeType.Element:
#>
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }
<#
         break;
         // Child attributes:
         case XmlNodeType.Attribute:
#>
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }
<#
         break;
         // Plain text:
         case XmlNodeType.Text:
#>
      public string Text  { get { return thisNode.InnerText; } }
<#
         break;
       } // switch
     } // foreach class child
  // End of the generated class:
#>
   }
<#
 } // foreach class

   // Add a constructor for the root class
   // that accepts an XML filename.
   string rootClassName = doc.SelectSingleNode("*").Name;
#>
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}
<#+
   private string UpperInitial(string name)
   {
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);
   }
#>
```

### <a name="run-the-test-program"></a>Запуск тестовой программы

В функции main консольного приложения за выполнение тестового метода отвечают приведенные ниже строки. Нажмите клавишу F5, чтобы запустить программу в режиме отладки:

```csharp
using System;
namespace MyProject
{
  class Program
  {
    static void Main(string[] args)
    {
      new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
    }
  }
}
```

### <a name="write-and-update-the-application"></a>Написание и обновление приложения

Теперь приложение можно написать в строго типизированном стиле, используя вместо универсального XML-кода созданные классы.

При изменении схемы XML можно легко создать новые классы. Компилятор сообщит разработчику, где именно требуется обновить код приложения.

Чтобы повторно создать классы при изменении XML-файла примера, щелкните **преобразовать все шаблоны** на панели инструментов **Обозреватель решений** .

## <a name="conclusion"></a>Заключение

В этом пошаговом руководстве показано несколько методов и преимуществ создания кода:

- *Создание кода* — это создание части исходного кода приложения на базе *модели*. Модель содержит информацию в форме, приемлемой для домена приложения, и может измениться в течение жизненного цикла приложения.

- Одно из преимуществ создания кода — строгая типизация. Хотя модель представляет данные в форме, более удобной для пользователя, созданный код позволяет другим частям приложения работать с информацией, используя набор типов.

- IntelliSense и компилятор помогают создавать код, который соответствует схеме модели, как при написании нового кода, так и при обновлении схемы.

- Эти преимущества можно использовать, добавив в проект один несложный файл шаблона.

- Текстовый шаблон можно разрабатывать и тестировать быстро и последовательно.

В этом пошаговом руководстве код программы фактически создается из экземпляра модели — репрезентативного примера XML-файлов, которые будут обрабатывать приложение. При более формальном подходе схема XML будет выполнять роль входных данных для шаблона в форме XSD-файла или определения доменного языка. Такой подход позволит шаблону проще определить такие характеристики, как кратность отношения.

## <a name="troubleshoot-the-text-template"></a>Устранение неполадок с текстовым шаблоном

Если при преобразовании или компиляции шаблона в **списке ошибок** появились ошибки или выходной файл был создан неправильно, эти неполадки текстового шаблона можно устранить с помощью методов, описанных в статье [Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

## <a name="see-also"></a>См. также

- [Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)
