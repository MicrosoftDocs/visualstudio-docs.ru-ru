---
title: Распространенные быстрые действия
description: Наиболее популярные быстрые действия для C# и Visual Basic, включая исправление опечаток в ключевых словах или символах, разрешение конфликтов слияния, удаление необходимых импортов, создание типов, введение локальных переменных и т. д.
ms.date: 03/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: db7a3a550f6bfc1250679eeefa0ba3ec6291eef0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585526"
---
# <a name="common-quick-actions"></a>Распространенные быстрые действия

В этих разделах статьи перечислены некоторые распространенные **быстрые действия**, которые применяются как к коду C#, так и к коду Visual Basic. Эти действия являются *исправлениями кода* для диагностики компилятора или встроенных [анализаторов .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md) в Visual Studio.

## <a name="actions-that-fix-errors"></a>Действия для исправления ошибок

Описанные в этом разделе быстрые действия исправляют ошибки в коде, которые в противном случае привели бы к сбою сборки. Когда для устранения ошибки в строке кода доступны быстрые действия, значок, отображаемый в поле или под красной волнистой линией, имеет форму лампочки с красным крестом.

![Значок ошибки и меню быстрых действий](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Исправление опечаток в символах или ключевых словах

Если вы неправильно вводите тип или ключевое слово в Visual Studio, это быстрое действие автоматически исправляет его. В меню лампочки отобразится следующий текст: **Изменить "\<слово с опечаткой>" на "\<правильное слово>"** . Пример:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

| Идентификатор ошибки | Применимые языки |
| - | - |
| CS0103, BC30002 | C# и Visual Basic |

### <a name="resolve-git-merge-conflict"></a>Разрешение конфликтов слияния Git

Эти быстрые действия позволяют устранить конфликты слияния Git, "применяя изменения", то есть удаляя конфликтующие маркеры и код.

```csharp
// Before
private void MyMethod()
{
    if (false)
    {

    }
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

| Идентификатор ошибки | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# и Visual Basic | Visual Studio 2017 версии 15.3 и более поздней |

## <a name="actions-that-remove-unnecessary-code"></a>Действия для удаления ненужного кода

### <a name="remove-unnecessary-usingsimports"></a>Удаление ненужных директив using/Import

Быстрое действие **Удалить ненужные директивы using/импорты** удалит все неиспользуемые директивы `using` и `Import` в текущем файле. При выборе этого элемента удаляются неиспользованные импорты пространства имен.

| Применимые языки | Поддерживаемая версия |
| - | - |
| C# и Visual Basic | Visual Studio 2015 и более поздней версии |

### <a name="remove-unnecessary-cast"></a>Удаление ненужного приведения

Если вы приводите тип к другому типу, которому не требуется приведение, можно воспользоваться действием **Удалить ненужное приведение**.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# и Visual Basic | Visual Studio 2015 и более поздней версии |

### <a name="remove-unused-variables"></a>Удаление неиспользуемых переменных

Это быстрое действие позволяет удалить объявленные переменные, которые нигде не используются.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# и Visual Basic | Visual Studio 2017 версии 15.3 и более поздней |

### <a name="remove-type-from-default-value-expression"></a>Удаление типа из выражения значения по умолчанию

Это быстрое действие удаляет тип значения из выражения значения по умолчанию и использует [литерал по умолчанию](/dotnet/csharp/language-reference/operators/default#default-literal), если компилятор может вывести тип выражения.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017 версии 15.3 и более поздней |

## <a name="actions-that-add-missing-code"></a>Действия для добавления недостающего кода

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Добавление директив using/imports для типов в ссылочных сборках, пакетах NuGet или других типов в решении

При использовании типов, расположенных в других проектах вашего решения, автоматически появляется быстрое действие, но другие нужно включить на вкладке **Сервис > Параметры > C#** или **Basic > Дополнительно**:

- Предлагать using/import для типов в эталонных сборках
- Предлагать using/import для типов в пакетах NuGet

Если параметр включен, при использовании типа в пространстве имен, которое еще не импортировано, но существует в ссылочной сборке или пакете NuGet, создается директива using/import.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

' After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| ИД диагностики | Применимые языки |
| - | - |
| CS0103, BC30451 | C# и Visual Basic|

### <a name="add-missing-casesdefault-caseboth"></a>Добавление отсутствующих элементов case и/или case по умолчанию

При создании оператора `switch` на языке C# или оператора `Select Case` на Visual Basic можно использовать действие кода, чтобы автоматически добавить отсутствующие элементы case и/или оператор case по умолчанию.

Используйте следующее перечисление и удалите оператор `switch` или `Select Case`:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Быстрое действие **Добавить оба** заполняет отсутствующие элементы case и добавляет элементы case по умолчанию.

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# и Visual Basic| Visual Studio 2017 версии 15.3 и более поздней |

### <a name="add-null-checks-for-parameters"></a>Добавление проверки null для параметров

Это быстрое действие позволяет добавить в код проверку параметра на значение Null.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

| Применимые языки | Поддерживаемая версия |
| -------------------- | ---------------- |
| C# и Visual Basic| Visual Studio 2017 версии 15.3 и более поздней |

### <a name="add-argument-name"></a>Добавление имени аргумента

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Применимые языки | Поддерживаемая версия |
| -------------------- | ---------------- |
| C# и Visual Basic| Visual Studio 2017 версии 15.3 и более поздней |

### <a name="add-braces"></a>Добавление фигурных скобок

Быстрое действие "Добавить фигурные скобки" заключает в скобки однострочные операторы `if`.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 и более поздних версий |

### <a name="add-and-order-modifiers"></a>Добавление и упорядочивание модификаторов

Эти быстрые действия помогают отсортировать имеющиеся модификаторы доступа и добавить недостающие.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# и Visual Basic| Visual Studio 2017 версии 15.5 и более поздних |
| IDE0040 | C# и Visual Basic| Visual Studio 2017 версии 15.5 и более поздних |

## <a name="code-transformations"></a>Преобразование кода

### <a name="convert-if-construct-to-switch"></a>Преобразование конструкции if в конструкцию switch

Это быстрое действие позволяет преобразовать конструкцию **if-then-else** в конструкцию **switch**.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

| Применимые языки | Поддерживаемая версия |
| -------------------- | ---------------- |
| C# и Visual Basic| Visual Studio 2017 версии 15.3 и более поздней |

### <a name="convert-to-interpolated-string"></a>Преобразование в интерполированную строку

[Интерполированные строки](/dotnet/csharp/language-reference/keywords/interpolated-strings) позволяют легко выразить строки с внедренными переменными по аналогии с методом **[String.Format](/dotnet/api/system.string.format#overloads)** .  Это быстрое действие распознает использование сцепленных строк или оператора **String.Format** и переключается на использование интерполированной строки.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

| Применимые языки | Поддерживаемая версия |
| -------------------- | ---------------- |
| C# 6.0+ и Visual Basic 14+ | Visual Studio 2017 и более поздних версий |

### <a name="use-object-initializers"></a>Использование инициализаторов объектов

Это быстрое действие позволяет использовать [инициализаторы объектов](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers), чтобы не вызывать конструктор и не добавлять строки операторов назначения.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# и Visual Basic | Visual Studio 2017 и более поздних версий |

### <a name="use-collection-initializers"></a>Использование инициализаторов набора

Это быстрое действие позволяет использовать [инициализаторы набора](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers), чтобы не вызывать несколько раз метод `Add` из вашего класса.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# и Visual Basic | Visual Studio 2017 и более поздних версий |

### <a name="convert-auto-property-to-full-property"></a>Преобразование автосвойства в полное свойство

Это быстрое действие позволяет преобразовать автосвойство в полное свойство, и наоборот.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

| Применимые языки | Поддерживаемая версия |
| -------------------- | ---------------- |
| C# и Visual Basic | Visual Studio 2017 версии 15.5 и более поздних |

### <a name="convert-block-body-to-expression-bodied-member"></a>Преобразование тела блока в элемент с телом выражения

Это быстрое действие позволяет преобразовать тело блока в элемент с телом выражения. Оно предназначено для методов, конструкторов, операторов, свойств, индексаторов и методов доступа.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 и более поздних версий |

### <a name="convert-anonymous-function-to-local-function"></a>Преобразование анонимной функции в локальную

Это быстрое действие преобразует анонимные функции в локальные.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? n : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? n : fibonacci(n-1) + fibonacci(n-2);
}
```

### <a name="convert-referenceequals-to-is-null"></a>Преобразование ReferenceEquals в is null

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0+ | Visual Studio 2017 версии 15.5 и более поздних |

Это быстрое действие предлагает использовать [сопоставление шаблонов](/dotnet/csharp/pattern-matching), а не шаблон кода ```ReferenceEquals```, где это возможно.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0+ | Visual Studio 2017 версии 15. и более поздних версий |

### <a name="introduce-pattern-matching"></a>Введение сопоставления шаблонов

Это быстрое действие предлагает использовать [сопоставление шаблонов](/dotnet/csharp/pattern-matching) с приведениями и проверкой на NULL в C#.

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}
```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0+ | Visual Studio 2017 и более поздних версий |
| IDE0019 | C# 7.0+ | Visual Studio 2017 и более поздних версий |

### <a name="change-base-for-numeric-literals"></a>Изменение основания для числовых литералов

Это быстрое действие позволяет преобразовать числовой литерал в систему счисления с другим основанием. Например, можно перевести любое шестнадцатеричное число в двоичное.

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

| Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| C# 7.0 и более поздние версии, Visual Basic 14 и более поздние версии | Visual Studio 2017 версии 15.3 и более поздней |

### <a name="insert-digit-separators-into-literals"></a>Добавление разделителей между цифрами в литералах

Это быстрое действие позволяет добавлять знаки-разделители в литеральные значения.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

| Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| C# 7.0 и более поздние версии, Visual Basic 14 и более поздние версии | Visual Studio 2017 версии 15.3 и более поздней |

### <a name="use-explicit-tuple-names"></a>Использование явных имен кортежей

Это быстрое действие выявляет области, где можно использовать явные имена кортежей вместо Item1, Item2 и т. д.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0+ и Visual Basic 15+ | Visual Studio 2017 и более поздних версий |

### <a name="use-inferred-names"></a>Использование выводимых имен

Это быстрое действие выделяет места в коде, которые можно упростить путем использования предполагаемых имен элементов в анонимных типах или в кортежах.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 версии 15.5 и более поздних |
| IDE0037 | C# 7.1+ | Visual Studio 2017 версии 15.5 и более поздних |

### <a name="deconstruct-tuple-declaration"></a>Деконструирование объявления кортежа

Это быстрое действие позволяет деконструировать объявления переменных в кортежах.

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0+ | Visual Studio 2017 версии 15.5 и более поздних |

### <a name="make-method-synchronous"></a>Превращение метода в синхронный

Когда для метода используется ключевое слово `async` или `Async`, ожидается, что внутри этого метода также будет использоваться ключевое слово `await` или `Await`. Но если это не так, появится быстрое действие, которое позволяет сделать метод синхронным, удалив ключевое слово `async` или `Async` и изменив тип возвращаемого значения. Используйте параметр **Синхронизация метода** в меню быстрых действий.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

| Идентификатор ошибки | Применимые языки |
| ------- | -------------------- |
| CS1998, BC42356 | C# и Visual Basic |

### <a name="make-method-asynchronous"></a>Превращение метода в асинхронный

При указании ключевого слова `await` или `Await` в методе предполагается, что сам метод помечен ключевым словом `async` или `Async`. Однако если это не так, появится быстрое действие, позволяющее сделать метод асинхронным. Используйте параметр **Make method/Function asynchronous** (Сделать метод/функцию асинхронными) в меню быстрых действий.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

| Идентификатор ошибки | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# и Visual Basic | Visual Studio 2017 и более поздних версий |

## <a name="see-also"></a>См. также раздел

- [Быстрые действия](../ide/quick-actions.md)
