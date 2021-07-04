---
title: Использование оболочек совместимости для изоляции приложения (модульное тестирование)
description: Сведения о том, как использовать типы оболочек для перенаправления вызовов к отдельным методам в коде, написанным в рамках теста. Оболочка может возвращать согласованные результаты при каждом вызове.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 72a976ccd487abdfa2c6501c0dcafee07dc5f4ae
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042864"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Использование оболочек совместимости для изоляции приложения при модульном тестировании

**Типы оболочек** — одна из двух технологий платформы Microsoft Fakes, используемых для изоляции тестируемых компонентов от окружения. Оболочки отвлекают вызовы к отдельным методам в коде, написанным в рамках теста. Множество методов возвращает различные результаты в зависимости от внешних условиях, но оболочка находится под контролем теста и может возвращать последовательные результаты при каждом вызове. Это упрощает создание тестов.

Используйте *оболочки*, чтобы изолировать код из сборок, которые не входят в состав решения. Чтобы изолировать компоненты решения друг от друга, используйте *заглушки*.

Обзор и рекомендации по быстрому началу работы см. в статье [Изоляция тестируемого кода с помощью Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

**Требования**

- Visual Studio Enterprise
- Проект .NET Framework
::: moniker range=">=vs-2019"
- Поддержка проектов в стиле пакета SDK, .NET Core и .NET 5.0, представленная в Visual Studio 2019 (обновление 6), включена по умолчанию в обновление 8. Дополнительные сведения см. в статье [Microsoft Fakes для проектов .NET Core и проектов в стиле SDK](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

## <a name="example-the-y2k-bug"></a>Пример. Ошибка 2000 года

Рассмотрим метод, который создает исключение 1 января 2000 г.

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Тестирование этого метода является проблематичным, поскольку программа зависит от `DateTime.Now`, зависимого от часов компьютера и среды, недетерминированного метода. Кроме того, `DateTime.Now` является статическим свойством, поэтому здесь нельзя использовать тип заглушки. Эта проблема является признаком проблемы изоляции в модульных тестах: программы, которые непосредственно вызывают API базы данных, взаимодействуют с веб-службами и т. д., трудно тестировать с помощью модульных тестов, так как их логика зависит от среды.

В этом случае необходимо использовать типы оболочек совместимости. Типы оболочек совместимости обеспечивают механизм использования любым методом .NET определяемого пользователем делегата. Типы оболочек программно создаются генератором Fakes и используют делегаты, которые мы называем типами оболочек совместимости, для указания новых реализаций метода.

В следующем примере теста показано, как использовать тип оболочки совместимости `ShimDateTime` для предоставления настраиваемой реализации метода DateTime.Now.

```csharp
//unit test code
// create a ShimsContext cleans up shims
using (ShimsContext.Create()) {
    // hook delegate to the shim method to redirect DateTime.Now
    // to return January 1st of 2000
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);
    Y2KChecker.Check();
}
```

## <a name="how-to-use-shims"></a>Использование оболочек

Сначала добавьте сборку Fakes:

1. В **Обозревателе решений** выполните следующие действия: 
    - Для более старого проекта .NET Framework (не в стиле пакета SDK) разверните узел **Ссылки** проекта модульного теста.
    ::: moniker range=">=vs-2019"
    - Для проекта в стиле SDK, предназначенного для .NET Framework, .NET Core или .NET 5.0, разверните узел **Зависимости**, чтобы найти сборку, которую нужно имитировать в разделе **Сборки**, **Проекты** или **Пакеты**.
    ::: moniker-end
    - При работе в Visual Basic на панели инструментов **Обозревателя решений** необходимо выбрать команду **Показать все файлы**, чтобы просмотреть узел **Ссылки**.

2. Выделите сборку, содержащую определения классов, для которых необходимо создать оболочки. Например, если требуется создать оболочку для **DateTime**, выберите **System.dll**.

3. В контекстном меню щелкните **Добавить сборку имитаций**.

### <a name="use-shimscontext"></a>Использование ShimsContext

При использовании типов оболочек в среде модульного тестирования заключите код теста в `ShimsContext` для управления временем существования оболочек совместимости. В противном случае оболочки будут существовать до завершения работы домена приложения. Самый простой способ создания `ShimsContext` — использование статического метода `Create()`, как показано в следующем коде.

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Очень важно правильно ликвидировать каждый контекст оболочки. В общем случае следует вызывать `ShimsContext.Create` внутри оператора `using`, чтобы гарантировать правильный сброс зарегистрированных оболочек. Например, можно зарегистрировать оболочку для метода теста, заменяющего метод `DateTime.Now` делегатом, который всегда возвращает 1 января 2000 г. Если вы забудете сбросить зарегистрированную оболочку в методе теста, остальная часть тестового запуска всегда будет возвращать в качестве значения `DateTime.Now` первое января 2000 года. Это может быть неожиданно и неудобно.

### <a name="write-a-test-with-shims"></a>Создание теста с оболочками

В коде теста вставьте *обход* для метода, который требуется имитировать. Пример:

```csharp
[TestClass]
public class TestClass1
{
        [TestMethod]
        public void TestCurrentYear()
        {
            int fixedYear = 2000;

            using (ShimsContext.Create())
            {
              // Arrange:
                // Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet =
                () =>
                { return new DateTime(fixedYear, 1, 1); };

                // Instantiate the component under test:
                var componentUnderTest = new MyComponent();

              // Act:
                int year = componentUnderTest.GetTheCurrentYear();

              // Assert:
                // This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year);
            }
        }
}
```

```vb
<TestClass()> _
Public Class TestClass1
    <TestMethod()> _
    Public Sub TestCurrentYear()
        Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
            Dim fixedYear As Integer = 2000
            ' Arrange:
            ' Detour DateTime.Now to return a fixed date:
            System.Fakes.ShimDateTime.NowGet = _
                Function() As DateTime
                    Return New DateTime(fixedYear, 1, 1)
                End Function

            ' Instantiate the component under test:
            Dim componentUnderTest = New MyComponent()
            ' Act:
            Dim year As Integer = componentUnderTest.GetTheCurrentYear
            ' Assert:
            ' This will always be true if the component is working:
            Assert.AreEqual(fixedYear, year)
        End Using
    End Sub
End Class
```

Имена классов оболочки создаются путем добавления префикса `Fakes.Shim` к имени исходного типа.

Оболочки работают путем вставки *обходов* в код тестируемого приложения. Где бы ни возникал вызов исходного метода, система Fakes выполняет обход, чтобы вместо вызова настоящего метода происходил вызов кода оболочки.

Обратите внимание, что обходы создаются и удаляются во время выполнения. Всегда следует создавать обходы в течение существования `ShimsContext`. После его удаления все оболочки, созданные во время его активности, удаляются. Лучшего всего сделать это внутри оператора `using`.

Можно увидеть ошибку сборки, утверждающую, что пространство имен Fakes не существует. Иногда эта ошибка появляется, когда есть другие ошибки компиляции. Устраните остальные ошибки, и она исчезнет.

## <a name="shims-for-different-kinds-of-methods"></a>Оболочки для методов различных типов

Типы оболочки позволяют заменить любой метод .NET, включая статические методы или невиртуальные методы собственными делегатами.

### <a name="static-methods"></a>Статические методы

Свойства для присоединения оболочек совместимости к статическим методам помещаются в тип оболочки. Каждое свойство имеет только метод задания, который можно использовать для присоединения делегата к целевому методу. Например, имеется класс `MyClass` со статическим методом `MyMethod`.

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Мы можем присоединить оболочку к методу `MyMethod`, который всегда возвращает значение 5.

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Методы экземпляра (для всех экземпляров)

Аналогично статическим методам для методов экземпляра можно создать оболочки для всех экземпляров. Свойства для присоединения этих оболочек помещаются во вложенный тип с именем AllInstances, чтобы избежать путаницы. Например, имеется класс `MyClass` с методом экземпляра `MyMethod`.

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Можно присоединить оболочку к `MyMethod`, которая всегда возвращает 5, независимо от экземпляра:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

Структура созданного типа ShimMyClass похожа на следующий код.

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public static class AllInstances {
        public static Func<MyClass, int>MyMethod {
            set {
                ...
            }
        }
    }
}
```

Обратите внимание, что Fakes в этом случае передает экземпляр среды выполнения в качестве первого аргумента делегата.

### <a name="instance-methods-for-one-runtime-instance"></a>Методы экземпляра (для одного экземпляра)

Для методов экземпляра можно также создать оболочки совместимости, используя разные делегаты в зависимости от получателя вызова. Это позволяет задать для одного метода экземпляра разные варианты поведения в зависимости от экземпляра типа. Свойства для настройки этих оболочек являются методами экземпляра самого типа оболочки. Каждый экземпляр типа оболочки также связан с необработанным экземпляром типа с оболочкой совместимости.

Например, имеется класс `MyClass` с методом экземпляра `MyMethod`.

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Мы можем настроить два типа оболочки MyMethod таким образом, что первый тип будет всегда возвращать значение 5, а второй — 10.

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

Структура созданного типа ShimMyClass похожа на следующий код.

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public Func<int> MyMethod {
        set {
            ...
        }
    }
    public MyClass Instance {
        get {
            ...
        }
    }
}
```

Доступ к фактическому экземпляру типа с оболочкой совместимости можно получить с помощью свойства Instance.

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Тип оболочки совместимости также имеет неявное преобразование в тип с оболочкой, поэтому, как правило, тип оболочки можно просто использовать как есть.

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Конструкторы

Для конструкторов также можно создать оболочки совместимости для присоединения типов оболочки к будущим объектам. Каждый конструктор предоставляется как статический метод конструктора в типе оболочки совместимости. Например, имеется класс `MyClass` с конструктором, принимающим целое число.

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Мы настраиваем тип оболочки совместимости конструктора так, чтобы каждый будущий экземпляр возвращал -5, если вызывается метод получения значения, независимо от значения в конструкторе.

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Каждый тип оболочки предоставляет два конструктора. Конструктор по умолчанию следует использовать при необходимости создания нового экземпляра, тогда как конструктор, принимающий экземпляр с оболочкой в качестве аргумента, следует использовать только в оболочках совместимости конструктора.

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

Структура созданного типа ShimMyClass похожа на следующий код.

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass>
{
    public static Action<MyClass, int> ConstructorInt32 {
        set {
            ...
        }
    }

    public ShimMyClass() { }
    public ShimMyClass(MyClass instance) : base(instance) { }
    ...
}
```

### <a name="base-members"></a>Базовые члены

Доступ к свойствам оболочки совместимости базовых членов может осуществляться путем создания оболочки для базового типа и передачи дочернего экземпляра в качестве параметра в конструктор базового класса оболочки.

Например, имеется класс `MyBase` с методом экземпляра `MyMethod` и подтипом `MyChild`.

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Мы можем настроить оболочку совместимости `MyBase`, создав новую оболочку `ShimMyBase`.

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Обратите внимание, что дочерний тип оболочки неявно преобразуется в дочерний экземпляр при передаче в качестве параметра в конструктор базовой оболочки совместимости.

Структура созданного типа ShimMyChild и ShimMyBase похожа на следующий код.

```csharp
// Fakes generated code
public class ShimMyChild : ShimBase<MyChild> {
    public ShimMyChild() { }
    public ShimMyChild(Child child)
        : base(child) { }
}
public class ShimMyBase : ShimBase<MyBase> {
    public ShimMyBase(Base target) { }
    public Func<int> MyMethod
    { set { ... } }
}
```

### <a name="static-constructors"></a>Статические конструкторы

Типы оболочек совместимости предоставляют статический метод `StaticConstructor`, чтобы создать оболочку для статического конструктора типа. Так как статические конструкторы выполняются только раз, убедитесь, что оболочка настроена перед получением доступа к любому члену типа.

### <a name="finalizers"></a>Методы завершения

Методы завершения не поддерживаются в Fakes.

### <a name="private-methods"></a>Закрытые методы

Генератор кода Fakes создает свойства оболочки для закрытых методов, которые имеют только видимые типы в сигнатуре, например видимые типы параметров и типы возвращаемого значения.

### <a name="binding-interfaces"></a>Привязка интерфейсов

Когда тип с оболочкой совместимости реализует интерфейс, генератор кода создает метод, позволяющий ему привязать все члены из этого интерфейса за один раз.

Например, имеется класс `MyClass`, реализующий интерфейс `IEnumerable<int>`.

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Вы можете создать оболочки для реализаций `IEnumerable<int>` в MyClass путем вызова метода привязки.

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

Структура созданного типа ShimMyClass похожа на следующий код.

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

## <a name="change-the-default-behavior"></a>Изменение поведения по умолчанию

Каждый созданный тип оболочки содержит экземпляр интерфейса `IShimBehavior` через свойство `ShimBase<T>.InstanceBehavior`. Это поведение используется, когда клиент вызывает член экземпляра, для которого оболочка не создана явно.

Если поведение не задано явно, будет использоваться экземпляр, возвращаемый статическим свойством `ShimBehaviors.Current`. По умолчанию это свойство возвращает поведение, вызывающее исключение `NotImplementedException`.

Это поведение можно изменить в любой момент, задав свойство `InstanceBehavior` для любого экземпляра оболочки совместимости. Например, в следующем фрагменте кода изменяется поведение оболочки, которое ничего не делает или возвращает значение по умолчанию возвращаемого типа, то есть `default(T)`:

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimBehaviors.DefaultValue;
```

Поведение также можно изменить глобально для всех экземпляров с оболочками совместимости, для которых свойство `InstanceBehavior` не было задано явно, путем задания статического свойства `ShimBehaviors.Current`.

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimBehaviors.Current = ShimBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Обнаружение событий доступа к среде

Можно назначить поведение всем членам (включая статические методы) определенного типа, назначив поведение `ShimBehaviors.NotImplemented` статическому свойству `Behavior` соответствующего типа оболочки.

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Параллелизм

Типы оболочек совместимости применяются ко всем потокам в домене приложения, и к ним не применяется сходство потоков. Это важный аспект, если вы планируете использовать средство выполнения тестов, поддерживающее параллельность. Тесты, включающие типы оболочек, невозможно запускать одновременно. Это свойство не применяется средой выполнения Fakes принудительно.

## <a name="call-the-original-method-from-the-shim-method"></a>Вызов исходного метода из метода оболочки совместимости

Предположим, что вы хотите записать текст в файловую систему после проверки имени файла, переданного в метод. В этом случае вам потребуется вызвать исходный метод в середине метода оболочки.

Первый подход для решения этой проблемы — заключить вызов исходного метода в оболочку с помощью делегата и `ShimsContext.ExecuteWithoutShims()`, как показано в следующем примере кода:

```csharp
// unit test code
ShimFile.WriteAllTextStringString = (fileName, content) => {
  ShimsContext.ExecuteWithoutShims(() => {

      Console.WriteLine("enter");
      File.WriteAllText(fileName, content);
      Console.WriteLine("leave");
  });
};
```

Другой подход заключается в задании для оболочки совместимости значения null, вызове исходного метода и восстановлении оболочки.

```csharp
// unit test code
ShimsDelegates.Action<string, string> shim = null;
shim = (fileName, content) => {
  try {
    Console.WriteLine("enter");
    // remove shim in order to call original method
    ShimFile.WriteAllTextStringString = null;
    File.WriteAllText(fileName, content);
  }
  finally
  {
    // restore shim
    ShimFile.WriteAllTextStringString = shim;
    Console.WriteLine("leave");
  }
};
// initialize the shim
ShimFile.WriteAllTextStringString = shim;
```

## <a name="systemenvironment"></a>System.Environment

Чтобы создать оболочку совместимости для <xref:System.Environment?displayProperty=fullName>, добавьте следующее содержимое в файл mscorlib.fakes после элемента **Assembly**:

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

После перестроения решения методы и свойства в классе <xref:System.Environment?displayProperty=fullName> доступны для создания оболочки, например:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Ограничения

Оболочки совместимости нельзя использовать для всех типов из библиотеки базовых классов .NET **mscorlib** и **System** в .NET Framework, а также в **System.Runtime** в .NET Core или .NET 5.0.

## <a name="see-also"></a>См. также раздел

- [Изоляция тестируемого кода с помощью Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Блог Питера Провоста (Peter Provost): оболочки Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Видео (1 ч 16 мин): тестирование нетестируемого кода с помощью Fakes в Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
